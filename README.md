Python Calculator - 


Description:
This is a basic calculator written in Python that performs Addition, Subtraction, Multiplication, and Division, as well as, Power of, Squared and Square Root.

How to use:
The calculator is very simple and instructs you on what to do as you go. 
- It will first give you a list of operators.
- Then prompt you to input an operator, which will be manually typed.
- Unless you choose square root or sqaured you will be asked to input a first number, followed by a second number, then your calculation will be performed.
- Sq and Sr will only require a single number input y the nature of the operations. 
- You can continue to do sums with your answer, you will have to choose another operator followed by a single numner(unless Sq or Sr are chosen)
- If you choose Sr or Sq, then you will not have to choose a number as the calculation will br perfomred on the answer to your previous sum.
- You can reset the caclulator with 'R'.
- You can end the programme with 'E'.



Code:

import math
result = 0  # Initialize the sum total
calc = ''   # Initialize the list of sums shown 

print('--------------------------')
print('Welcome!')
print('--------------------------')
print('Table of Mathematical Operations:')
print('--------------------------')
print('|   Addition         +    |')           # printed welcome message 
print('|   Subtraction      -    |')
print('|   Multiplication   *    |')
print('|   Division         /    |')
print('|   Power Of         P    |')
print('|   Squared          Sq   |')
print('|   Square Root      Sr   |')
print('| --Reset--          R    |')
print('| --Exit Program--   E    |')
print('--------------------------')


while True: #overall continous loop until break with E (whole calculator)
    print('-----------------------------------------')
    operation = input("Choose Operation (+, -, *, /, P, Sq, Sr, R, E ): ")
    print('--------------------------')
    

    while operation not in ('+', '-', '*', '/', 'E', 'P', 'R','Sq','Sr'):       #while o not in --- means loop will not end until o is equal to one of the tuple       
        print('Invalid input, Choose an Operator   --->   +, -, *, /, or E to Exit')
        print('--------------------------')
        operation = input('Choose Operation: ') 
        print('--------------------------') 

    if operation == 'R': #Resets calc
        result = 0  # resets total and sums and list of sums back to 0 and continues back to the start of the loop
        calc = '' 
        print('calculator Reset!') 
        print('--------------------------') 
        continue 
    if operation == 'E': #exits the calc
        result = 0
        calc = '' 
        print('calculator ShutDown') 
        print('--------------------------') 
        break # ends nearest enclosing loop (whole calc)    

    if operation == 'Sq':      # start of Sqaure 
        if result == 0 and calc == '':             # if first time using                            
            num1 = float(input('Choose Your Number: '))             # choose number to square.
            result = num1 * num1            
            calc += f"\n     {operation}   {num1} = {result}"     # add sum to the list (first entry)
            print(calc)
            continue 
        else:
            result2 = result * result   # if it's not the first sum a new variable is needed(i think) it enables me to have the previus result and the new result in the same 'sum line' 
            calc += f"\n     {operation}   {result} = {result2}"     # adds sum to the list
            print(calc)
            result = result2       # this makes it so that more sums can be performed with the new answer from result 2
            continue 



    if operation == 'Sr':   # square root option.   Works the same way as above.
        if result == 0 and calc == '':             # if first time using    
            num1 = float(input('Choose Your Number: '))
            result =  math.sqrt(num1) 
            calc += f"\n    {operation}   {num1} = {result}"
            print(calc)
            continue     
        else:
            result2 = math.sqrt(result)        # if it's not the first sum
            calc += f"\n     {operation}   {result} = {result2}"
            print(calc)
            result = result2
            continue


    if result == 0 and calc == '':        # for main operators choose first number the first time of use.    # Updated to not reset if Sum = 0
        while True:                                                       
            try:                                                           
                num1 = float(input('Choose Your First Number: '))   # first number choice (if Sr or Sq arent chosen)
                print('--------------------------')
                break                                                      

            except ValueError:             # check to make sure number is valid number                              
                print('--------------------------')
                print('Invalid input! Please Enter a Valid Number!')
                print('--------------------------')
    else:
        num1 = result   # makes continuous sums by making answer of previous sum num1 for next sum.     

    
    while True:                                                       
        try:                                                           
            num2 = float(input('Choose Your Next Number: '))    #second number choice
            print('--------------------------')
            break                                                    

        except ValueError:                                    # check to make sure number is valid number            
            print('--------------------------')
            print('Invalid input! Please Enter a Valid Number!')
            print('--------------------------')                # IT MAY BE POSSIBLE TO COMBINE THE TWO ERROR CHECKS ON THE TWO INPUTS



    if operation == "+":
        result = num1 + num2    # basic calculator operators 
    elif operation == "-":
        result = num1 - num2
    elif operation == "*":
        result = num1 * num2
    elif operation == "/":
        if num2 != 0:     # check if num2 IS EXPLICITLY NOT 0 and the else is if it is, better for errors apparently but could be reversed to if num2 = 0 etc
            result = num1 / num2
        else:
            print("Error: Division by zero!")
            continue
    elif operation == 'P':
        result = pow(num1, num2)   # does one number to the power of another using the .math expression pow(x, y)
       


          

    if calc:    # if calc has something in it already, you already did a sum it only shows OP + new number = result
        calc += f"\n     {operation}    {num2} = {result}"  
    else:
        calc = f"{num1} {operation}    {num2} = {result}"   # if first time it shows N1 OP N2 = Rsult       
    

    print(calc) # this print keeps stacking with above \n
    




