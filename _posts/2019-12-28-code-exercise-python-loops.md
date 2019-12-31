---
title: Coding Exercise - Python While Loops
layout: post
tags:
- python
- loops
categories: python
---

#### While Loops
``` python
current_number = 1
while current_number < 5:
	print(current_number)
	current_number +=1
```

#### This loop runs forever! 

```python
x= 1
while x <= 5:
print(x)
```

> Every programmer accidentally writes an infinite while loop from time to time, especially when a program’s loops have subtle exit conditions. If your program gets stuck in an infinite loop, press ctrl-C or just close the terminal window displaying your program’s output.

#### While loop with list

```python
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
print(pets)
new_pets= []

# example 1
while 'cat' in pets: 
	pets.remove('cat')
	print(pets)
	
# example 2
while pets:
	pet=pets.pop()
	print(pet)
	new_pets.append(pet)

print(new_pets)

# example 3 (Dictionary)
while new_pets:
	pet=new_pets.pop()
	if pet=='dog':
		responses[pet] = 'feed'
		
print(responses)
```