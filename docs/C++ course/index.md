# Report for C++ course project
## Preamble
The author finds the structure of the report outlined in the project description, which 
makes perfect sense for lab reports, somewhat odd when applied to software engineering.
To help the marker mark this report, and to help the author to write it. 
He now attempts to outline how he writes the report and maps it to the sections specified in the project brief.

There are five sections mentioned in the project description.

- Abstract
- Introduction
- Code design and implementation
- Results
- Discussion and conclusions

The author believe the *Introduction* and *Results* section maps to user documentation in software development settings. So it is natural to combine them together as [documentation].
The author also merges *Code design and implementation* and *Discussion and conclusions*. They come under [technical aside].
Abstract is left as a standalone section.

  [documentation]: gstar.md
  [technical aside]: tech-aside.md


## GenAI prompts
The author used the following prompts to generate code/debug for this project:

```text
generate 10 more dummy data using the same format

libc++abi: terminating due to uncaught exception of type std::invalid_argument: Type must be one of: Elliptical or Spiral
fix
Galaxies milky_way{"Milky way", coord, "Spiral", 10}; line 29

do the same validation for minute and seconds in RightAscension
```

<!-- !!! failure "Substandard commits"
    The commits for the project are deliberately kept small and sometimes incomplete 
    (in terms of code function). This is below the professional standard the author normally would hold 
    himself up to. However the choice is made to 'demonstrate the work submitted is my own' and comply with
    the mark scheme.  -->