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

```java
  public List<int[]> getThem(){  
    List<int[]> list1 = new ArrayList<int[]>();
    for (int[] x : theList)
        list1.add(x);
    return list1;
  }
```

