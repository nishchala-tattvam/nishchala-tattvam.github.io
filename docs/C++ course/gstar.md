# `gstar`
## Introduction
This is a demo library for the project of the C++ course. The author chose the first option: star catalog: 
"Design and apply a class hierarchy for storing observational data of astronomical objects".

This library provides three main APIs for storing structured data, `RaDec`, `Stars` and `Galaxies`.

## `RaDec`
`RaDec` represents coordinates of celestial objects in the right ascension-declination based system.
It is one of the basic properties of both `Stars` and `Galaxies`.

Within `RaDec`, it contains two data members: `RightAscension` for representing right ascension and `Declination` for declination. Here is a pseudo code.

```cpp linenums="1"
class RaDec{
private:
 RightAscension ra_{};
 RightAscension dec_{};
}
```

### Instantiation
To instantiate object of type `Ra`, simply pass in coordinates in the form of (hours, minutes, seconds).

```cpp linenums="1"
RightAscension ra{5, 34, 31.95};
```

For declination, the coordinates should be passed in the form of (degree, seconds, arcseconds)

```cpp linenums="2"
Declination dec{22, 0, 52.2};
```

To create a `RaDec` object, we may pass in `RightAscension` and `Declination` as arguments:

```cpp linenums="3"
RaDec coord{ra, dec};
```

### Access member information
To access information about the coordinates, we may print it.

```cpp linenums="4"
std::cout << RaDec coord{ra, dec}; << std::endl;
```

```text title="Output"
Right Ascension: 4h 35m 55.24s 
Declination: 16° 30′ 33.5″
```

Notice the data members in `RaDec` are protected. To programmatically access them, we have provided
the `get_ra()` and `get_dec()` methods.

### Modify member information
We provided appropriate setters for changing the right ascension data and declination data. They are
`set_ra()` and `set_dec()` respectively.

!!! note "Access pattern"
    The pattern described above applies to all public APIs. Specifically we may print data via `std::cout`,
    and programmatically access/modify the information with appropriate getter/setter methods. Because this library is for
    demonstration purpose only, we omit the name of some getter methods here. 

## `Stars`
Class `Stars` represents stars.

It contain the following information:

- name (string)
- coordinates
- spectral type (Harvard system)
- temperature (in K)
- age (in years)
- radius (in km)
- mass (in kg)

### Instantiation
To instantiate a `Star`, 

```cpp linenums="5"
Stars crab_pulsar{
    "Crab Pulsar (PSR B0531+21)", // name
    coord, // coordinates
    "O", // spectral type
    1.6e6, // temperature (in K)
    970.0, // age (in years)
    10.0,   // radius (in km)
    2.8e30  // mass (in kg)
};
```

### Access member information

```cpp linenums="14"
std::cout << crab_pulsar << std::endl;
```

```text title="Output"
crab-pulsar
Right Ascension: 5h 34m 31.95s 
Declination: 22° 0′ 52.2″
Spectral Type: O
Temperature: 1.6e+06K
Age: 970years 
Radius: 10km 
Mass: 2.8e+30kg 
```

## `Galaxies`
`Galaxies` capture information related to galaxies. 

It has the following property:

- name
- coordinates
- diameter (in lightyears)
- type (Spiral or Elliptical)

### Instantiation
To record a galaxy's information

```cpp linenums="15"
Galaxies milky_way{
    "Milky way", 
    coord, 
    "Spiral", 
    10
};
```

### Access member information

```cpp linenums="21"
std::cout << crab_pulsar << std::endl;
```

```text title="Output"
milky-way
Right Ascension: 5h 34m 31.95s 
Declination: 22° 0′ 52.2″
Type: Spiral
Diameter: 10 lightyears
```