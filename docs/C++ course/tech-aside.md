# Technical aside
The goal of this project, as detailed in the project brief, is to

> Design and apply a class hierarchy for storing observational data of astronomical objects

## Choice of objects
For simple objects, this is straight forward. As mentioned in the documentation, the author only designed 
two object types: Stars and Galaxies. They share two common properties: name and coordinates.
So it is sensible to create a `Observable` object, containing `name` and `coordinates` properties,
that acts as a base class.

All input validation in `Observable` and its child are based on common sense. For example, temperature, 
when written in Kelvin, should not be below zero. The author wrote a special class `Coordinates` to capture 
coordinate data information. This choice is made because unlike temperature and other data, it coordinate
data does not find itself a natural way to be represented as one of basic data types in C++. Furthermore,
the choice of `class` as oppose to `struct` is made due to input validation concerns.

## "Minimum functionality"
The author did not find a natural way to incorporate the "minimal functionality" part of the project 
specification to demonstrate a class hierarchy. If he were to do so, he would need to implement a pandas 
like database designed specifically for astronomical observables. This is beyond the time allowed for a 
project like this. Even in production settings, he would recommend a SQL like database as solution instead 
of writing a custom astronomy database from scratch unless the user's needs and other non-functional requirements 
justify it.

On account of the above, the "minimal functionality" is separate from the main `gstar` library implementation 
and is shown as demo code in the `samples` folder.

## Testing
Test coverage is quite limited due to time constraints. However, all tests written are passed. 

## "Advanced features"
The project brief asked the author to 

> demonstrate the key ones (advanced code features) using short code snippets

Please refer to section [GoogleTest] and [cmake] on this site. Please note that the references sections list
the official tutorial which the author believe to be excellent learning materials.
Therefore the site merely acts as a quick summary/references for the commands the author use regularly.
Explanations are only added when the author believes it justifies to provides new information 
or his own interpretation to the official tutorial. Detailed explanation may be missing.

 [GoogleTest]: ../Software/C++/google-test.md
 [cmake]: ../Software/C++/cmake.md

 ## Beyond this project
 The code and features in this project is minimal. There are some obvious room for improvement.
 For example, the regex sniffer could be more robust and flexible, allowing for varied data structure
 instead of hard coding it. How the code could be extended depends on user needs. As mentioned before,
 a very evolved form of this project would be a SQL like database customized for astrophysics data.