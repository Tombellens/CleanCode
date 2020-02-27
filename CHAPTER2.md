## CHAPTER 2: Meaningful Names

1. Use Intention-Revealing Names
2. Avoid Disinformation
3. Make Meaningful Distinctions
4. Use Pronounceable Names
5. Use Searchable Names
6. Avoid Encodings
7. Avoid Mental Mapping
8. Class Names
9. Method Names
10. Extra

---

### 1. Use Intention-Revealing Names

The name of a variable, function or class should answer all the big questions. It should tell
you why it exists, what is does and how it is used.

If a name requires a comment, then the name does not reveal its intent.

E.G. A board-game where certain cells are flagged
```java
  public List<int[]> getThem(){  
    List<int[]> list1 = new ArrayList<int[]>();
    for (int[] x : theList)
        if (x[0] == 4)
        list1.add(x);
    return list1;
  }
```


This is a bad example. What kind of things are in *theList?* What is the significance of the
value 4? How would I use the list being returned? 
Following example does the same but has better naming: 

```java
  public List<int[]> getFlaggedCells(){  
    List<int[]> flaggedCells = new ArrayList<int[]>();
    for (int[] cell : gameBoard)
        if(x[0] == 4)
        list1.add(x);
    return list1;
  }
```

### 2. Avoid Disinformation

Programmers must avoid leaving false clues that obscure the meaning of code. 

E.G. 

```java
    String[] accountList = new String[];
```

This is bad naming. Do not refer to a grouping of accounts as an *accountList* unless it's actually
a List. Better would be: 

```java
    String[] accounts = new String[];
    String[] accountArray = new String[];
    String[] accountGroup = new String[];                   
```

### 3. Make Meaningful Distinctions

Programmers create problems for themselves when they write code solely to satisfy a compiler 
or interpreter. For example, because you can't use the same name to refer to two different things
in the same scope, you might be tempted to to change one name in an arbitrary way. 

E.G. You need to copy a one char-array into another char-array

```java
    public static void copyChars(char a1[], char a2[]){
        for (int i = 0; i < a1.length; i++){
            a2[i] = a1[i];
}
}
```

These names are not disinformative, they are noninformative, they provide no clue to the author's
intention. Better would be:

```java
    public static void copyChars(char source[], char destination[]){
        for (int i = 0; i < source.length; i++){
            destination[i] = source[i];
}
}
```

### 4. Use Pronounceable Names

If you can't pronounce the name of a variable, you can't discuss it without sounding like an idiot. The variable-name
*genymdhms* is not a good name.

### 5. Use Searchable Names

Single-letter names and numeric constants have a particular problem in that they are not easy
to locate across a body of text. One might easily grep for *MAX_CLASSES_PER_STUDENT* but the number 7 could be 
more troublesome. 

The author's personal preference is that single letter names can ONLY be used as 
local variable inside short methods. 

The length of a name should correspond to the size of its scope. 

### 6. Avoid Encodings

We have enough encodings to deal with, without adding more to our burden. Encoding type or scope
information into names simply adds an extra burden of deciphering. Encoded names are seldom 
pronounceable and are easy to miss-type.

####    6.1 Hungarian Notation
Java Programmers don't need type encoding. Objects are strongly typed and editing environments
have advanced such that they detect a type error long before you can run a compile. So nowadays
Hungarian Notation and other forms of type encoding are simply impediments.

####    6.2 Member_prefixes
You don't need prefix variables with *m_* anymore. Your classes and functions should be small
enough that you don't need them. 

####    6.3 Interfaces and Implementations
When you have an abstract class and an implementation of that class with the same name, the 
author advises to put the prefix before the implementation and not otherwise. 

### 7. Avoid Mental Mapping
Readers shouldn't have to mentally translate your names into other names they already know. This is
a problem with single-letter variable names. Certainly a loop counter may be named *i* or *j* or *k* 
(though never *l* !) **if its scope is very small and no other names can conflict with it .** In most other contexts a
single-letter name is a poor choice: it's just a place holder that the reader must mentally map to the actual concept.

### 8. Class Names
Classes and objects should have noun or noun phrase names  like *Customer*, *WikiPage*, *Account* and *AddressParser*.
Avoid words like *Manager*, *Processor*, *Data* or *Info* in the name of a class. A class name should not be a verb.

### 9. Method Names
Methods should have verbs or verb phrase names like *postPayment*, *deletePage* or *save*. Accessors, mutators and predicates
should be named for their value prefixed with *get*, *set* and *is*. 

```java
String name = employee.getName();
customer.setName("Mike");
if (payCheck.isPosted())...
```
When constructors are overloaded, use static factory methods with names that describe the arguments.

E.G.

```java
Complex fulcrumPoint = new Complex(23.0);
```

This is an overloaded constructor that can take different types of arguments. It's better to make a static 
factory method with a name that describes the argument. 

```java
Complex fulcrumPoint = Complex.FromRealNumber(23.0)
```
Consider enforcing the use of this factory method by making the corresponding constructor private.

### 10. Extra

#### 10.1 Don't Be Cute 
Don't tell little culture-dependent jokes like *eatMyShorts()* to mean *abort()*.

#### 10.2 Pick One Word per Concept
Pick one word for one abstract concept and stick with it. For instance, it's confusing to have *fetch*, *retrieve*,
and *get* as equivalent methods or different classes. Likewise it's confusing to have a *controller*, a *manager*
and a *driver* in the same codebase.

#### 10.3 Pick Different Words for Different Concepts
Variables, methods or classes with the same words should be semantically the same. Don't use *add* for a method
that will do a concatenation and for another method that will put a single parameter into a collection. It would 
be better to use a name like *append* or *insert*.

#### 10.4 Add Meaningful Context
Few names are meaningful in themselves. You need to place names in context by enclosing them in well-named
classes, functions or namespaces. Imagine that you have the variables named *firstName*, *lastName*, *street*, 
*houseNumber*, *city* and *state*. Together it's pretty clear they form an address. But what if you saw
the *state* variable being used alone in a method? 

#### 10.5 Don't Add Gratuitous Context
Don't add information to the variables that are common to most of the variables. In an imaginary application
called "Gas Station Deluxe", it is a very bad idea to prefix every variable with *GSD*. You type G and press
the completion key and are rewarded with a mile-long list of every class in the system. Why make it so hard for the 
IDE to help you?





