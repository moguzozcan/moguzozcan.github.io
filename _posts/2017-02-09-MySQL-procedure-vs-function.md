---
title: "MySQL Procedure vs. Function"
date: 2017-02-09
categories: 
  - Jekyll
---

One of the most mixed topics in sql word is the difference between procedure (also called stored procedures, because they are stored
in the db :) ) and function. In this post I will try to examine them.
So, let's start with what is procedure and function?

First of all, a stored routine is either a procedure or a function.

Procedures:
Procedures are a declarative sql routines, stored in database catalog not in schema?  


Functions:
Functions are also some sql routines, 
Rather than procedures, functions have to return a value with "RETURN" statement. 

Differences between procedures and functions:
| Procedures                                  | Functions                                         | 
|---------------------------------------------|---------------------------------------------------|
| Can return 0, 1 or many (up to 1024)        | Can only return 1 value                           | 
| Generally used for business logic execution | Generally used for calculations                   | 
| Always return zero by default               | Can return, value, table or table values          | 
| Cannot be called from sql statement         | Can be called and used directly by an sql query   | 
| Has pre-compiled execution plan             | Does not have any execution plan                  | 
| Can be invoked with a CALL statement        | -                                                 | 
| Values are return with output variables     | -                                                 | 

--Stored procedure has the security and reduces the network traffic and also we can call stored procedure in any no. 
of applications at a time.

Next question is difference between function and stored function ?
