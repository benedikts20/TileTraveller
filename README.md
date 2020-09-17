# TileTraveller
Assignment 8 T-111-PROG in RU

Collaborators:

  Benedikt Aron: benedikts20
  
  Davíð Bjarki: davidercool
  
  Daníel Arnarsson: danielarn20
  
  Birkir Arndal: birkirarndal

```py
'''
Við viljum strangt til taka að við vitum að það séu margar miklu betri
leiðir til að leysa þetta verkefni en við vorum of hræddir við skammi
frá kennara fyrir að nota hluti sem ekki var búið að "kenna" okkur
þannig við völdum þessa leið fyrst hún var eina sem við vissum að hafði 
bara efni frá fyrri köflum

Github rep: https://github.com/benedikts20/TileTraveller


define a function move(dir,x,y) where dir is the attempted move direction and x,y are the current coordinates
	check if dir is a valid direction for each x and y and do the following:
		return 4 values:
			If Invalid:
				string of valid directions for current location
				current x position
				current y position
				boolean value of False
			If Valid:
				string of valid directions for next location, empty string if next location is the victory tile
				current x incremented by one if moving east and decremented by one if moving west
				current y incremented by one if moving south and decremented by one if moving north
				boolean value of True
			
define x,y as 1,1 respectively

endless loop:
	store user input in variable dir
	call move(dir,x,y) and store the results in dir,x,y,flag
	if dir is an empty string exit the loop
	if flag is false notify user of false input
	notify user of possible move directions depending on value of dir
'''

def move(dir,x,y):
	if x==1 and y==1:
		if dir == "n": return "nes",x,y+1,True
		return "n",x,y,False
	if x==2 and y==1:
		if dir == "n": return "ws",x,y+1,True
		return "n",x,y,False
	#if x==3 and y==1:
	if x==1 and y==2:
		if dir == "n": return "es",x,y+1,True
		if dir == "e": return "ws",x+1,y,True
		if dir == "s": return "n" ,x,y-1,True
		return "nes",x,y,False
	if x==2 and y==2:
		if dir == "w": return "nes",x-1,y,True
		if dir == "s": return "n",x,y-1,True
		return "ws",x,y,False
	if x==3 and y==2:
		if dir == "n": return "ws",x,y+1,True
		if dir == "s": return "",x,y-1,True
		return "ns",x,y,False
	if x==1 and y==3:
		if dir == "e": return "we",x+1,y,True
		if dir == "s": return "nes",x,y+1,True
		return "es",x,y,False
	if x==2 and y==3:
		if dir == "w": return "es",x-1,y,True
		if dir == "e": return "ws",x+1,y,True
		return "we",x,y,False
	if x==3 and y==3:
		if dir == "w": return "we",x-1,y,True
		if dir == "s": return "ns",x,y-1,True
		return "ws",x,y,False

print("You can travel: (N)orth.")
x,y=1,1
while True:
	dir = input("Direction: ").lower()
	dir,x,y,flag = move(dir,x,y)
	if dir=="":break
	if not flag: print("Not a valid direction!")
	first=True
	print("You can travel: ",end="")
	if "n" in dir:print("(N)orth",end="");first=False
	if "e" in dir:
		if not first:print(" or ",end="")
		print("(E)ast",end="");first=False
	if "s" in dir:
		if not first:print(" or ",end="")
		print("(S)outh",end="");first=False
	if "w" in dir:
		if not first:print(" or ",end="")
		print("(W)est",end="");first=False
	print(".")
print("Victory!")
```
