# Assignment 1

In this assignment, you will create a program that computes the distance an object will fall in Earth's gravity

## Part One

1. Create a new class called GravityCalculator. 
2. Copy and paste the following initial version: 

```
class GravityCalculator {

public static void main(String[] arguments) 

{
double gravity = -9.81; // Earth's gravity in m/s^2

double initialVelocity = 0.0;

double fallingTime = 10.0;

double initialPosition = 0.0;

double finalPosition = 0.0;

 System.out.println("The object's position after " + fallingTime +
" seconds is " + finalPosition + " m.");
}
}
```
3. Run it in Eclipse (Run → Run As → Java Application). 
What is the output of the unmodified program? Include this as a comment in the source code of your submission. 

## Part Two

Modify the example program to compute the position of an object after falling for 10 seconds, outputting the position in 
meters. The formula in Math notation is: 

x(t) = 0.5 × at^2+ vit + xi

## Variable&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     Meaning&nbsp;&nbsp;&nbsp;&nbsp;    Value
a&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;      Acceleration (m/s^2)&nbsp;&nbsp;&nbsp;&nbsp;-9.81 

t&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Time (s)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;10 

vi&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Initial velocity (m/s)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0 

xi&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Initial position&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0 

 Note: The correct value is -490.5 m. Java will output more digits after the decimal place, but that is unimportant.

 ## Submission Instruction
 Submit your GravityCalculator.java file via Stellar

 MIT OpenCourseWare
http://ocw.mit.edu 

6.092 Introduction to Programming in Java
January (IAP) 2010

For information about citing these materials or our Terms of Use, visit: http://ocw.mit.edu/terms.
## Contributing

Contributions are always welcome!

See `contributing.md` for ways to get started.

Please adhere to this project's `code of conduct`.


## Acknowledgements

 - [Awesome Readme Templates](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
 - [Awesome README](https://github.com/matiassingers/awesome-readme)
 - [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)

