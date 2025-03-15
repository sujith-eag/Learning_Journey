Implement a class Rectangle with the following features:

Constructor to take width and height as numeric arguments
Methods to compute area and perimeter
Methods to return hight and width
Method is `isSquare()` that returns a Boolean indicating whether the rectangle is a square.

```python
class Rectangle:
	def __init__(self, width, hight):
		self.width = width
		self.hight = hight
		
	def area(self):
		result = self.width*self.hight
		return result
		
	def peri(self):
		result = (self.width*2)+(self.hight*2)
        # result = 2* (self.width + self.hight)
		return result
		
	def getWidth(self):
		return self.width
	
	def getHight(self):
		return self.hight
	
	def isSquare(self):
		if (self.hight == self.width):
			return True
		else:
			return False
        # return self.width == self.hight


h = float(input("Enter Hight: "))
w = float(input("Enter width: "))

r1 = Rectangle(w,h)
print(f"\nFor the Rectangle with hight: {r1.hight}, width: {r1.width}")

print(f"The Width will be {r1.getWidth()}, hight will be {r1.getHight()}")

print(f"The Area will be : {r1.area()}")

print(f"The Perimeter will be: {r1.peri()}")

print(f"Is it a Square?: {r1.isSquare()}")
```

