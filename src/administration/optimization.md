# Optimization
This section discusses various methods of keeping code optimized. This project introduces some very resource intensive mechanics and in-order to improve server performance wherever possible we must first begin with the code itself in-order to minimize performance impact and reduce memory usage and consumption.

## Avoid Writing Long Methods
The methods should not be too long and should be specific to perform single functionality. It is better for maintenance as well as performance since while class loading and during method call, the method is loaded in stack memory. If methods are large with too much processing they will consume memory as well as CPU cycles to execute.    

Try to break the methods into smaller ones at suitable logical points. Also, if you want to strengthen your skills in Java then enroll with Geeksforgeeks Java Programming Foundation – Self-Paced course and learn the basic concepts, data types, operators, functions & more.

## Use Efficient Data Structures and Algorithms 
Choose the most appropriate data structures and algorithms for your specific use case. For example, use `HashMap` instead of a `List` if you need fast lookups, or use a priority queue instead of sorting an array if you only need the smallest or largest items.

## Minimize Object Creation
Creating and destroying objects in Java can be expensive. Use object pooling to reuse objects instead of creating new ones, and use immutable objects to avoid unnecessary object creation.

## Use the StringBuilder Class for String Concatenation
When concatenating strings in a loop or other performance-critical code, use the StringBuilder class instead of the + operator, which creates new strings and can be slow.    

A string is an immutable class the object created by String cannot be reused. So if we need to create a large string in case of SQL queries etc it is bad practice to concatenate the String object using the ‘+’ operator.    

This will lead to multiple objects of String created leading to more usage of heap memory. In this case, we can use StringBuilder or StringBuffer, the former is preferential over the latter since it has a performance advantage due to non-synchronized methods. The sample is provided below as an illustration which is to be avoided as follows:

```java
 String query = String1+String2+String3;
```

instead, do this:

```java
StringBuilder strBuilder = new StringBuilder(“”);

strBuilder.append(String1).append(String2).append(String3);

String query = strBuilder.toString();            
```

## Use the Enhanced "for" Loop
When iterating over collections, use the enhanced for loop (for-each loop) instead of a regular for loop, as it is generally more efficient.   

While iterating through any collection get the size of the collection beforehand and never get it during iteration. The sample is provided below as an illustration which is to be avoided as follows:

```java
List<String> objList = getData();
for (int i = 0; i < objList.size(); i++) { execute code ..}
```

instead, do this:

```java
List<String> objList = getData();
int size = objList.size();
for (int i = 0; i < size; i++) { execute code ..} 
```

## Avoid Multiple If-else Statements
We use conditional statements in our code for decision-making. The conditional statements should not be overused. If we are using too many conditional if-else statements it will impact performance since JVM will have to compare the conditions. This can become worse if the same is used in looping statements like for, while, etc.    

If there are too many conditions in your business logic try to group the conditions and get the boolean outcome and use it in the if statement. Also, we can think of using a switch statement instead of multiple if-else if possible. Switch statement has a performance advantage over if – else. The sample is provided below as an illustration which is to be avoided as follows:

```java
if (condition1) {

    if (condition2) {

        if (condition3 || condition4) { execute ..}

        else { execute..}
```
instead, do this:

```java
boolean result = (condition1 && condition2) && (condition3  || condition4)  
```
## Avoid Unnessary Method Calls
Minimize the number of method calls in your code, especially in loops or other performance-critical code. For example, cache the result of a method call if it doesn't change between calls.

## Optimize Memory Usage
Avoid unnecessary object creation, use primitive data types when possible, and free up memory when it's no longer needed. This can help reduce memory usage and improve performance.   

Usage of primitive types over objects is beneficial since the primitive type data is stored on stack memory and the objects are stored on heap memory. If possible, we can use primitive types instead of objects since data access from stack memory is faster than heap memory. So it is always beneficial to use `int` over `Integer` or `double` over `Double`.    

This also applies to the use of `BigDecimal`.    

We know that BigDecimal class provides accurate precision for the decimal values. Over usage of this object hampers the performance drastically specifically when the same is used to calculate certain values in a loop.   

BigDecimal uses a lot of memory over long or double to perform calculations. If precision is not the constraint or if we are sure the range of the calculated value will not exceed long or double we can avoid using BigDecimal and use long or double with proper casting instead.

## Avoid Creating Big Objects Often
There are certain classes that act as data holders within the application. These objects are heavy and their creation should be avoided multiple times. An example of such objects is the DB connection objects or system configuration objects or session objects for the user after login.    

These objects used a lot of resources while created. We should reuse these objects instead of creating them as creation will drastically hamper the application performance due to more memory usage. We should use the Singleton pattern wherever possible to create a single instance of the object and reuse it wherever required or clone the object instead of creating a new one.

## Use Stored Procedures Instead of Queries
It is better to write stored procedures instead of complex and long queries and call them while processing. Stored procedures are stored as objects in the database and pre-compiled.   

The execution time of the stored procedure is less compared to the query with the same business logic as a query is compiled and executed every time wherever it is called through the application. Also, the stored procedure has an advantage in data transfer and network traffic since we are not transferring the complex query for execution every time to the database server.

## Using `PreparedStatement` instead of `Statement`
While executing the SQL query through the application we use JDBC API and classes for the same. `PreparedStatement` has an advantage over `Statement` for parameterized query execution since the preparedstatement object is compiled once and executed multiple times. Statement object on other hand is compiled and executed every time it is called. Also, the prepared statement object is safe to avoid SQL injection attacks for Web Application security.

## Select Required Columns in a Query
While getting the data from the database we use select queries to get the data. Avoid selecting columns that are not necessary for further processing. Select only those columns which we will be required for further processing or display on the front end. Selecting too many columns causes a delay in query execution at the database end. Also, it increases network traffic from database to application which should be avoided.   

The sample is provided below as an illustration which is to be avoided as follows:
```java
select * from users where user_id = 100;
```

instead, do this:

```java
select user_name, user_age, user_gender, user_occupation, user_address from users where user_id = 100;
```

## Fetch Data Using Joins
While getting the data from multiple tables it is necessary to use the joins properly on tables. If the joins are not properly used or the tables are not normalized it will cause a delay in query execution leading to a performance hit for the application. Avoid using subqueries instead of joins as subqueries take more time for execution than joins.   

Create an index on columns of the table which are frequently used for improving the performance of query execution and reducing the latency of the application.

## Use of Unnecessary Log Statements and Incorrect Log Levels

Logging is an integral part of any application and needs to be implemented efficiently in order to avoid performance hits due to incorrect logging and log levels. We should avoid logging big objects into code. Logging should be limited to specific parameters we need to monitor and not the whole object.   

Also, the logging level should be kept to higher levels like DEBUG, ERROR, and not INFO. The sample is provided below as an illustration which is to be avoided as follows:

```java
Logger.debug("User info : " + user.toString());
Logger.info("Method called for setting user data:" + user.getData());
```

instead, do this:

```java 
Logger.debug(“User info : ” + user.getName() + ” : login ID : ” + user.getLoginId());
Logger.info(“Method called for setting user data”);
```

