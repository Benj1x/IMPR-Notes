# IMPR-Notes
Notes for IMPR exam - mostly the stuff I'm a bit unsure off

## IMPR notes

- 1 Hjælpemidler: Contents
   - 1.1 Tilladte hjælpemidler:
   - 1.2 Ikke tilladte hjælpemidler:
- 2 Honorable mentions:
   - 2.1 Læs spørgsmålet flere gange, og forstå:
- 3 Pointers
   - 3.1 Declaring a pointer:
   - 3.2 Assigning addresses to Pointers
   - 3.3 Changing Value Pointed by Pointers
   - 3.4 Printing a variable and it’s memory address:
- 4 Arrays & pointers:
   - 4.1 Print addresses of array elements:
- 5 Memory Allocation
   - 5.1 malloc
   - 5.2 calloc
   - 5.3 realloc
- 6 Structs:
   - 6.1 Pointers to structs:
   - 6.2 Dynamically allocating structs:
- 7 Files
   - 7.1 Read & Write modes


## 1 Hjælpemidler: Contents

### 1.1 Tilladte hjælpemidler:

- At konsultere egen kode produceret på github.com.
- At konsultere kursets slides og kodestumper på Moodle og github.com.
- At medbringe og bruge kursets bog.

### 1.2 Ikke tilladte hjælpemidler:

- Video eller lydmateriale.
- Brug af kompilere, linter, syntakschecker eller andre værktøjer til
    at assistere med at skrive kode, det inkludere blandt andet Visual
    studio, CLion, emacs, gcc, clang og lignende af online værktøjer.
- Interaktive hjælpemidler.
- Kommunikation med andre.
- Brug af online ressourcer der IKKE er af egen produktion.


## 2 Honorable mentions:

### 2.1 Læs spørgsmålet flere gange, og forstå:

Læs opgaverne godt igennem, og forstå - eksamenssættet er eksplicit i
hvad der står eksempel, fra Mini-eksamenssæt:

Vi bliver bedt tidlele variablen ’a’ typen double med en værdi af 3,14.
Fejlen her, er at der blev antaget at vi også skulle vise det for en pointer.
Men som vi kan se i "printf()" så er a, **ikke** en pointer, og vi kan derfor
antage, at vi **kun** skal vise det for "int a ="


## 3 Pointers

### 3.1 Declaring a pointer:
```
1 int* x;
2 //Here, we have declared a pointer x of int type.
3
4 //You can also declare pointers in these ways.
5
6 int *x1;
7 int* x2 ;
8 //Let’s take anoth e r example o f d e c l a r i n g p o i n t e r s.
9
10 i n t* x1 , x2 ;
11 //Here , we have d e c l a r e d a p o i n t e r p1 and a normal v a r i a b l e p.
```
### 3.2 Assigning addresses to Pointers

```
1 i n t* pc , c ;
2 c = 5 ;
3 pc = &c ;
4 //Here , 5 i s a s s i g n e d t o t h e c v a r i a b l e. And , t h e a d d r e s s o f c i s
a s s i g n e d t o t h e pc p o i n t e r.
```
### 3.3 Changing Value Pointed by Pointers

```
1 i n t* pc , c ;
2 c = 5 ;
3 pc = &c ;
4 c = 1 ;
5 p r i n t f ( "%d " , c ) ; // Output : 1
6 p r i n t f ( "%d " , *pc ) ; // Ouptut : 1
7 //We have a s s i g n e d t h e a d d r e s s o f c t o t h e pc p o i n t e r.
8
9 //Then , we changed t h e v a l u e o f c t o 1. S i n c e pc and t h e a d d r e s s
o f c i s t h e same , *pc g i v e s us 1.
```

### 3.4 Printing a variable and it’s memory address:

1 # i n c l u d e < s t d i o. h>
2 i n t main ( )
3 {
4 i n t v a r = 5 ;
5 p r i n t f ( " v a r : %d\n " , v a r ) ;
6
7 // N o t i c e t h e use o f & b e f o r e v a r
8 p r i n t f ( " a d d r e s s o f v a r : %p " , &v a r ) ;
9 r e t u r n 0 ;
10 }

```
Output:
var: 5
address of var: 2686778
```
## 4 Arrays & pointers:

