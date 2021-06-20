# Mathplug_App:  Built on Python 3, Jupyter notebook.
## 1. Code for embedding into a Mathematics learning App
### Multiplication.
#### This code will ask the student to input two values and ask for their solution.
#### If the student's solution is within 10%, the response is more positive than if the student's solution is out by over 50%
#### The feedback from the code will ONLY return the real solution when the student is correct.

```
# Multiplication Function ~ soft wired solution
# Student answer the question posed, 
# depending on accuracy the code responds according
# to within 50% with "Not quite, try again"
# to within 10% with "Very close, try again"

# Interactive input code:
a = int(input("First number in multiplication?: "))
b = int(input("Second number in multiplication?: "))
solution = int(input("What is the product of these two numbers? "))

sol = a*b  #defines correct solution

# Block1 evaluates the student's solution
def sol_a(solution):
    if solution ==sol:
        return "Correct,"
    elif 0.2 < abs(((solution-sol)/sol)) <0.5:
        return "Not Quite, try again."
    elif abs(((solution-sol)/sol))<0.2:
        return "Very close, try again."
    else:
        return "Not right, try again. "


y = sol_a(solution)  # New variable defined by of function sol_a()

# Block2, links the variable sol to be included ONLY if the correct response
# is provided as an input to sol_a()
def ifsol(y):
    if y == "Correct,":
        print(sol_a(solution),a,"x",b," is ", sol)
    elif y=="Very close, try again.":
        print("Very close, try again.")
    else:
        print("Nowhere near, revise material")
print(ifsol(y))
#print(sol_a(solution),a,"x",b," is ", sol)

```

### For example if we input a=10 and b=10, the solution is 100
### For the student's solution is 70, then the response is "Not Quite, try again."
### For the student's solution of 90, the response is "Very close, try again."
### Whereas for the correct solution (100) will give the response "Correct, 10 x 10  is  100", finally providing the real solution.


## 2. MathsPlug_Arithmetic_App GUI
## Built with Jupyter 3, tKinters
### A basic app for entering teo integers and obtain the result of using those integers as the operands for addition, subtraction, multiplication and division operation.
### The checking code is under construction/

### The student may enter their integers into boxes, by clicking on the +, x, /, -  buttons will reveal the true solutions

[![arithmetic-app.jpg](https://i.postimg.cc/ZqxJ6z62/arithmetic-app.jpg)](https://postimg.cc/94z3jS8Y)



```
### Arithmetic App GUI

from tkinter import Tk, Label, Entry, StringVar
import math as m
import tkinter as tk

root = tk.Tk()

label=Label(root,text="Welcome to the MathPlug Arithmetic App")
label.pack(pady=10)
#############################################################
#STEP 1: Create the canvas
canvas1 = tk.Canvas(root, width=600, height = 300)
canvas1.pack()
##########################################################
#STEP 2: Add the entry boxes
entry1 = tk.Entry(root)
canvas1.create_window(160, 20, window=entry1)

entry2 = tk.Entry(root)
canvas1.create_window(400,20,window=entry2)

entry3 = tk.Entry(root)
canvas1.create_window(160,200,window=entry3)


# Create respective labels for entry 1,2,3
field0 = tk.Label(text=('Enter Numbers'))           
canvas1.create_window(40,20, window=field0)

field1 = tk.Label(text=('Sum = '))           
canvas1.create_window(400,20, window=field1)

field2 = tk.Label(text=('Product = '))           
canvas1.create_window(400,50, window=field2)

field3 = tk.Label(text='Quotient = ')
canvas1.create_window(400,80,window=field3)

field4 = tk.Label(text='Quotient = ')
canvas1.create_window(400,110,window=field4)

field5 = tk.Label(text='Your Solution:')
canvas1.create_window(40,200, window=field5)

# Arithmetic Functions

def get_Sum():
    x1 = entry1.get()
    x2 = entry2.get()
    label_sum = tk.Label(root, text=(round(float(x1)+float(x2))))
    canvas1.create_window(425,20,window=label_sum)  
def get_Product():
    x1 = entry1.get()
    x2 = entry2.get()
    label_prod = tk.Label(root, text=(round(float(x1)*float(x2))))
    canvas1.create_window(435,50,window=label_prod)
    
def get_Quot():
    x1 = entry1.get()
    x2 = entry2.get()
    label_sub = tk.Label(root, text = (round(float(x1)/float(x2))))
    canvas1.create_window(435,80,window=label_sub)
    
def get_Sub():
    x1 = entry1.get()
    x2 = entry2.get()
    label_sub = tk.Label(root, text = (round(float(x1)-float(x2))))
    canvas1.create_window(435,110,window=label_sub)
#############


def Check(x3):
    x1 = entry1.get()
    x2 = entry2.get()
    x3 = entry3.get()
    if float(x1)*float(x2) == float(x3):
        print('Correct')
    else:
        print("Not Correct")    
        
    label_check = tk.Label(root, text = (Check()))
    canvas1.create_window(435,110,window=label_check)
#STEP 4: Add the function buttons

button2=tk.Button(text='+',command=get_Sum)
canvas1.create_window(300,20,window=button2)

button1=tk.Button(text='X',command=get_Product)
canvas1.create_window(300,50,window=button1)

button3=tk.Button(text='/',command=get_Quot)
canvas1.create_window(300,80,window=button3)

button4=tk.Button(text='-',command=get_Sub)
canvas1.create_window(300,110,window=button4)

button5=tk.Button(text='Check',command=Check)
canvas1.create_window(300,200,window=button5)
#######################################################################
root.mainloop()
```


## 3 MathsPlug Arithmetic Tester (Random Questions)
### This code will challenge the student with sets of randomly genorated questions.
### A choice for the quantity of questions is provided.
### When all the questions are completed, the code will output the number of questions answered correctly.

### An exmaple output from a set of five questions will appear as follows:

#### number of questions?5
#### 5 + 1 = 6
####  Correct

####  8 - 7 = 4
#### Not quite

#### 2 + 9 = 11
#### Correct

#### 5 + 2 = 6
#### Not quite

#### 8 - 8 = 0
#### Correct

#### your score is 3 out of 5

```
# MathsPlug Random Arithmetic

import random
# set up score as zero
score = 0
# dictionary initialised
questions = {}

# Generate questions with randomly picked number between 1 and 10
a = 0 #int(input("lower bound: "))
b = 10 #int(input("upperbound: "))
c = int(input("number of questions?"))

for i in range(c):
    operand_a = random.randint(a,b)
    operand_b = random.randint(a,b)
    operators = ['+','-','*']
    operator_type = random.choice(operators)
    question = str(operand_a)+" "+operator_type+" "+str(operand_b)
    solution = str(eval(question))
    question+=" = "
# contributes to the dictionary of questions
    questions.update({question:solution})
    
    
for q in questions.keys():
    student_sol=input(q)
    if questions.get(q)==student_sol:
        print("Correct")
        score +=1
    else:
        print("Not quite")
print("your score is " +str(score) + " out of "+str(c))
```
