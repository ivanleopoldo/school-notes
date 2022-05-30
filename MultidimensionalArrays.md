# **Two-dimensional Arrays**

It is an array of one-dimensional arrays.

To declare a two-dimensional array:

```python
type arrayName [x] [y]

int arr[3][4]
```

Where type can be any valid C data type and arrayName be a valid variable name. It can be considered as a table where **_x_** as the number of rows and **_y_** as the number of columns. A two-dimensional array **a**, which has x = 3, y = 4 can be shown as:

<img src="https://www.tutorialspoint.com/cprogramming/images/two_dimensional_arrays.jpg" alt="photo">

Thus every element in array **a** is identified by an element name of the form **a[ i ][ j ]**, where **a** is the name of the array, and **i** and **j** are the subscripts that uniquely identify each element in array **a**.

<hr>

## Initializing Two-Dimensional Arrays

These types of arrays may be initialized by specifying bracketed values for each row.

```c
int a[3][3] = {
    {1,2,3},
    {4,5,6},
    {7,8,9}
};
```

The nested braces are optional:

```c
int a[3][3]= {1,2,3,4,5,6,7,8,9};
```

<hr>

## Accessing Two-Dimensional Array Elements

An element in a two-dimensional array is accessed by using the row index and column index:

```c
int arr[3][3] = {
    {1,2,3},
    {4,5,6},
    {7,8,9}
};
int val = arr[0][1];

printf("%d", val); // 2
```

We can also use nested loops to print all the elements in a two-dimensional array:

```c

int row_size = 3;
int column_size = 3;
int arr[row_size][column_size] = {
    {1,2,3},
    {4,5,6},
    {7,8,9}
};

int i, j;
for ( i = 0; i < row_size; i++ ) {
    for ( j = 0; j < column_size; j++ ) {
        printf("a[%d][%d] = %d\n", i,j, a[i][j] );
    }
}
   
```

<hr>

## Passing Two-Dimensional Arrays to Functions

You can pass Two-Dimensional Arrays to a function like a One-Dimensional Array but you have to declare the function like this:

```c
void func(int arr[2][3]){
    // do this    
}
```

The size of the row is optional:

```c
void func(int arr[][3]){
    // do this
}
```

It is invalid to declare the parameter like this:

```c
void func(int arr[][]){
    // do this
}
```

Another way to declare a function would be:

```c
void func(int (*arr)[]){
    // do this
}
```

<hr>

## Returning a Two-Dimensional Array

This can be done by creating a two-dimensional array inside the function using malloc and returning that array:

```c
int **func(int arr[][3]){
    int i;
    int **new_arr;
    int row_size = 3;
    int column_size = 3;

    new_arr = malloc(sizeof(int*) * row_size);

    for(i=0; i < row_size; i++){
        new_arr[i] = malloc(sizeof(int *) * column_size);
    }

    return new_arr;
}
```

<hr>

## Matrix Arithmetic

Performing arithmetic on two different arrays:

```c
int i, j;
int row_size, column_size;

row_size = 2;
column_size = 2;

int first[row_size][column_size] = {
    {1, 2},
    {3, 4}
};

int second[row_size][column_size] = {
    {5, 6},
    {7, 8}
};

int results[row_size][column_size];
 
for (i = 0; i < row_size; i++) {
    for (j = 0 ; j < column_size; j++) {
        results[i][j] = first[i][j] + second[i][j]; // change arithmetic symbol
        printf("%d\t", results[i][j]);
    }
    printf("\n");
}

```


### Sources

- [Multi-dimensional Arrays in C](https://www.tutorialspoint.com/cprogramming/c_multi_dimensional_arrays.htm)
- [Two-Dimensional Array in C](https://overiq.com/c-programming-101/two-dimensional-array-in-c/)
- [Passing 2-D Array to a Function in C](https://overiq.com/c-programming-101/passing-2-d-array-to-a-function-in-c/)
- [Returning Two Dimensional Array from a Function in C
](https://followtutorials.com/2011/08/returning-two-dimensional-array-from-a-function-in-c.html)
- [Matrix addition in C
](https://www.programmingsimplified.com/c-program-add-matrices)
