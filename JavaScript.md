# Object-Oriented Programming (OOP) in JavaScript/TypeScript

Object-Oriented Programming (OOP) in JavaScript and TypeScript allows developers to organize and structure their code efficiently using classes, objects, and OOP principles. Below are the key OOP concepts explained with examples.

---

## 1. **Classes and Objects**

- A **class** is a blueprint for creating objects.
- An **object** is an instance of a class.

### JavaScript Example:

```javascript
class Person {
    constructor(name, age) { // Constructor
        this.name = name;
        this.age = age;
    }

    greet() { // Instance Method
        return `Hello, my name is ${this.name}.`;
    }
}

const person = new Person("Alice", 30); // Create an object
console.log(person.greet()); // Output: Hello, my name is Alice.
```

### TypeScript Example:

```typescript
class Person {
    name: string;
    age: number;

    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }

    greet(): string {
        return `Hello, my name is ${this.name}.`;
    }
}

const person = new Person("Alice", 30);
console.log(person.greet()); // Output: Hello, my name is Alice.
```

---

## 2. **Instance Methods**

- Operate on instance-specific data.
- Use the `this` keyword to refer to the object.

### Example:

```javascript
class Counter {
    constructor() {
        this.count = 0;
    }

    increment() {
        this.count++;
        return this.count;
    }
}

const counter = new Counter();
console.log(counter.increment()); // Output: 1
console.log(counter.increment()); // Output: 2
```

---

## 3. **Static Methods**

- Defined using the `static` keyword.
- Belong to the class, not an instance.
- Use for utility functions.

### Example:

```javascript
class MathUtils {
    static add(a, b) {
        return a + b;
    }
}

console.log(MathUtils.add(10, 20)); // Output: 30
```

---

## 4. **Class Properties** (TypeScript Example)

- Can declare properties in TypeScript with explicit types.
- Use `readonly` for immutable properties.

### Example:

```typescript
class Employee {
    readonly id: number; // Immutable property
    name: string;

    constructor(id: number, name: string) {
        this.id = id;
        this.name = name;
    }
}

const emp = new Employee(1, "John");
console.log(emp.name); // Output: John
// emp.id = 2; // Error: Cannot assign to 'id' because it is a read-only property.
```

---

## 5. **Inheritance**

- Allows a child class to inherit properties and methods from a parent class.

### JavaScript Example:

```javascript
class Animal {
    speak() {
        return "I am an animal.";
    }
}

class Dog extends Animal {
    speak() {
        return "Woof!";
    }
}

const dog = new Dog();
console.log(dog.speak()); // Output: Woof!
```

### TypeScript Example:

```typescript
class Animal {
    speak(): string {
        return "I am an animal.";
    }
}

class Dog extends Animal {
    speak(): string {
        return "Woof!";
    }
}

const dog = new Dog();
console.log(dog.speak()); // Output: Woof!
```

---

## 6. **Encapsulation**

- Use access modifiers (`public`, `private`, `protected`) in TypeScript.
- Restrict access to class properties and methods.

### Example:

```typescript
class BankAccount {
    private balance: number; // Private property

    constructor() {
        this.balance = 0;
    }

    deposit(amount: number): void {
        this.balance += amount;
    }

    getBalance(): number {
        return this.balance;
    }
}

const account = new BankAccount();
account.deposit(1000);
console.log(account.getBalance()); // Output: 1000
// console.log(account.balance); // Error: Property 'balance' is private
```

---

## 7. **Polymorphism**

- Allows different classes to have methods with the same name but different behavior.

### Example:

```typescript
class Shape {
    area(): number {
        return 0;
    }
}

class Circle extends Shape {
    radius: number;

    constructor(radius: number) {
        super();
        this.radius = radius;
    }

    area(): number {
        return Math.PI * this.radius * this.radius;
    }
}

class Rectangle extends Shape {
    width: number;
    height: number;

    constructor(width: number, height: number) {
        super();
        this.width = width;
        this.height = height;
    }

    area(): number {
        return this.width * this.height;
    }
}

const shapes: Shape[] = [new Circle(5), new Rectangle(4, 5)];
shapes.forEach(shape => console.log(shape.area()));
// Output: 78.53981633974483 (Circle)
// Output: 20 (Rectangle)
```

---

## 8. **Abstract Classes**

- Enforce subclasses to implement specific methods.
- Use the `abstract` keyword in TypeScript.

### Example:

```typescript
abstract class Shape {
    abstract area(): number; // Must be implemented by subclasses
}

class Circle extends Shape {
    radius: number;

    constructor(radius: number) {
        super();
        this.radius = radius;
    }

    area(): number {
        return Math.PI * this.radius * this.radius;
    }
}

const circle = new Circle(5);
console.log(circle.area()); // Output: 78.53981633974483
```

---

## 9. **Summary Table**

| **Concept**      | **JavaScript/TypeScript Feature**                  |
| ---------------- | -------------------------------------------------- |
| Class            | `class` keyword                                    |
| Constructor      | `constructor` function                             |
| Instance Method  | Regular methods using `this`                       |
| Static Method    | `static` keyword                                   |
| Access Modifiers | `public`, `private`, `protected` (TypeScript only) |
| Inheritance      | `extends` keyword                                  |
| Abstract Class   | `abstract` keyword (TypeScript only)               |
| Polymorphism     | Methods with the same name in different classes    |

---
