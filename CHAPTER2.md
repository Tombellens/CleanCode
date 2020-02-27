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


This is a bad example. What kind of things are in theList? What is the significance of the
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

This is bad naming. Do not refer to a grouping of accounts as an accountList unless it's actually
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