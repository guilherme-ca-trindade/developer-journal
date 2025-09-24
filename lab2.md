# 🧠 Using Objects in Java
---

## 🚀 Overview
How classes encapsulate behavior and state, and how objects are created and interact through methods and variables. This is foundational for building scalable, modular applications.

---

## 🧩 Key Concepts

### 🔹 Class
- A blueprint for creating objects.
- Defines **methods** (behavior) and **variables** (state).

### 🔹 Instance Variable
- Belongs to an object (instance of a class).
- Each object has its own copy.
- Example: `private String name;`

### 🔹 Instance Method
- Operates on instance variables.
- Called on an object.
- Example: `public void setName(String newName)`

### 🔹 Class Variable (`static`)
- Shared across all instances of a class.
- Useful for constants or counters.
- Example: `private static int count;`

### 🔹 Class Method (`static`)
- Can be called without creating an object.
- Cannot access instance variables directly.
- Example: `public static int getCount()`

### 🔹 Object Creation
- Done using the `new` keyword.
- Example: `Student s1 = new Student();`

### 🔹 Method Invocation
- Instance: `s1.setName("Alice");`
- Static: `Student.getCount();`

---

## 🧪 Practice Reflection
- Reinforce the difference between instance and class members.
- Practice writing constructors and method calls.
- How encapsulation helps organize code and protect data.

---

## 📌 Takeaways
- Understand when to use `static` vs instance members.
- Always initialize objects before use.
- Encapsulation and method design are key to clean, reusable code.
