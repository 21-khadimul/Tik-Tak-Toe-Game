Inheritance 

<br>

## Problem 01:
Create a generic base class called building that stores the number of floors a building has,
the number of rooms, and its total square footage. Create derived class called house that
inherits building and also stores the number of bedrooms and the number of bathrooms.
Next, create a derived class called office that inherits building and also stores the number
of fire extinguishers and the number of telephones.
<br>

Theory:<br>

Inheritance in C++ is a fundamental object-oriented programming concept that allows a derive class to inherit properties and behaviors (data members and methods) from base class . This promotes code reusability and establishes a hierarchical relationship between classes, enabling polymorphism. 
<br>
Code:
<br>

cpp
#include <iostream>
using namespace std;

class Building {
protected:
    int floors;
    int rooms;
    float squareFootage;

public:
    Building(int f, int r, float sq) : floors(f), rooms(r), squareFootage(sq) {}

    void display() {
        cout << "Building Details:" << endl;
        cout << "Floors: " << floors << endl;
        cout << "Rooms: " << rooms << endl;
        cout << "Total Square Footage: " << squareFootage << " sq ft" << endl;
    }
};

class House : public Building {
private:
    int bedrooms;
    int bathrooms;

public:

    House(int f, int r, float sq, int bdr, int bth) 
        : Building(f, r, sq), bedrooms(bdr), bathrooms(bth) {}

    void display() {
        Building::display(); 
        cout << "House Details:" << endl;
        cout << "Bedrooms: " << bedrooms << endl;
        cout << "Bathrooms: " << bathrooms << endl;
    }
};


class Office : public Building {
private:
    int fireExtinguishers;
    int telephones;

public:

    Office(int f, int r, float sq, int fe, int t) 
        : Building(f, r, sq), fireExtinguishers(fe), telephones(t) {}

    void display() {
        Building::display(); 
        cout << "Office Details:" << endl;
        cout << "Fire Extinguishers: " << fireExtinguishers << endl;
        cout << "Telephones: " << telephones << endl;
    }
};


int main() {

    House myHouse(2, 5, 2500, 3, 2);
    cout << "My House Info:" << endl;
    myHouse.display();
    cout << endl;

    Office myOffice(5, 10, 5000, 4, 12);
    cout << "My Office Info:" << endl;
    myOffice.display();

    return 0;
}

<br>

Output:
<br>
![](src/oop4.png)


Discussion and conclusion:<br>

From the above code we have learned how to reuse properities of base classes in derived classes using inheritance.

<br>

## Problem 02:
When a base class is inherited as public by the derived class, what happens to its public
members? What happens to its private members? If the base is inherited as private by
the derived class, what happens to its public and private members?
<br>

Theory:<br>

When a base class is inherited by a derived class in C++, the access specifier (public, private, or protected) used during inheritance affects the accessibility of the base class members in the derived class. Here's a breakdown of what happens to the public and private members based on the inheritance type:

1. Public Inheritance<br>
When a base class is inherited publicly:

Public Members: The public members of the base class remain public in the derived class. They can be accessed by objects of the derived class and any code that has access to the derived class object.

Private Members: The private members of the base class are not accessible directly in the derived class. They can only be accessed through public or protected member functions of the base class.
<br>
Example:<br>

cpp
Copy code
#include<iostream>
using namespace std;
class Base {
public:
    int pubValue;
private:
    int privValue;
};

class Derived : public Base {
public:
    void acc() {
        pubValue;  
       
        cout<<pubValue;
        cout<<"f"<<endl;
    }
};

int main() {
    Derived d;
    d.pubValue = 10;

    d.acc();
}


2. Private Inheritance<br>
When a base class is inherited privately:

Public Members: The public members of the base class become private in the derived class. They cannot be accessed by any code outside the derived class.

Private Members: The private members of the base class remain not accessible in the derived class, just as in public inheritance.
<br>
Example:<br>

cpp
#include<iostream>
using namespace std;
class Base {
public:
    int pubValue;
private:
    int privValue;
};

class Derived : private Base {
public:
    void acc() {
        pubValue;  
        
        cout<<pubValue;
        cout<<"f"<<endl;
    }
};

