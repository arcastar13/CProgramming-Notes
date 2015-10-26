# CProgramming-Notes
Personal reading notes for C Programming Language



# Chapter 6 - Structures

##6.1 Basics of Structures
1. basic idea: organize complicated data, allow a group of related variables to be treated as a unit
2. structures can be nested

```
struct rec {
  struct point p1;
  struct point p2;
};

 struct point {
  int x;
  int y;
};
```


##6.2 Structures and Functions
Only legal operations on a structure are copying it or assigning to it as a unit, taking its address with &, and accessing its members. (p129)

* if a large structure is to be passed to a function, it is generally more efficient to pass a pointer than to copy the whole structure. (related to hw4) 
* struct point *pp: pp is a pointer to a struct of type struct point, *pp is the struct
* if we have struct rect r, *rp = &r; equivalent expressions: r.pt1.x, rp->pt1.x, (r.pt1).x, (rp->pt1).x


##6.3 Arrays of Structures
Parallel arrays suggest an array of structures. Each keyword entry is a pair, and there is an array of pairs.
```
struct key {
  char * word;
  int count;
} keytab[NKEYS];
```

##6.4 Pointers to Structures
** coming back

##6.5 Self-referential structures
