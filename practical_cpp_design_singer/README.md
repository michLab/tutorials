# Practical C++ design
From Programming to Architecture
Second Edition

Adam B. Singer

# Aim

The aim of thi tutorial is to create calculator app, which incorporates the
Reverse Polish Notation algorithm.

# The calculator requirements

1.  The calculator will be stack based; the stack size should not be
hard-­coded.
2. The calculator will use RPN to perform operations.
3. The calculator will exclusively operate on floating-point numbers; a
technique for entering input numbers (including scientific notation)
should be implemented.
4. The calculator will have the ability to undo and redo operations; the
undo/redo stack sizes should be conceptually unlimited.
5. The calculator will have the ability to swap the top two elements of
the stack.
6. The calculator will be able to drop (erase) an element from the top of
the stack.
7. The calculator will be able to clear the entire stack.
8. The calculator will be able to duplicate the element from the top of
the stack.
9. The calculator will be able to negate the element from the top of the
stack.
10. The calculator will implement the four basic arithmetic operations:
addition, subtraction, multiplication, and division. Division by 0 is
impermissible.
11. The calculator will implement the three basic trigonometric
functions and their inverses: sin, cos, tan, arcsin, arccos, and arctan.
Arguments to the trigonometric functions will be given in radians.
12. The calculator will implement functions for y^x and y^(1/x) .
13. The calculator will implement a runtime plugin structure to expand
the operations the calculator can perform.
14. The calculator will implement both a command line interface (CLI)
and a graphical user interface (GUI).
15. The calculator will not support infinity or imaginary numbers.
16. The calculator will be fault tolerant (i.e., it will not crash if the
user gives bad input) but does not need to handle floating-point
exceptions.