int main() {
    Derived d;
    d.pubValue = 10; // error, can't accessible in main

    d.acc();
}



Discussion and conclusion:<br>
Public Inheritance:
Public members: Remain public in the derived class.
Private members: Not accessible in the derived class.
Private Inheritance:
Public members: Become private in the derived class and accessible in derived class but not main function.
Private members: Not accessible in the derived class.


<br>
<br>

## problem 03:
Explain what protected means. (Be sure to explain what it means both when referring
to members of a class and when it is used as an inheritance access specifier.)
<br>

Theory:<br>

Protected as a Class Member Access Specifier:
When a class member is declared as protected, it means:

The member is accessible within the class itself, just like private members.
The member is also accessible by derived classes but not accessible by any other part of the program.
In simpler terms, protected members are available within the class that declares them and in any class that inherits from that class, but not to any code outside those classes.
Protected as an Inheritance Access Specifier:
When protected inheritance is used, the accessibility of the base class members changes in the derived class:

Public members of the base class become protected in the derived class.
Protected members of the base class remain protected in the derived class.
Private members of the base class remain inaccessible in the derived class, as usual (unless accessed via public or protected member functions of the base class).
Protected inheritance is used when you want to allow a derived class to access the base class members (like in public inheritance) but still keep them hidden from the outside world (like in private inheritance).

Discussion and conclusion:<br>
rotected members of a class are accessible within the class and its derived classes, but not outside.
Protected inheritance changes the public members of the base class into protected members in the derived class while keeping protected members as protected.
<br>
<br>


## Problem 04:
When one class inherits another, when are the classesâ€™ constructors called? When are
their destructors called?

Theory:<br>

Constructor Call Order:
When a derived class object is created:

The base class constructor is called first, before the derived class constructor.
The derived class constructor is called after the base class constructor has finished.

Destructor Call Order:
When a derived class object is destroyed (goes out of scope or is deleted):

The derived class destructor is called first.
After the derived class destructor has finished, the base class destructor is called.

Discussion and conclusion:<br>
Base class constructor is called first, then the derived class constructor.Derived class destructor is called first, then the base class destructor.
<br>

<br>


## Problem 05:
Given this skeleton, fill in the details as indicated in the comments:
<br>

cpp
# include <iostream >
using namespace std;
class planet
{
protected :
double distance ; // miles from the sun
int revolve ; // in days
public :
planet ( double d, int r) { distance = d; revolve = r; }
};

class earth : public planet
{
double circumference ; // circumference of orbit
public :
/*
Create earth ( double d, int r). Have it pass the
distance and days of revolution back to planet .
Have it compute the circumference of the orbit .
( Hint : circumference = 2r *3.1416.)
*/
/*
Create a function called show () that displays the
information .
*/
};
int main ()
{
earth ob (93000000 , 365) ;
ob. show ();
return 0;
}

<br>
Theory:<br>

Inheritance in C++ is a fundamental object-oriented programming concept that allows a derive class to inherit properties and behaviors (data members and methods) from base class . This promotes code reusability and establishes a hierarchical relationship between classes, enabling polymorphism. 
<br>

Code:

<br>

cpp
#include <iostream>
using namespace std;

class planet {
protected:
    double distance; 
    int revolve;     
public:
   
    planet(double d, int r) : distance(d), revolve(r) {}
};

class earth : public planet {
    double circumference; 
public:
    
    earth(double d, int r) : planet(d, r) {
       
        circumference = 2 * distance * 3.1416;
    }

   
    void show() {
        cout << "Distance from the sun: " << distance << " miles" << endl;
        cout << "Days of revolution: " << revolve << " days" << endl;
        cout << "Circumference of orbit: " << circumference << " miles" << endl;
    }
};

int main() {
    earth ob(2210018, 365); 
    ob.show(); 
    return 0;
}


Output:
<br>
![](src/oop5.png)
<br>

Discussion and conclusion:<br>
From the above code we have learned how to reuse properities of base classes in derived classes using inheritance.


<br>
<br>

