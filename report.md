# The usage of const keyword and & opertator

## 1-The usage of const keyword in c++

### 1-Constant Variables
While declaring a variable as const it must be initialized as well. Once declared as const then we cannot change its value later on as shown in the example 1 below

**[Example 1](https://drive.google.com/file/d/1jKbMH5x6mEGqsVhnJ6yfebSUuibx7Uee/view?usp=sharing)**

### 2-Using const with Pointers
*We can make a pointer constant at time of declaration.

*We can make the value constant to what the pointer is pointing to.

**Constant Pointers:**

if we want that a pointer variable must always point to the same variable then we can make it constant as shown in the example 2 below.

**[Example 2.1](https://drive.google.com/file/d/18f8-FCI7w5UEL5TSorgoxnNuUAuR3sfZ/view?usp=sharing)**

**Pointer to Constant Variables**

A pointer to const means that we can access the value of the variable through pointer variable but cannot change the value of the pointed variable through the pointer variable as explained in example3.

**[Example 2.2](https://drive.google.com/file/d/1wkDGnLJIYNWBhTsgURbnu76nufKTSpAF/view?usp=sharing)**

### 3-Constant Function Arguments

We can use the const keyword with the arguments of a function. If an argument is declared as const then the function will not be allowed to change its value. The same is explained in the following code.

**[Example 3](https://drive.google.com/file/d/1RC14zuQN_GrxF7i6TCjUrXrRCj6zzR-M/view?usp=sharing)**

### 4-Constant Data Members of a Class

If we define a const data member of a class then we must have to initialize that data member through the constructor of the class. The value of const data members cannot be changed through the object of the variable as shown in the code below.

**[Example 4](https://drive.google.com/file/d/1VGr5jInh8xbfjDrF6su-MEkJSwB8XkKN/view?usp=sharing)**

### 5-Constant Objects of a Class

If we declare an object of class as const then the values of data members cannot be changed later on. If we try to change the values of data members then compiler will generate an error as shown in the following code.

**[Example 5](https://drive.google.com/file/d/1h8vG4tI4OVnvIER_heMlgzr-ATNVO1tL/view?usp=sharing)**





## 2-The usage of and & operator

**In C++ there're two different syntax according to the place of the operator**

### 1-&variable; 
 extracts the address of the variable  


### 2-Type& ref = variable; 
 creates reference  to variable called ref as seen in the example

the next example shows the two possible places
**[Example 6](https://drive.google.com/file/d/1x9RtI170Gl2drqlZOhg4igY2kAG-PXvz/view?usp=sharing)**

### 3-Bitwise AND operator &&
The output of bitwise AND is 1 if the corresponding bits of two operands is 1. If either bit of an operand is 0, the result of corresponding bit is evaluated to 0.and we use this operation in conditions as shown 








