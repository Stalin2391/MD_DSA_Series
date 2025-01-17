# Agenda :

### Intro to OOP
### Class
### Object


## Introduction to Object-Oriented Programming (OOP):

- OOPS (Object-Oriented Programming System) is a programming paradigm that is based on the concept of "objects." 
- These objects represent real-world entities and interact with one another to perform tasks.
- OOPS is designed to make software more modular, reusable, and easier to maintain by organizing code into objects that encapsulate both data (attributes) and behavior (methods).


## Object

An **object** is an instance of a class. It contains both data (attributes) and methods (functions or operations) that operate on the data.

**Example:**
A "Car" object might have attributes like `color`, `model`, and `year`, and methods like `start()` and `stop()`.

## Class

A **class** is a blueprint or template for creating objects. It defines the structure and behavior of objects.

**Example:**
A "Car" class might define the properties and methods that all car objects will have.

### Example :

```java

class Person {
    String name;
    int age;

    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter and Setter methods for encapsulation
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    // Display information about the person
    public void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Person p = new Person("John", 30);
        p.display();
        
        // Using setter to modify data
        p.setAge(31);
        p.display();
    }
}


```