# Technical aside

The goal of this project, as detailed in the project brief, is to

> Design and apply a class hierarchy for storing observational data of astronomical objects

## Choice of objects
For simple objects, this is straight forward. As mentioned in the documentation, I only designed 
two object types: Stars and Galaxies. They share two common properties: name and coordinates.
So it is sensible to create a `Observable` object, containing `name` and `coordinates` properties,
that acts as a base class.

All input validation in `Observable` and its child are based on common sense. For example, temperature, 
when written in Kelvin, should not be below zero. I wrote a special class `Coordinates` to capture 
coordinate data information. This choice is made because unlike temperature and other data, it coordinate
data does not find itself a natural way to be represented as one of basic data types in C++. Furthermore,
the choice of `class` as oppose to `struct` is made due to input validation concerns.

## "Minimum functionality"
<!-- The minimal functionality -->