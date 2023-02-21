# Coding Standard
Coding standards are a set of guidelines that reputable software development companies expect their programmers to adhere to. According to their organization's needs and the kinds of software they create, they typically create their own coding standards and rules. Maintaining coding standards is crucial for programmers; otherwise, the code would be rejected during code review.   

For our project, we would like to implement and enforce some coding standards to achieve uniformity across the various different repositories and to make collaboration easier.   

> See also [Housekeeping](housekeeping.md) and [Optimization](optimization.md) as well as [this](https://www.cs.bu.edu/courses/cs112/problem_sets/coding_standards.html#:~:text=There%20are%20two%20standard%20formats%20for%20braces%2C%20either,a%20pair%20is%20lined%20up%20%20vertically.%20) page by Wayne Snyder from Boston University.
    
## Purpose of Having Coding Standards:

- A coding standard gives a uniform appearance to the codes written by different engineers.
- It improves readability, and maintainability of the code and it reduces complexity also.
- It helps in code reuse and helps to detect error easily.
- It promotes sound programming practices and increases efficiency of the programmers.

Below is the outlined coding standard going forward.
## Standardization of Headers for Different Modules
A header is the block of text at the top of a class, it should go at the top of the class and include the following things:
- Name of the module
- Date of module creation
- Author of the module
- Modification history
- Synopsis of the module about what the module does
- Different functions supported in the module along with their input output parameters
- Global variables accessed or modified by the module

Header comments (see below) should use the multi-line comment style (i.e., use \* and */) and all other comments should use the single-line (i.e., use //) convention. This is because you can surround single-line comments with a multi-line comment, but not multi-line around multi-line — if you want to comment out a region of code during development, and you used multi-line comments everywhere, you are stuck.  

Here is an example of a header comment:

```java
/*
  * Customer.java
  * by John Doe (jdoe@example.com)
  * 2022-03-20
  *
  * This class represents a bank customer. It contains basic
  * fields and references to the customer's accounts.
  *
  * Note that the main() method's input data file must be
  * called "finance_data.txt". For the format of this
  * file, see comment above the getData() method.
  *
  * Credits: The code for the hash table in the
  * calculateInterestRate() method was taken from
  * "Algorithms and Data Structures," by George Guidal, pp. 234-35.
  */
```

> 📝 **Note:** You can generate some default file header comments with IntelliJ IDEA, see [their page on how to do this](https://www.jetbrains.com/help/idea/using-file-and-code-templates.html#syntax).

A header should also (for our purposes) come in the form of a repository's `README.md` file. Each repository should be initialized with a README, and if it is a plugin then it must also be initialized with a properly formatted `plugin.yml` file.   

For better understanding and maintenance of the code, the header of different modules should follow some standard format and information. The header format must contain the following:

### **Name of the Module**
Here is the name of the project or module for which the repository was made. Name should be short and concise by giving an accurate description of the main purpose of that plugin or project.    

For example, the [`PlayerStats`](../core/playerstats.md) module, although it will handle the database connection  and data storage for the rest of the project, it's main purpose is to record information about the player in the form of statistics therefore: `PlayerStats`.   

The [`Market`](../mech/economy/market.md) module handles the entire economy system of the project by implementing an API but it's main purpose is to build a functioning dynamic market economy, thus: `Market`.

### **Proper Dating**
The creation of the module as well as the dates of any major or minor updates and/or bug fixes must be correctly recorded to keep things organized. Please follow `ISO 8601` (YYYY-MM-DD). 

### **Crediting of Contributors**
Please accurately credit authors of the code including yourself and any other contributor such as authors of open-source works that you took from. This is to prevent any licencing or copyright issues as well as serve as a reference as to who should be contacted in the event of a bug or feature request.

### **Modification History**
The complete and unadulturated modification history of the module and its files should be documented.    

This includes but not limited to: 
- The creation and maintaining of a proper changelog that correctly uses SemVer 
  - > See: [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) as well as [Semantic Versioning](https://semver.org/spec/v2.0.0.html)
- Proper commits and commit comments
  - > See: [Proper Git Commits](commits.md) on how to practice good commits
- Commenting out of deprecated code rather than deleting for posterity and documentation purposes
- When possible, add proper annotations such as `@Deprecated` when planning to remove a method in the future

### **Synopsis of the Module**
A short summary of the module and what it aims to do and currently does should be included.   

This also includes different functions supported in the module along with their input output parameters (i.e. commands and command arguments/parameters and the intendend outputs)   

Be descriptive!

## Naming Conventions for Local Variables, Global Variables, Constants and Functions
Below are some naming conventions to follow when writing code:

- Meaningful and understandable variables name helps anyone to understand the reason of using it.
- Local variables should be named using camel case lettering starting with small letter (e.g. localData) 
- Global variables names should start with a capital letter (e.g. GlobalData)
- Constant names should be formed using capital letters only (e.g. CONSDATA)
- Avoid the use of digits in variable names
- The names of the function should be written in camel case starting with small letters
- The name of the function must describe the reason of using the function clearly and briefly

## Proper Indentation and Spacing
> This was covered briefly in [Housekeeping](housekeeping.md)
   
Proper indentation is very important to increase the readability of the code. For making the code readable, programmers should use White spaces properly. Some of the spacing conventions are given below:

- There must be a space after giving a comma between two function arguments.
- Each nested block should be properly indented and spaced.
- Proper indentation should be there at the beginning and at the end of each block in the program.
- Curly brace goes at the end of the line that starts the class, method, loop, etc., and the closing brace is on a line by itself, lined up vertically with the start of the first line:

This will look like this:
```java
public class SomeClass {

    public SomeClass() {
        ...;
    }

    public int someMethod(int n, float m) {
        ...;
        for (int i = 0; i < someField; i++) {
            ...;
        }
        ...;
    }
}
```

## Code Should be Well Documented
The code should be properly commented for understanding easily. Comments regarding the statements increase the understandability of the code.   

For each significant field or variable declaration, give a brief comment stating the use of the variable, and when useful, the units (e.g., feet or inches).

Give end-of-line comments for any line of code that is trickly, or non-obvious; don’t overdo this, and don’t just rephrase the Java in English, but DO provide concise, informative comments to help the reader (who knows Java idioms, but not your code) understand what is going on.   

Create Javadoc comments wherever and whenever possible, [here](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html) is a tutorial on how to use the Javadoc feature in your code.

## Reduce Function Length Whenever Possible
Lengthy functions are very difficult to understand. That’s why functions should be small enough to carry out small work and lengthy functions should be broken into small ones for completing small tasks.