# CProgramming-Notes
Personal reading notes for C Programming Language


# Chapter 5 -Pointers and Arrays
Def: A pointer is a variable that contains the address of a variable.

##5.1 Pointers and Addresses
1. Notation: p = &c; p points to c.
2. * is the indirection or dereferencing operator. When applied to pointer, it accesses the object the pointer points to.
```
int x = 1, y = 2, z[10];
int *ip; //ip is a pointer to int
ip = &x; //ip now points to x
y = *ip; //y is now 1, because * accesses the object the pointer points to
*ip = 0; //x is now 0
ip = &z[0]; //ip now points to z[0]
```
3. other examples: double *dp(dp is a pointer to double, *dp have values of type double), atof(char *)(atof is a pointer to char)
4. pointers are variables, so they can be used without dereferencing.
```
iq = ip //iq now points to whatever ip points to
```

##5.2 Pointers and Function Arguments
Background: Pass by reference and pass by value. (C passes arguments to functions by value)
* Scenario: want to share a web page with you.
* Pass by reference: give you the URL. If page is changed, we both see the change. If you delete the URL, you're just destroying the reference to the page, not the page itself.
* Pass by value: print out the page and give you the copy. This copy is disconnected from the original, thus would not be able to see any updates nor would any change on the copy affect the original webpage. If destroy, you're just destroying the copy, but the original would stay intact.

Swap example: this function below only swaps copies of a and b.
``` 
void swap(int x, int y)
{
  int temp;
  temp = x; 
  x = y;
  y = temp;
}

//correct one below
void swap(int *px, int*py)
{
  int temp;
  temp = *px; //temp is the value of whatever px points to, i.e. x
  *px = *py; x = y;
  *py = temp; //value of whatever py points to is now temp
}
```

## 5.3 Pointers and Arrays
```
int a[10]; //define an array of size 10
int *pa; //pa is a pointer to an integer
pa = &a[0]  <--> pa = a; //pa points to element 0 of a
x = *pa //copy the contents of a[0] to x
*(pa+1) //content of a[1]
```

Note that char s[] and char *s are equivalent. 

## 5.4 Address Arithmetic
1. Pointers and integers are only interchangeable at zero.
2. adding p+n: address of the nth object beyond the one p currently points to.
3. subtract q-p+1: number of elements from p to q inclusive(p and q point to elements of same array, p<q)
4. Pointer arithmetic is consistent. If p were a pointer to float, p++ would advance to next float.

Summary:
* Legal: adding/subtracting a pointer and an integer, subtracting or comparing two points to members of same array, assigning and comparing to zero.
* All others are illegal(e.g. add/multiply/divide pointers, add float/double to them, assign a pointer of one type to a pointer of another type without cast except for void *)
* 
## 5.5 Character Pointers and Functions
1. String constant is an array of characters. Length is one more than the number of characters because of the null character '\0' signifying the end.
2. Access character string through a character pointer.

```
char amessage[] = "hello" //an array
char *pmessage = "hello" //a pointer
```

## 5.6 Pointer Arrays; Pointers to Pointers

## 5.7 Multi-dimensional Arrays

## 5.8 Initialization of Pointer Arrays

## 5.9 Pointers vs Multi-dimensional Arrays
```
int a[10][20] //multi-dimensional array
int *b[10] //allocats 10 pointers and does not initialize them, each pointer can point to array of different size
```

## 5.11 Pointers to Functions

## 5.12 Complicated Declarations
```
int *f() //function returning pointer to int
int (*pf)() //pointer to function returning int
```

more examples:
```
1. char **argv //pointer to pointer to char
2. int (*daytab)[13] //pointer to array[13] of int
3. int *daytab[13] //array[13] of pointer to int
4. void *comp() //function returning pointer to void
5. void (*comp){} //pointer to function returning void
6. char (*(*x())[])() //function returning pointer to array[] of pointer to function returning char
7. char(*(*x[3])())[5] //array[3] of pointer to function returning pointer to array[5] of char
```


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
