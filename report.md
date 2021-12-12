# The usage of const keyword and & opertator
## 1) Constant Variables in C++
If you make any variable as constant, using const keyword, you cannot change its value. Also, the constant variables must be initialized while they are declared.
```
int main
{
    const int i = 10;
    const int j = i + 10;     // works fine
    i++;    // this leads to Compile time error   
}

```
In the above code we have made i as constant, hence if we try to change its value, we will get compile time error. Though we can use it for substitution for other variables.

## 2) Pointers with const keyword in C++
Pointers can be declared using const keyword too. When we use const with pointers, we can do it in two ways, either we can apply const to what the pointer is pointing to, or we can make the pointer itself a constant.
*Pointer to a const variable*
This means that the pointer is pointing to a const variable.
```
const int* u;
```
Here, u is a pointer that can point to a const int type variable. We can also write it like,
```
char const* v;
```
still it has the same meaning. In this case also, v is a pointer to an char which is of const type.
Pointers to a const variable is very useful, as this can be used to make any string or array immutable(i.e they cannot be changed).
*const Pointer*
To make a pointer constant, we have to put the const keyword to the right of the *.
```
int x = 1;
int* const w = &x;
```
Here, w is a pointer, which is const, that points to an int. Now we can't change the pointer, which means it will always point to the variable x but can change the value that it points to, by changing the value of x.

The constant pointer to a variable is useful where you want a storage that can be changed in value but not moved in memory. Because the pointer will always point to the same memory location, because it is defined with const keyword, but the value at that memory location can be changed.

**NOTE**: We can also have a const pointer pointing to a const variable.
```
const int* const x;
```
## 3) const Function Arguments and Return types
We can make the return type or arguments of a function as const. Then we cannot change any of them.
```
void f(const int i)
{
    i++;    // error
}

const int g()
{
    return 1;
}
```
**Some Important points to Remember**
1.	For built in datatypes, returning a const or non-const value, doesn't make any difference.
```
const int h()
{
    return 1;
}   
	
int main()
{
const int j = h();
int k = h();
}
```
Both j and k will be assigned the value 1. No error will occur.
2. For user defined datatypes, returning const, will prevent its modification.
3.	Temporary objects created while program execution are always of const type.
4.	If a function has a non-const parameter, it cannot be passed a const argument while making a call.

void t(int*) 
{ 
// function logic
}

If we pass a const int* argument to the function t, it will give error.
5.	But, a function which has a const type parameter, can be passed a const type argument as well as a non-const argument.
```
void g(const int*) 	{
    	    // function logic
}
```
This function can have a int* as well as const int* type argument.

## 4) Defining Class Data members as const
These are data variables in class which are defined using const keyword. They are not initialized during declaration. Their initialization is done in the constructor.
```
class Test
{
    const int i;
    public:
    Test(int x):i(x)
    {
        cout << "\ni value set: " << i;
    }
};

int main()
{
    Test t(10);
    Test s(20);
}
```
In this program, i is a constant data member, in every object its independent copy will be present, hence it is initialized with each object using the constructor. And once initialized, its value cannot be changed. The above way of initializing a class member is known as Initializer List in C++.

## 5) Defining Class Object as const
When an object is declared or created using the const keyword, its data members can never be changed, during the object's lifetime.

```
const class_name object;
```
For example, if in the class Test defined above, we want to define a constant object, we can do it like:
```
const Test r(30);
```
## 6) Defining Class's Member function as const
A const member functions never modifies data members in an object.

Syntax:
```
return_type function_name() const;
```
Example for const Object and const Member function
```
class StarWars
{
    public:
    int i;
    StarWars(int x)    // constructor
    { 
        i = x; 
    }

    int falcon() const  // constant function
    { 
        /* 
            can do anything but will not
            modify any data members
        */
        cout << "Falcon has left the Base";
    }

    int gamma()
    { 
        i++; 
    }
};

int main()
{
    StarWars objOne(10);        // non const object
    const StarWars objTwo(20);      // const object

    objOne.falcon();     // No error
    objTwo.falcon();     // No error

    cout << objOne.i << objTwo.i;

    objOne.gamma();     // No error
    objTwo.gamma();     // Compile time error
}

Falcon has left the Base
Falcon has left the Base
10 20
```

Here, we can see, that const member function never changes data members of class, and it can be used with both const and non-const objecta. But a const object cannot be used with a member function which tries to change its data members.



# **In C++ there're two different syntax according to the place of the & operator**


## 1)Modify the passed parameters in a function: 
If a function receives a reference to a variable, it can modify the value of the variable. For example, the following program variables are swapped using references. 
```
#include<iostream>
using namespace std;
  
void swap (int& first, int& second)
{
    int temp = first;
    first = second;
    second = temp;
}
  
int main()
{
    int a = 2, b = 3;
    swap( a, b );
    cout << a << " " << b;
    return 0;
}
Output:

 3 2 
 ```
## Avoiding a copy of large structures:
 Imagine a function that has to receive a large object. If we pass it without reference, a new copy of it is created which causes wastage of CPU time and memory. We can use references to avoid this
```
struct Student {
string name;
string address;
int rollNo;
}

// If we remove & in below function, a new
// copy of the student object is created.
// We use const to avoid accidental updates
// in the function as the purpose of the function
// is to print s only.
void print(const Student &s)
{
	cout << s.name << " " << s.address << " " << s.rollNo;
}
```
## 3)In For Each Loops to modify all objects :
 We can use references in for each loops to modify all elements.
 ```
#include <bits/stdc++.h>
using namespace std;

int main()
{
	vector<int> vect{ 10, 20, 30, 40 };

	// We can modify elements if we
	// use reference
	for (int &x : vect)
		x = x + 5;

	// Printing elements
	for (int x : vect)
	cout << x << " ";

	return 0;
}
```
## 4)For Each Loop to avoid the copy of objects:
 We can use references in each loop to avoid a copy of individual objects when objects are large.  
```
#include <bits/stdc++.h>
using namespace std;

int main()
{
	vector<string> vect{"geeksforgeeks practice",
					"geeksforgeeks write",
					"geeksforgeeks ide"};

	// We avoid copy of the whole string
	// object by using reference.
	for (const auto &x : vect)
	cout << x << endl;

	return 0;
}
```
## 5)Declaration of Reference variable is preceded with ‘&’ symbol ( but do not read it as “address of”).
```
#include <iostream>
using namespace std;

int main() {
	int i=10; //simple or ordinary variable.
	int *p=&i; //single pointer
	int **pt=&p; //double pointer
	int ***ptr=&pt; //triple pointer
	// All the above pointers differ in the value they store or point to.
	cout << "i=" << i << "\t" << "p=" << p << "\t"
		<< "pt=" << pt << "\t" << "ptr=" << ptr << "\n";
	int a=5; //simple or ordinary variable
	int &S=a;
	int &S0=S;
	int &S1=S0;
	cout << "a=" << a << "\t" << "S=" << S << "\t"
		<< "S0=" << S0 << "\t" << "S1=" << S1 << "\n";
	// All the above references do not differ in their values
	// as they all refer to the same variable.
}
```





















