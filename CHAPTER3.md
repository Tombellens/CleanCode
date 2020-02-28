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
10. Structured Programming

---

### 1. Small!

Functions should be as short as possible. Functions should not be 100 lines long. Functions should 
hardly ever be 20 lines long. 

#### 1.1 Blocks and Indenting

This implies that blocks within *if*-statements, *else*-statements, *while*-stattements and so on should be
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
  private void includeSetupAndTearDownPages() throws Exception{
        includeSetupPages();
        includePageContent();
        updatePageContent();
  }

  private void includeSetupPages() throws Exception{
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

