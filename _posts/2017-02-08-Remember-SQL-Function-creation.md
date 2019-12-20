---
title: "Remember SQL Function Creation"
date: 2017-02-08
categories: 
  - SQL Function Creation
---

In this post, I will go over the SQL Function creation process, for this MySQL data types must also be revised. 
The mostly used MySQL data types are:

INT	A standard integer
DECIMAL	A fixed-point number
FLOAT	A single-precision floating point number
DOUBLE	A double-precision floating point number
BIT	A bit field
CHAR	A fixed-length nonbinary (character) string
VARCHAR	A variable-length non-binary string
TEXT	A small non-binary string
DATE	A date value in ‘CCYY-MM-DD’ format
TIME	A time value in ‘hh:mm:ss’ format
DATETIME	A date and time value in ‘CCYY-MM-DD hh:mm:ss’ format
TIMESTAMP	A timestamp value in ‘CCYY-MM-DD hh:mm:ss’ format

The above information is taken from: http://www.mysqltutorial.org/mysql-data-types.aspx

Now, the function creation process...

-Firstly, drop the function if another function with this name already exists.

```mysql
drop function if exists initcap;
```

-Then, create function, define its parameters. The syntax of creating a function is given below. The parameters of an sql 
function can be in three types, IN, OUT, INOUT. Furthermore, if the function you wrote gives the same results for the 
same input, then it should be declare as DETERMINISTIC, if not declare as NOT DETERMINISTIC
```sql
CREATE FUNCTION function_name(param1,param2,…)
    RETURNS datatype
   [NOT] DETERMINISTIC
 statements
```

This is a real example, which takes a string and returns it with only first letter of each word is capitalized. For me,
the logic is simple but syntax of the sql, since I am rarely using sql, kind of hard for me. 
```sql
CREATE FUNCTION initcap (word VARCHAR) RETURNS VARCHAR
        DETERMINISTIC
BEGIN
        DECLARE @ConvertedWord VARCHAR
        DECLARE @Index INT
        
        SET @Index = 2 
        SET @ConvertedWord = UPPER(SUBSTRING(word, 1, 1)
        WHILE(@Index < LEN(word + 1)
                BEGIN
                        IF((SUBSTRING(word, @Index-1, 1) =' ' AND @Index+1 <> LEN(@word))
                                BEGIN
                                        SET @ConvertedWord = UPPER(SUBSTRING(word, @Index, 1)
                                        SET @Index = @Index + 1 
                        END
                        ELSE
                                BEGIN
                                        SET @ConvertedWord = @ConvertedWord + LOWER(SUBSTRING(word, @Index, 1))
                                        SET @Index = @Index + 1
                        END
        END               
        RETURN @ConvertedWord
END
```