## Problem 06:
<br>
Fix the following program:
<br>

cpp
/*
A variation on the vehicle hierarchy . But
this program contains an error . Fix it. Hind :
try compiling it as is and observe the error
messages .
*/
# include <iostream >
using namespace std;
// A base class for various types of vehicles .
class vehicle
{
int num_wheels ;
int range ;
public :
vehicle (int w, int r)
{
num_wheels = w;
range = r;
}
void showv ()
{
cout << " Wheels : " << num_wheels << â€™\nâ€™;
cout << " Range : " << range << â€™\nâ€™;

}
};
enum motor {gas , electric , diesel };
class motorized : public vehicle
{
enum motor mtr ;
public :
motorized ( enum motor m, int w, int r) : vehicle (w, r)
{
mtr = m;
}
void showm ()
{
cout << " Motor : ";
switch (mtr )
{
case gas : cout << "Gas \n";
break ;
case electric : cout << " Electric \n";
break ;
case diesel : cout << " Diesel \n";
break ;
}
}
};
class road_use : public vehicle
{
int passengers ;
public :
road_use (int p, int w, int r) : vehicle (w, r)
{
passengers = p;
}
void showr ()
{
cout << " Passengers : " << passengers << â€™\nâ€™;
}
};
enum steering { power , rack_pinion , manual };
class car : public motorized , public road_use
{
enum steering strng ;
public :
car ( enum steering s, enum motor m, int w, int r, int p) :
road_use (p, w, r), motorized (m, w, r), vehicle (w, r)
{

strng = s;
}
void show ()
{
showv ();
showr ();
showm ();
cout << " Steering : ";
switch ( strng )
{
case power : cout << " Power \n";
break ;
case rack_pinion : cout << " Rack and Pinion \n";
break ;
case manual : cout << " Manual \n";
break ;
}
}
};
int main ()
{
car c(power , gas , 4 , 500 , 5);
c. show ();
return 0;
}

<br>

Theory:<br>

Virtual inheritance is a way to prevent duplicate base class instances when multiple inheritance is used. If a class inherits from multiple classes that share a common base, virtual inheritance ensures that only one instance of the base class is inherited by the derived class, avoiding ambiguity and redundancy. It's commonly used in cases like the "diamond problem," where a base class is inherited multiple times through different paths.

<br>

Code:

<br>

cpp
#include <iostream>
using namespace std;

class vehicle {
    int num_wheels;
    int range;
public:
    vehicle(int w, int r) : num_wheels(w), range(r) {}

    void showv() {
        cout << "Wheels: " << num_wheels << '\n';
        cout << "Range: " << range << '\n';
    }
};

enum motor { gas, electric, diesel };

class motorized : public virtual vehicle {
    enum motor mtr;
public:
    motorized(enum motor m, int w, int r) : vehicle(w, r) {
        mtr = m;
    }

    void showm() {
        cout << "Motor: ";
        switch (mtr) {
            case gas: cout << "Gas \n"; break;
            case electric: cout << "Electric \n"; break;
            case diesel: cout << "Diesel \n"; break;
        }
    }
};

class road_use : public virtual vehicle {
    int passengers;
public:
    road_use(int p, int w, int r) : vehicle(w, r) {
        passengers = p;
    }

    void showr() {
        cout << "Passengers: " << passengers << '\n';
    }
};


enum steering { power, rack_pinion, manual };


class car : public motorized, public road_use {
    enum steering strng;
public:
    car(enum steering s, enum motor m, int w, int r, int p)
        : vehicle(w, r), motorized(m, w, r), road_use(p, w, r) {
        strng = s;
    }

    void show() {
        showv(); 
        showr();
        showm();
        cout << "Steering: ";
        switch (strng) {
            case power: cout << "Power \n"; break;
            case rack_pinion: cout << "Rack and Pinion \n"; break;
            case manual: cout << "Manual \n"; break;
        }
    }
};

int main() {
    car c(power, gas, 4, 500, 5);
    c.show();
    return 0;
}




Output:
<br>
![](src/oop6.png)

Discussion and conclusion:<br>
From the above code we have learned how to use virtual inheritance in cases like diamond problems.

