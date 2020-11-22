+++
memflask = True
isdraft = False
+++

# C programming: Quizz 01 

## Question 1: Suppose that in a C program snippet, followings statements are used.


```c
i) sizeof(int);
ii) sizeof(int*);
iii) sizeof(int**);
```


Assuming size of pointer is 4 bytes and size of int is also 4 bytes, pick the most correct answer from the given options.


[ ] Only i) would compile successfully and it would return size as 4

[x] i), ii) and iii) would compile successfully and size of each would be same i.e. 4 

[ | i), ii) and iii) would compile successfully but the size of each would be different and would be decided at run time. 

[ ] ii) and iii) would result in compile error but i) would compile and result in size as 4. 

----
Explanation:

Size of all pointer types is same. And whether it is a 'pointer to char' or 'pointer to int' or 'pointer to pointer to int', the size always remain same. That's why all i), ii) and iii) would compile successfully and would result in same size value of 4.

Assume *int* is 4 bytes, *char* is 1 byte and *float* is 4 bytes. Also, assume that pointer size is 4 bytes (i.e. typical case)

## What’s the size returned for each of sizeof() operator?

```C
char *pChar;
int *pInt;
float *pFloat;
 
sizeof(pChar);
sizeof(pInt);
sizeof(pFloat);
```

[x] 4 4 4 

[ ] 1 4 4 

[ ] 1 4 8 

[ ] None of the above 

----

Question 2 Explanation: 

Irrespective of the type of pointer, the size for a pointer is always same. So whether it’s pointer to char or pointer to float, the size of any pointer would be same. Even size of a pointer to user defined data type (e.g. struct) is also would be same.

```C
#include "stdlib.h"
int main()
{
 int *pInt;
 int **ppInt1;
 int **ppInt2;
 
 pInt = (int*)malloc(sizeof(int));
 ppInt1 = (int**)malloc(10*sizeof(int*));
 ppInt2 = (int**)malloc(10*sizeof(int*));
 
 free(pInt);
 free(ppInt1);
 free(*ppInt2);
 return 0;
}
```

Choose the correct statement w.r.t. above C program.

[ ] malloc() for ppInt1 and ppInt2 isn’t correct. It’ll give compile time error. 

[ ] free(*ppInt2) is not correct. It’ll give compile time error. 

[ ] free(*ppInt2) is not correct. It’ll give run time error. 

[X] No issue with any of the malloc() and free() i.e. no compile/run time error. 

----

Explanation:

ppInt2 is pointer to pointer to int. *ppInt2 is pointer to int. So long as the argument of free() is pointer, there's no issue. That's why B) and C) both are not correct. Allocation of both ppInt1 and ppInt2 is fine as per their data type. So A) is also not correct. The correct statement is D).
