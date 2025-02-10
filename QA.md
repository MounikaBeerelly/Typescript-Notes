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
1. **Type Annotations**
- Type annotations in TypeScript are a way to explicitly declare the type of a variable, function parameter, or return value. This means you tell TypeScript what kind of data a variable should hold.
- Example of Type Annotations
    ```
    let message: string = "Hello, TypeScript!"; // 'message' must always be a string
    let count: number = 42;                    // 'count' m
    ust always be a number
    let isDone: boolean = true;                // 'isDone' 
    must always be a boolean
    ```
    - **Remember** :
        - string, number, and boolean are basic types.
        - If you try to assign a value of a different type to these variables, TypeScript will show an error.
    -  **Why is this important ?**
        - Error Preventionm - Static typing helps you avoid common errors, like accidentally assigning a string to a number variable.
        - Code Clarity - When you or someone else reads your code, the types make it clear what kind of data to expect, making the code easier to understand and maintain.
- **Type Annotations in Functions**
    - You can also use type annotations in functions to specify the types of the parameters and the return value.
    ```
    function add(a: number, b: number): number {
        return a + b;
    }
    console.log(add(5, 3));  // Output: 8
    ```
- **Key Points to Remember :**
    - `a: number` and `b: number` specify that a and b must be numbers. 
    - `: number` after the parentheses indicates that the function returns a number.
    - If you try to call the add function with anything other than numbers, TypeScript will give you an error.
- **Type Inference** :
----------------------
- TypeScript can automatically infer types based on the value assigned to a variable, so you donʼt always need to use type annotations.
    ```
    let name = "Sagar";  // TypeScript infers that 'name' is a string
    let age = 24;        // TypeScript infers that 'age' is a number
- Type inference is useful, but explicitly using type annotations can make your code more understandable and error-proof.
- **How to Remember Static Typing :**
    - Static = Set in Stone : Once you define a type, it doesnʼt change. Like setting something in stone, it stays the same.
    - Type Annotations - Labels: Think of type annotations as labels you stick on variables, telling everyone (and TypeScript) exactly whatʼs inside.
    - Error Prevention - Static typing acts like a safety net, catching mistakes before they cause problems.
    - Code Clarity : With types clearly marked, anyone can quickly understand what your code is doing.
- By using static typing and type annotations in TypeScript, you write safer, more reliable code that's easier to read and maintain.

4. ### Interfaces in TypeScript.
- **Interfaces** in TypeScript are like blueprints that define the structure of an object. They allow you to specify what properties and methods an object should have, along with their types. 
- Interfaces ensure that objects follow a certain structure,helping to catch errors and making your code more predictable.
1. **Basic Structure of an Interface** :
- An interface is defined using the interface keyword, followed by the name of the interface. Inside the interface, you declare properties and their types.
- Example of a Simple Interface
    ```
    interface User {
        name: string;
        age: number;
        isActive: boolean;
    }
    let user1: User = {
        name: "Sagar",
        age: 24,
        isActive: true,
    };
    console.log(user1); // Output: { name: "Sagar", age: 24, isActive: true }
    ```
- **Remember :**
- The User interface defines that any object of type 
name, age, and User must have isActive properties with specific types (string, number, boolean).
- If you try to create an object without following this structure, TypeScript will throw an error.
2. **Optional Properties :**
- In an interface, you can define optional properties by using a `?` after the property name. Optional properties donʼt have to be included in the object.
- Example with Optional Properties
    ```
    interface User {
        name: string;
        age: number;
        isActive: boolean;
        email?: string;  // Optional property
    }
    let user2: User = {
        name: "Amit",
        age: 25,
        isActive: false,
        // email is optional, so we can skip it
    };
    console.log(user2); // Output: { name: "Amit", age: 25, isActive: false }
- **Key Points :**
- email is optional, so user2 can be created without it.
- This flexibility is useful when not every object needs every property.
3. **Read-only Properties :**
- You can use the readonly modifier to make properties in an interface immutable after they are set.
- Example with Read-Only Properties
    ```
    interface User {
        readonly id: number;
        name: string;
        age: number;
    }
    let user3: User = {
        id: 101,
        name: "Kiran",
        age: 26,
    };
    // user3.id = 102; // Error: Cannot assign to 'id' because it is a read-only property.
    ```
- **Key Points :**
- id is marked as readonly , meaning once it's set, it can't be changed.
- This ensures that critical properties remain constant adding safety to your code.
4. **Interface for Functions :**
- Interfaces can also be used to define the structure of functions, including the parameters and return type.
- Example of an Interface for a Function
    ```
    interface Greet {
        (name: string): string;
    }
    let sayHello: Greet = function(name: string) {
        return `Hello, ${name}!`;
    };
    console.log(sayHello("Sagar")); // Output: "Hello, Sagar!"
    ```
- **Remember :**
- The Greet interface defines that any function of this type must take a string as a parameter and return a string.
5. **Extending Interfaces :**
- You can create new interfaces by extending existing ones, which allows you to build on previous structures without rewriting them.
- Example of Extending an Interface
    ```
    interface Person {
        name: string;
        age: number;
    }
    interface Employee extends Person {
        employeeId: number;
    }
    let employee1: Employee = {
        name: "John",
        age: 30,
        employeeId: 1234,
    };
    console.log(employee1); // Output: { name: "John", age: 30, employeeId: 1234 }
    ```
- **Key Points :**
- Employee extends Person, so it inherits name and age while adding employeeId.
- This helps in reusing code and keeping your interfaces DRY (Donʼt epeat Yourself).
- **How to Remember Interfaces :**
    - Blueprint - Think of an interface as a blueprint or a contract that objects must follow.
    - Optional Properties - `?` means the property is optional, like leaving a field blank in a form.
    - Read-Only - readonly is like a lock on a property, preventing changes after it's set.
    - Functions - Interfaces can describe the structure of functions too, not just objects.
    - Inheritance - Interfaces can be extended, like building new floors on an existing building.
- Interfaces help you define clear, consistent structures for your objects, leading to more maintainable and error-free code.
