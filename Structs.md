# **Structures in C**

A structure in C is a user defined data type that allows you to create an object.

<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/Structure-In-C.png">

---

## **Usage**

### **Creation**

"struct" is used to create a structure in C and are usually defined before the main function;

```c
struct person
{
    char fname[50];
    char lname[50];
    int age;
};
```

### **Declaration**

There are multiple ways to declare a struct variable.

A variable declaration with structure declaration:

```c
struct person
{
    char fname[50];
    char lname[50];
    int age;
} p1; // p1 is declared as struct person.
```

A variable declaration like normal data types:

```c
struct person
{
    char fname[50];
    char lname[50];
    int age;
};

int main()
{
    struct person p1; // p1 is declared as struct person.

    return 0;
}
```

### **Initialization**

Members of a structure cannot be initialized with a value inside of the structure.

To initialize a value:

```c
struct person
{
    char fname[50];
    char lname[50];
    int age;
};

int main()
{
    struct person p1;

    p1.fname = "first name";
    p1.lname = "last name";
    p1.age = 28;

    return 0;
};
```

The "." is used to access members of the structure.

Another way to initialize is to use curly braces:

```c
struct person
{
    char fname[50];
    char lname[50];
    int age;
};

int main()
{
    struct person p1 = {"first name", "last name", 15}; // It has to be the order as the structure member order.

    return 0;
};
```

Another way to initialize is to use designated initialization:

```c
struct person
{
    char fname[50];
    char lname[50];
    int age;
};

int main()
{
    struct person p1 = {.fname = "first name", .lname = "last name", .age = 16}; // The dot is necessary.

    return 0;
};
```

---

## **Advanced Topics**

### **Size**

The size of a structure is the sum of all the bytes of its members.

```c
// this is 0 bytes
struct person{}

// this is 1 byte
struct person
{
    char fname;
}

// this is 50 bytes
struct person
{
    char fname[50];
}

// this is 4 bytes
struct person
{
    int age;
}
```

There is one different thing that messes up the size.

```c
struct person {
    char fname;
    int age;
} // Expected size is 5 bytes but compiler shows 8 bytes.
```

The reason why the compiler shows 8 bytes is because of "structure padding". Bytes are inserted in order to align the data in memory.

### **Aliasing**

A structure can be aliased using "typedef".

```c
// "person" here is optional
typedef struct person 
{
    char fname[50];
    char lname[50];
    int age;
} Person; // "Person" is now the alias of "struct person"
```

To declare an aliased struct:

```c
typedef struct person 
{
    char fname[50];
    char lname[50];
    int age;
} Person;

int main()
{
    Person p1; // Declaration using aliased name.

    return 0;
}
```

### **Structures within structures**

A struct data type can be placed within a struct as a member.

```c
typedef struct
{
    int day;
    int month;
    int year;
} Birthdate;

struct student
{
    char fname[50];
    char lname[50];
    char abbreviatedCourse[5];
    Birthdate birthdate;
}
```

### **Array of Structures**

Declaration of an array of structures is the same as normal declaration of array.

```c
typedef struct
{
    char fname[50];
    char lname[50];
    int age;
} Person;

int main()
{
    Person p1[4]; // Declared an array of Person struct.

    return 0;
}
```

To initialize and access variables. We can just use ".".

```c
typedef struct
{
    char fname[50];
    char lname[50];
    int age;
} Person;

int main()
{
    Person p1[4]; // Declared an array of Person struct.

    p1[0] = {"first name", "last name", 18};

    p1[1].fname = "first name";
    p1[1].lname = "last name";
    p1[1].age = 45;

    return 0;
}
```

### **Structure Pointer**

We can have a pointer to a structure. Instead of using "." to access, we use "->".

```c
typedef struct
{
    int x, y;
} Point, *PPoint; // Declaring a pointer alias

int main()
{
    Point p1 = {4, 5};
    PPoint p2 = &p1; //Pointer to p1.

    printf("%d", p2->x); //prints 4
    printf("%d", p2->y); //prints 5

    return 0;
}
```

---

## **Sources**

1. [Structures in C](https://www.geeksforgeeks.org/structures-c/)
2. [Structure Padding](https://www.includehelp.com/c/size-of-struct-in-c-padding-alignment-in-struct.aspx)