### 4.1 Print addresses of array elements:

1 # i n c l u d e < s t d i o. h>
2 i n t main ( ) {
3 i n t x [ 4 ] ;
4 i n t i ;
5
6 f o r ( i = 0 ; i < 4 ; ++ i ) {
7 p r i n t f ( "&x[%d ] = %p\n " , i , &x [ i ] ) ;
8 }
9
10 p r i n t f ( " Address o f a r r a y x : %p " , x ) ;
11
12 r e t u r n 0 ;
13 }

```
Outputs: &x[0] = 1450734448
&x[1] = 1450734452
&x[2] = 1450734456
&x[3] = 1450734460
Address of array x: 1450734448
```

```
There is a difference of 4 bytes between two array elements. It is be-
cause the size of int is 4 bytes. The address of &x[0] and x is the same. It’s
because the variable name x points to the first element of the array.
```
1 //Here , we have d e c l a r e d an a r r a y x o f 6 e l e m e n t s. To a c c e s s
e l e m e n t s o f t h e a r r a y , we have used p o i n t e r s.
2 # i n c l u d e < s t d i o. h>
3 i n t main ( ) {
4
5 i n t i , x [ 6 ] , sum = 0 ;
6
7 p r i n t f ( " E n t e r 6 numbers : " ) ;
8
9 f o r ( i = 0 ; i < 6 ; ++ i ) {
10 // E q u i v a l e n t t o s c a n f ("%d " , &x [ i ] ) ;
11 s c a n f ( "%d " , x+ i ) ;
12
13 // E q u i v a l e n t t o sum += x [ i ]
14 sum += *( x+ i ) ;
15 }
16
17 p r i n t f ( "Sum = %d " , sum ) ;
18
19 r e t u r n 0 ;
20 }

```
Output: Enter 6 numbers: 2
3
4
4
12
4
Sum = 29
```

1 // I n t h i s example , &x [ 2 ] , t h e a d d r e s s o f t h e t h i r d e l e m e n t , i s
a s s i g n e d t o t h e p t r p o i n t e r. Hence , 3 was d i s p l a y e d when we
p r i n t e d *p t r.
2 // p r i n t i n g *( p t r + 1 ) g i v e s us t h e f o u r t h e l e m e n t. S i m i l a r l y ,
p r i n t i n g *( p t r − 1 ) g i v e s us t h e second e l e m e n t.
3 # i n c l u d e < s t d i o. h>
4 i n t main ( ) {
5
6 i n t x [ 5 ] = { 1 , 2 , 3 , 4 , 5 } ;
7 i n t* p t r ;
8
9 // p t r i s a s s i g n e d t h e a d d r e s s o f t h e t h i r d e l e m e n t
10 p t r = &x [ 2 ] ;
11
12 p r i n t f ( "*p t r = %d \n " , *p t r ) ; // 3
13 p r i n t f ( "*( p t r + 1 ) = %d \n " , *( p t r + 1 ) ) ; // 4
14 p r i n t f ( "*( p t r − 1 ) = %d " , *( p t r − 1 ) ) ; // 2
15
16 r e t u r n 0 ;
17 }

## 5 Memory Allocation

### 5.1 malloc

```
The name "malloc" stands for memory allocation.
The malloc() function reserves a block of memory of the specified num-
ber of bytes. And, it returns a pointer of void which can be casted into
pointers of any form.
1 // T h i s a l l o c a t e s 4 0 0 b y t e s o f memory. B e c a u s e t h e s i z e o f a f l o a t
i s 4 b y t e s. And , t h e p o i n t e r p t r h o l d s t h e a d d r e s s o f t h e
f i r s t b y t e i n t h e a l l o c a t e d memory.
2
3 p t r = ( f l o a t*) m a l l o c ( 1 0 0 * s i z e o f ( f l o a t ) ) ;
4 // R e s u l t s i n a NULL p o i n t e r i f t h e memory c a n n o t be a l l o c a t e d.
```
### 5.2 calloc

```
The name "calloc" stands for contiguous allocation.
```

```
The malloc() function allocates memory and leaves the memory unini-
tialized, whereas the calloc() function allocates memory and initializes all
bits to zero.
1 // a l l o c a t e s c o n t i g u o u s s p a c e i n memory f o r 25 e l e m e n t s o f t y p e
f l o a t.
2 p t r = ( f l o a t*) c a l l o c ( 2 5 , s i z e o f ( f l o a t ) ) ;
```
### 5.3 realloc

