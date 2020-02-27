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

