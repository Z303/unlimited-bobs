# Unlimited Bobs
![A number of grey spheres following a circular pattern with a counter in the bottom right](./unlimited-bobs.gif)

An unlimited Bobs effect for the TIC-80


```
buffers={16384,32640,49024,65508}

width=240
height=136

bufferSize=(width*height)/2

ballCount=8

t=0


for s=1,#buffers do
 cls()
 memcpy(buffers[s],0,bufferSize)
end

function TIC()
	s=1+t%#buffers

 memcpy(0,buffers[s],bufferSize)


 for b=1,ballCount do
 	alpha=b*2*math.pi/ballCount
 
	 speed=(s+t*#buffers)*#buffers/3600
	 x=math.sin(alpha+3.12*speed-11)*116
	 y=math.sin(alpha+2.54*speed)*64

	 circ(width/2+x,height/2+y,4,0);		        
	 for j=0,2 do
	  circ(width/2+x-j/2,height/2+y-j/2,
	       3-j,14-j);
	 end
 end
	
 memcpy(buffers[s],0,bufferSize)	
	
	bobCount=(ballCount*t)//#buffers
	textWidth=print(bobCount,820,430,0,true)

	counterX=width-textWidth
	counterY=130
	print(bobCount,
							counterX-1,counterY-1,0,true)
	print(bobCount,
							counterX,counterY,12,true)
	
	t=t+1
end
```
