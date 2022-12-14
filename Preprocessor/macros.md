## Macro

> A macro is a fragment of code which has been given a name. Whenever the name is used, it is replaced by the contents of the macro. There are two kinds of macros.

The macro in C language is known as the piece of code which can be replaced by the macro value. The macro is defined with the help of #define preprocessor directive and the macro doesn’t end with a semicolon(;). Macro is just a name given to certain values or expressions it doesn't point to any memory location.

Whenever the compiler encounters the macro, it replaces the macro name with the macro value. Two macros could not have the same name.

The syntax of the macro is as shown in the following code. Here, we will have the three components:
```
#define PI 3.14
```
#define = Preprocessor Directive

PI = Macro Name

3.14 = Macro Value

```
#include<stdio.h>

// This is macro definition
#define PI 3.14

void main()
{
    // declaration and initialization of radius
    int radius = 5;
    // declaration and calculating the area
    float area = PI * (radius*radius); 
    
    // Printing the area of circle
    printf("Area of circle is %f", area);
}

```

> Predefined Macros

* Here are some predefined macros in C programming.

|Macro | Value|
|---|---|
|__DATE__	|A string containing the current date.|
|__FILE__	|A string containing the file name.|
|__LINE__	|An integer representing the current line number.|
|__STDC__	|If follows ANSI standard C, then the value is a nonzero integer.|
|__TIME__	|A string containing the current time.|


example :-
```
#include <stdio.h>
int main()
{
   printf("Current time: %s",__TIME__);   
}

```
Output => Current time: 19:54:39

## Types of MACROS

>1. Object like macro -

An object-like macro is a simple identifier which will be replaced by a code fragment. It is called object-like because it looks like a data object in code that uses it. They are most commonly used to give symbolic names to numeric constants.

You create macros with the ‘#define’ directive. ‘#define’ is followed by the name of the macro and then the token sequence it should be an abbreviation for, which is variously referred to as the macro’s body, expansion or replacement list. For example,

#define BUFFER_SIZE 1024

* By convention, macro names are written in uppercase. Programs are easier to read when it is possible to tell at a glance which names are macros.

* The macro’s body ends at the end of the ‘#define’ line. You may continue the definition onto multiple lines, if necessary, using backslash-newline. When the macro is expanded, however, it will all come out on one line. For example,
```
#define NUMBERS 1, \
                2, \
                3
int x[] = { NUMBERS };
     → int x[] = { 1, 2, 3 };
```


>2. Function-like Macro:

These macros are the same as a function call. It replaces the entire code instead of a function name. Pair of parentheses immediately after the macro name is necessary. If we put a space between the macro name and the parentheses in the macro definition, then the macro will not work. 
A function-like macro is only lengthened if and only if its name appears with a pair of parentheses after it. If we don’t do this, the function pointer will get the address of the real function and lead to a syntax error.
Below is the illustration of function-like macros:

```
#include <stdio.h>
 
// Function-like Macro definition
#define min(a, b) (((a) < (b)) ? (a) : (b))
 
// Driver Code
int main()
{
 
    // Given two number a and b
    int a = 18;
    int b = 76;
 
    printf("Minimum value between"
           " %d and %d is %d\n",
           a, b, min(a, b));
 
    return 0;
}
Output => Minimum value between 18 and 76 is 18
```

* When we use macro functions, however, unlike regular functions, they do not perform any kind of type checking. Because of this drawbacks, inline functions are usually preferable to macro functions. But because macros directly substitute their code, they reduce the overhead of a function call.


>. Stringizing

Sometimes you may want to convert a macro argument into a string constant. Parameters are not replaced inside string constants, but you can use the ‘#’ preprocessing operator instead. When a macro parameter is used with a leading ‘#’, the preprocessor replaces it with the literal text of the actual argument, converted to a string constant. Unlike normal parameter replacement, the argument is not macro-expanded first. This is called stringizing.

* The number-sign or "stringizing" operator (#) converts macro parameters to string literals without expanding the parameter definition. 


```
#include <stdio.h>
#define PRINT_MSG( x ) printf(#x "\n")
int main()
{
    PRINT_MSG(LOVE TO READ ATICLEWORLD);
    PRINT_MSG(12456);
    return 0;
}

#include <stdio.h>
// Stringizing operator #
// it converts the input into a String literal
#define STRINGIZING_OPERATOR(input) #input
int main()
{
    
    printf(STRINGIZING_OPERATOR(Coding Ninjas));
    return 0;
}

```

>. Token Pasting Operator (##)

The Token Pasting operator is also a preprocessor operator. It instructs the compiler to add or concatenate two tokens into a single string. This operator is used in the macro definition.

When expanding macros, it is frequently useful to combine two tokens into one. This is known as token concatenation or token pasting. Token pasting is performed by the '##' pre-processing operator. When a macro is expanded, the two tokens on either side of each '##' operator are combined to form a single token that replaces the '##' and the two original tokens in the macro expansion.

The token pasting (##) operator simply removes any surrounding white space and concatenates (joins together) the non-whitespace characters.

#### Syntax
The syntax of the token-pasting operator (##) is as follows:

```
#define MACRO_NAME(param1, param2) param1##param2
#define: It is a preprocessor directive in C.
MACRO_NAME: It represents the macro that has to be replaced by its value throughout the program.
Param1 / param2: The parameters that are passed to the macros for concatenation.
##: This is the token-pasting operator.
```

```
#include <stdio.h>

#define TOKEN_PASTING(param1, param2) param1##param2
int main()
{
    
    printf("The concatenated result is: %d",TOKEN_PASTING(1234,56789));
    return 0;
}
Output: 

The concatenated result is: 123456789
```
