# Assignment 7:Magic Squares!
A magic square of order n is an arrangement of n × n numbers, usually distinct integers, in a square, such that the n numbers in all rows, all columns, and both diagonals sum to the same constant (see Wikipedia: Magic Square). 

## Checking the row values

* We give you two text files: Mercury.txt and Luna.txt

* For each file: open the file, and check that all rows indeed sum to the same constant.

## Hints
* Copy both text files to the root directory of your project. This is the directory that contains the src folder. Alternative:Use absolute paths to the files (c:\somedir\Mercury.txt on Windows or /Users/myuser/Mercury.txt on Mac)

* You will need to handle or rethrow IOException

* Read the files line by line as explained during the lecture today.

* Use ... = myLine.split("\t"); to break apart each line at the tab character, producing an array of String (String[]),
each containing one value. Consult the Java API reference for String.split).

* Finally, use ... = Integer.valueOf(substring); to transform each string value into an integer value. 

## Optional part:Column/Diagonal Values

Optionally, try to check that the columns and the diagonal also sum to the same constant. This is slightly trickier!

## Submission Instruction

Submit your MagicSquares.java file via Stellar. 