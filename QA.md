# TypeScript Question and Answers

1. ### What is TypeScript ?
- TypeScript is a programming language that adds extra features to JavaScript. 
- It helps you write more reliable code by letting you define what type of data (like numbers, strings, or objects) each part of your code should use.

2. ###  Basic Types in TypeScript ?
- TypeScript extends JavaScript by adding types to variables, enabling better error detection and code clarity. 
- Basic types are the foundation of TypeScript, and they represent the simplest forms of data youʼll work with.
- List of Basic Types
    - string : Represents text.
    - number : Represents numeric values.
    - boolean : Represents true/false values.
    - array : Represents a collection of values.
    - tuple : Represents a fixed-size array with specific types at each index.
    - enum : Represents a set of named constants.
    - any : Represents any type (avoids type checking)
    - unknown : Represents a safer version of any
    - void : Represents no value or absence of return
    - null and undefined : Represent empty or uninitialized values
    - never : Represents values that never occur

**string type :**
- Used to store textual data.
- Example:
    ```
    let firstName: string = "Alice";
    let greeting: string = `Hello, ${firstName}`; // Using 
    template literals
    console.log(greeting); // Output: Hello, Alice
    ```
**number type :**
- Used for all numbers, including integers and floating-point values.
- Example:
    ```
     let age: number = 24;
    let pi: number = 3.14;
    console.log(age, pi); // Output: 24 3.14
    ```
**Boolean type :**
- Used for true/false values.
- Example:
    ```
    let isLoggedIn: boolean = true;
    console.log(isLoggedIn); // Output: true
    ```
**array type :**
-  Used to store a list of values. Can be typed with a specific type of elements.
- Example:
    - Using generic type ( Array<Type> ):
    ```
    let numbers: Array<number> = [1, 2, 3];
    console.log(numbers); // Output: [1, 2, 3]
    ```
    - Using square brackets ( Type[] ):
    ```
    let names: string[] = ["Alice", "Bob"];
    console.log(names); // Output: ["Alice", "Bob"]
    ```
**tuple :**
- An array with a fixed number of elements, where each element has a specific type.
- Example:
    ```
    let user: [string, number] = ["Alice", 24];
    console.log(user); // Output: ["Alice", 24]
    ```
**enum :**
- Used for defining a set of named constants.
- Example:
    ```
    enum Color {
        Red,
        Green,
        Blue
    }
    let myColor: Color = Color.Green;
    console.log(myColor); // Output: 1 (index of Green in the enum)
    ```
**any :**
- Allows a variable to hold any type. Use cautiously, as it disables type checking.
- Example:
    ```
    let value: any = "Hello";
    value = 42; // Allowed
    console.log(value); // Output: 42
    ```
**unknown :**
- Similar to any, but safer as it requires type checking before usage.
- Example:
    ```
    let value: unknown = "Hello";
    // value.toUpperCase(); // Error: Object is of type 'unknown'
    if (typeof value === "string") {
    console.log(value.toUpperCase()); // Output: HELLO
    }
    ```
**void :**
- Represents the absence of a value, typically used for functions that donʼt return anything.
- Example:
    ```
    function logMessage(message: string): void {
        console.log(message);
    }
    logMessage("Hello, TypeScript!"); // Output: Hello, TypeScript!
    ```
**null and undefined :**
- null : Represents an intentionally empty value.
- undefined : Represents an uninitialized value.
- Example:
    ```
    let value: null = null;
    let anotherValue: undefined = undefined;
    console.log(value, anotherValue); // Output: null undefined
    ```
**never :**
- Represents values that never occur, such as functions that always throw an error or never return.
- Example:
    ```
    function throwError(message: string): never {
        throw new Error(message);
    }
    ```
3. ### Static Typing in TypeScript
- Static Typing is a key feature in TypeScript that allows you to define the type of a variable, function parameter, or return value at the time of writing your code. 
- This is different from JavaScript, where types are determined at runtime. 
- With static typing, TypeScript checks your code for type errors before it even runs, helping you catch mistakes early.
1. Type Annotations
- Type annotations in TypeScript are a way to explicitly declare the type of a variable, function parameter, or return value. This means you tell TypeScript what kind of data a variable should hold.
- Example of Type Annotations
    ```
    let message: string = "Hello, TypeScript!"; // 'message' must always be a string
    let count: number = 42;                    // 'count' m
    ust always be a number
    let isDone: boolean = true;                // 'isDone' 
    must always be a boolean
    ```