```
If the dynamically allocated memory is insufficient or more than required,
you can change the size of previously allocated memory using the realloc()
function.
1 p t r = ( i n t*) m a l l o c ( 1 0 * s i z e o f ( i n t ) ) ;
2
3 p t r = r e a l l o c ( p t r , 20 * s i z e o f ( i n t ) ) ;
4 //Here , p t r i s r e a l l o c a t e d with a new s i z e 2 0.
```
## 6 Structs:

### 6.1 Pointers to structs:

1 # i n c l u d e < s t d i o. h>
2 s t r u c t p e r s o n
3 {
4 i n t age ;
5 f l o a t w e i g h t ;
6 } ;
7
8 i n t main ( )
9 {
10 s t r u c t p e r s o n *p e r s o n P t r , p e r s o n 1 ;
11 p e r s o n P t r = &p e r s o n 1 ;
12
13 p r i n t f ( " E n t e r age : " ) ;
14 s c a n f ( "%d " , &p e r s o n P t r −>age ) ;
15
16 p r i n t f ( " E n t e r w e i g h t : " ) ;
17 s c a n f ( "%f " , &p e r s o n P t r −>w e i g h t ) ;
18


19 p r i n t f ( " D i s p l a y i n g : \ n " ) ;
20 p r i n t f ( " Age : %d\n " , p e r s o n P t r −>age ) ;
21 p r i n t f ( " w e i g h t : %f " , p e r s o n P t r −>w e i g h t ) ;
22
23 r e t u r n 0 ;
24 }

```
The address of person1 is stored in the personPtr pointer using personPtr
= &person1;.
Now, you can access the members of person1 using the personPtr
pointer.
personPtr->age is equivalent to *personPtr.age personPtr->weight is
equivalent to *personPtr.weight
```
### 6.2 Dynamically allocating structs:

1 # i n c l u d e < s t d i o. h>
2 # i n c l u d e < s t d l i b. h>
3 s t r u c t p e r s o n {
4 i n t age ;
5 f l o a t w e i g h t ;
6 c h a r name [ 3 0 ] ;
7 } ;
8
9 i n t main ( )
10 {
11 s t r u c t p e r s o n *p t r ;
12 // a l l o c a t i n g memory f o r 50 numbers o f s t r u c t p e r s o n
13 p t r = ( s t r u c t p e r s o n*) m a l l o c ( 5 0 * s i z e o f ( s t r u c t p e r s o n ) ) ;
14 }

```
This allocates 50 slots for the variable ptr
```
## 7 Files

### 7.1 Read & Write modes


Mode Meaning of mode During Inexistence of file

r Open for reading

```
If the file does not exist, fopen() returns
NULL.
```
rb Open for reading
in binary mode.

```
If the file does not exist, fopen() returns
NULL
```
w Open for writing.

```
If the file exists, its contents are overwritten.
If the file does not exist, it will be created.
```
wb

```
Open for writing
in binary mode.
```
```
If the file exists, its contents are overwritten.
If the file does not exist, it will be created.
```
a

```
Open for append.
Data is added to
the end of the file.
```
```
If the file does not exist, it will be created.
```
ab

```
Open for append
in binary mode.
Data is added to
the end of the file.
```
```
If the file does not exist, it will be created.
```
r+

```
Open for both
reading and writ-
ing.
```
```
If the file does not exist, fopen() returns
NULL.
```
rb+

```
Open for both
reading and writ-
ing in binary
mode.
```
```
If the file does not exist, fopen() returns
NULL.
```
w+

```
Open for both
reading and writ-
ing.
```
```
If the file exists, its contents are overwritten.
If the file does not exist, it will be created.
```
wb+

```
Open for both
reading and writ-
ing in binary
mode.
```
```
If the file exists, its contents are overwritten.
If the file does not exist, it will be created.
```
a+

```
Open for both
reading and ap-
pending.
```
```
If the file does not exist, it will be created.
```
ab+

```
Open for both
reading and ap-
pending in binary
mode.
```
```
If the file does not exist, it will be created.
11
```