<br>
<br>
<br>

<br>
<br>
<br>


Virtual Functions

<br>

## Problem 01:
What is a virtual function?
<br>

Answer:<br>
Virtual function: A virtual function is a member function in a base class that is declared with the virtual keyword. It is meant to be overridden in derived classes. When a virtual function is called through a base class pointer or reference, the version of the function that is called depends on the type of the object being pointed to, not the type of the pointer. This enables run-time polymorphism.
<br>

## Problem 02: 
What types of functions cannot be made virtual?

<br>
Answer:<br>
Non-virtual functions:

Constructors cannot be virtual.
Static functions cannot be virtual.
Friend functions (since they aren't members of the class) cannot be virtual.
<br>

## Problem 03: 
How does a virtual function help achieve run-time polymorphism? Be specific.
<br>

Answer:<br>
Run-time polymorphism: Virtual functions help achieve run-time polymorphism by allowing derived class objects to be treated as objects of the base class. When a virtual function is called on a base class pointer (or reference) that actually points to a derived class object, the derived class's version of the function is called. This decision is made at run-time, not at compile-time, enabling flexibility in handling different types of objects through base class pointers.
<br>

## Problem 04: 
What is a pure virtual function?
<br>

Answer:<br>
Pure virtual function: A pure virtual function is a virtual function that is not implemented in the base class. It is declared with the syntax = 0 in the base class, forcing derived classes to override it. If a derived class does not override the pure virtual function, it also becomes an abstract class.
<br>

## Problem 05: 
What is an abstract class? What is a polymorphic class?
<br>

Answer:<br>
Abstract class: An abstract class is a class that contains at least one pure virtual function. It cannot be instantiated directly and serves as a blueprint for derived classes, which must provide implementations for the pure virtual functions.
<br>
Polymorphic class: A polymorphic class is a class that contains at least one virtual function. It allows for polymorphic behavior, meaning that objects of the class can exhibit different behaviors depending on which derived class they belong to.


## Problem 06:
Is the following fragment correct? If not, why not?
cpp
class base
{
public :
virtual int (int a) = 0;
// ...
};
class derived : public base
{
public :
int f(int a, int b) { return a*b; }
// ...
}:


<br>
Answer:<br>
The given fragment has several issues.
Issues:
Syntax error in virtual function declaration:

In the base class, the declaration of the pure virtual function is incorrect:
cpp

virtual int (int a) = 0;

This is missing the function name. A virtual function must have a proper name and parameters. For example:

cpp
virtual int f(int a) = 0;

Mismatch in function signature:

The derived class is supposed to override the pure virtual function from the base class. However, in the derived class, the function:
cpp
int f(int a, int b) { return a * b; }

It does not match the signature of the base class's pure virtual function f(int a). For it to properly override the base class function, the signature must match exactly, both in the number of parameters and their types. The correct function in the derived class should be:

cpp
int f(int a) override { return a * 2; }

Corrected Code:
cpp
class base
{
public:
    virtual int f(int a) = 0;  
};

class derived : public base
{
public:
    int f(int a) override { return a * 2; }  
};


<br>
Discussion and conclusion:<br>
The base class contains a pure virtual function f(int a), which must be overridden by any derived class.In the derived class, the f function must have the same signature (name and parameters) as the base class virtual function for it to be considered an override.


<br>
<br>


## Problem 07:
Is the virtual quality inherited?
<br>

Answer:<br>
Yes, the virtual quality is inherited in C++.

When a member function of a base class is declared as virtual, it retains its virtual nature in all derived classes, even if the virtual keyword is not explicitly repeated in the derived class. This means that the derived class can override that virtual function, and run-time polymorphism will apply as expected when the function is called through a base class pointer or reference.

Inherited Virtual Nature: Once a function is declared virtual in the base class, it is virtual in all classes derived from it, even if you don't explicitly write the virtual keyword again in the derived class.

Overriding: A derived class can override the base class's virtual function. When a function is overridden, the derived class's version is called when using a base class pointer or reference at run time (run-time polymorphism).

<br>
<br>
