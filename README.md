# Wrapper Classes

## Learning Goals

- Introduce Wrapper Classes
- Define autoboxing and unboxing 

## Introduction

For every primitive type in Java, there is a built-in reference type
called a wrapper class. 

Why do we need wrapper classes?  Sometimes a method
requires a reference to an object rather than a primitive value.  We can wrap a primitive
value by creating  a wrapper class instance and provide the reference to the wrapper object.
We also use wrapper objects when working with generic classes, which is something we will
explore when we get to the Java Collections Framework.

## Java Wrapper Classes

Let's go back to the difference between primitive types and reference types
again. Reference variables refer to an object in Java. But wouldn't it be nice
if we could treat our primitive variables the same way? As an object instead?
In Java, there exist a couple of wrapper classes to do just that! A **wrapper**
**class** is a class whose object contains primitive data types so that we can
use them as objects.

Consider the following table of primitive data types and
the equivalent wrapper class:

| Primitive Data Type | Wrapper Class |
|---------------------|---------------|
| `boolean`           | `Boolean`     |
| `byte`              | `Byte`        |
| `char`              | `Character`   |
| `int`               | `Integer`     |
| `long`              | `Long`        |
| `float`             | `Float`       |
| `double`            | `Double`      |

We can initialize a wrapper object in a similar way that we would initialize a
primitive data type, by assigning it to a primitive value as shown
below. After assigning the variable to a value,
we can call methods such as `toString()` using the object reference.
We would not be able to do this if the variable
was declared using a primitive data type.

```java
public class WrapperExample1 {
    public static void main(String[] args){
        Integer i = 2;
        Double d = 3.5;
        Boolean b = true;
        System.out.println(i.toString());
        System.out.println(d.toString());
        System.out.println(b.toString());
    }
}
```

The code prints:

```text
2
3.5
true
```

Wrapper classes also have some special values like the minimum and maximum values for the type.
We  can use `Integer.MIN_VALUE` or `Integer.MAX_VALUE` to initialize a variable
to the smallest or largest possible value.

```java
public class WrapperExample2  {
   public static void main(String[] args) {
     System.out.println(Integer.MIN_VALUE);
     System.out.println(Integer.MAX_VALUE);
   }
}
```

The code prints:

```text
-2147483648
2147483647
```

## Autoboxing and Unboxing

Now what if we have a primitive data type, but we want to use it like an object?
Can we cast it to its corresponding wrapper class? The answer is yes - but this
is a special kind of cast. **Autoboxing** is the automatic conversion between a
primitive and its wrapper class. Let's look at an example!

```java
int a = 8;
double x = 18.50;

// Autoboxing
Integer b = a;
Double y = new Double(x);

System.out.println(a);
System.out.println(b);
System.out.println(x);
System.out.println(y);
```

The code prints:

```text
8
8
18.50
18.50
```

Notice how we can either convert the primitive to its wrapper object by directly
assigning the primitive to the wrapper object, or using the syntax
`Object object = new Object()` and feeding the wrapper class the primitive value
as a parameter.

**Unboxing** is the opposite of autoboxing in that it converts an object of its
wrapper class to its matching primitive. This is also an automatic conversion
just like autoboxing!


```java
Integer b = 8;
Double y = 18.50;

// Unboxing
int a = b;
double x = y;

System.out.println(a);
System.out.println(b);
System.out.println(x);
System.out.println(y);
```

We see the same output:

```text
8
8
18.50
18.50
```

## Conclusion

The Java compiler applies **autoboxing** when a primitive value is:

- Assigned to a variable declared with a wrapper class.
- Passed as an argument in a method call to a parameter declared with a wrapper class.
- Returned from a method with a wrapper class return type.

The Java compiler applies **unboxing** when a wrapper class object is:

- Assigned to a variable declared with a primitive type.
- Passed as an argument in a method call to a parameter declared with a primitive type.
- Returned from a method with a primitive return type.