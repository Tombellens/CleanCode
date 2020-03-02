## CHAPTER 3: Functions

1. Small!
2. Do One Thing
3. One Level of Abstraction per Function
4. Use Descriptive Names
5. Function Arguments
6. Side Effects
7. Command Query Separation
8. Exceptions vs. Error Codes
9. Duplication

---

### 1. Small!

Functions should be as short as possible. Functions should not be 100 lines long. Functions should 
hardly ever be 20 lines long. 

#### 1.1 Blocks and Indenting

This implies that blocks within *if*-statements, *else*-statements, *while*-statements and so on should be
one line long. Probably that line should be a function call. Not only does this keep the enclosing function 
small, but it also adds documentary value because the function called within the block can have a nicely descriptive
name.

### 2. Do One Thing

Functions should do one thing. They should do it well. They should do it only.

### 3. One Level of Abstraction per Function

In order to make sure our functions are doing "one thing", we need to make sure that the statements within our
function are all at the same level of abstraction.

#### 3.1 The Stepdown Rule

The code should read like a top-down narrative. We want every function to be followed by those at the next level
of abstraction so that we can read the program, descending one level of abstraction at a time as we read down
the list of functions.

```java
  private void includeSetupAndTearDownPages(){
        includeSetupPages();
        includePageContent();
        updatePageContent();
}

  private void includeSetupPages(){
        includeSuiteSetupPage();
        includeSetupPage();
}

  private void includeSuiteSetupPage(){
        //Code for the includeSuiteSetup
}

 private void includeSetupPage(){
        //Code for the includeSetup
}

 private void includePageContent(){
        //Code for the includePageContent();
}

 private void updatePageContent(){
        //Code for the updatePageContent();
}
```

#### 3.2 Switch Statements
It 's hard to make a small *switch* statement. It's also hard to make a *switch* statement
that does one thing. Unfortunately we can't always avoid *switch* statements, but we can make
sure that each *switch* statement is buried in a low-level class and is never repeated. 

The author's general rule for *switch* statements is that they can be tolerated if they appear 
only once, are used to create polymorphic objects, and are hidden behind an inheritance relationship so that the rest of the 
system can't see them. 



### 4. Use Descriptive Names
The smaller and more focussed a function is, the easier it is to choose a descriptive
name. Don't be afraid to make a name long. A long descriptive name is better than a
long descriptive comment.

### 5. Function Arguments
The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed
by two (dyadic). Three arguments (triadic) should be avoided where possible. More than three
(polyadic) requires very special justification- and then shouldn't be used anyway.

Arguments are hard because they take a lot of conceptual power and aren't easy to test.

#### 5.1 Common Monadic Forms
There are two very common reasons to pass a single argument into a function. You may be
asking a question about that argument, as in *boolean fileExists("MyFile")*. Or
you may be operating on that argument, transforming it into something else and
returning it. For example, *InputStream fileOpen ("MyFile")* transforms a file name
*String* into an *InputStream* return value.

Try to avoid any monadic functions that don't follow these forms.Using an output argument 
instead of a return value for a transformation is confusing. If a function is going to
transform its input argument, the transformation should appear as the return value.

#### 5.2 Flag Arguments
Passing a boolean into a function is a truly terrible practice. It immediately complicates
the signature of the method, loudly proclaiming that this function does more than one thing.
It does one thing if the flag is true and another if the flag is false.

#### 5.3 Dyadic Functions
Dyads aren't evil and you will certainly have to write them. However, you should be aware
that they come at a cost and should take advantage of what mechanisms may available to you
to convert them into monads.


E.G. This is a perfectly reasonable example
```java
 Point p = new Point(0,0);
```

This, on the other hand, is rather confusing

```java
 writeField(output-Stream, name);
```
The reading requires a short pause until we learn to ignore the first parameter.
The parts we ignore are where the bugs will hide. Better would be:

```java
 writeField(name);
```
#### 5.4 Triads
Functions that take three arguments are significantly harder to understand than dyads.
The issues of ordering, pausing and ignoring are more than doubled. The author suggests
to think very carefully before creating a triad.

#### 5.5 Argument Objects
When a function seems to need more than two or three arguments, it is likely that some of
those arguments ought to be wrapped into a class of their own. Consider the difference
between the two following declarations

```java
    Circle makeCircle(double x, double y, double radius);
    Circle makeCircle(Point center, double radius);
```

### 6. (Have No) Side Effects

A side effect is when your function ('s name) promises to do one thing but it also does other 
(hidden) things. E.G. When your function makes unexpected changes to the variables of 
its own class. Functions with side effects can have dangerous implications for your program.

#### 6.1 Output Arguments

In general output arguments should be avoided. If your function must change the state of 
something, have it change the state of its owning object.

### 7. Command Query Separation

Functions should either do something or answer something, but not both. Either your 
function should change the state of an object, or it should return some information
about that object.

### 8. Prefer Exceptions to Returning Error Codes

Error codes need to be handled immediately and are a subtle violation of command query
separation. If you use exceptions instead of returned error codes, then the error processing
code can be separated from the happy path code and can be simplified.

#### 8.1 Extract Try/Catch Blocks

*Try/catch* blocks are ugly in their own right. They confuse the structure of the code 
and mix error processing with normal processing. It is better to extract the bodies of 
the *try* and *catch* blocks out into functions of their own.

### 9. Don't repeat yourself

Duplication is a problem because it bloats the code and will require four-fold modification
should the algorithm ever have to change. It is also a four-fold opportunity for an 
error of omission. 

