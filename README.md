# Mathplug_App:  Built on Python 3, Jupyter notebook.
## Code for embedding into a Mathematics learning App
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
