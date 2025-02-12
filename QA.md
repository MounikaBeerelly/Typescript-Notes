# TypeScript Question and Answers

1. ## What is TypeScript ?
- TypeScript is a programming language that adds extra features to JavaScript. 
- It helps you write more reliable code by letting you define what type of data (like numbers, strings, or objects) each part of your code should use.

2. ##  Basic Types in TypeScript ?
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
3. ## Static Typing in TypeScript
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

4. ## Interfaces in TypeScript.
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

5. ## Union Types in TypeScript
- Union Types in TypeScript allow a variable to hold more than one type of value.
- This is useful when a variable can be one of several types, giving you flexibility while still enforcing type safety.
1. **Basic Syntax**
- To use a union type, you use the pipe symbol ( | ) to separate the different types a variable can hold.
- Example of Union Types
    ```
    let value: string | number;

    value = "Hello";  // OK
    value = 42;       // OK
    // value = true;  // Error: Type 'boolean' is not assignable to type 'string | number'
    ```
- **Remember :**
- `value` can be either a `string` or a `number` , but not a `boolean`.
2. **Using Union Types in Functions**
- Union types are also useful for function parameters and return values, allowing functions to accept or return multiple types.
- Example of Union Types in Functions
    ```
    function printId(id: number | string): void {
        console.log(`Your ID is: ${id}`);
    }
    printId(123);      // Output: Your ID is: 123
    printId("ABC123"); // Output: Your ID is: ABC123
    ```
- **Key Points:**
- printId can accept either a number or a string as its argument.
3. **Type Narrowing :**
- When you use union types, TypeScript often needs to determine which type is being used at a specific point in the code. This process is called type narrowing. 
-mTypeScript uses conditions to figure out which type is 
currently being used.
- Example of Type Narrowing
    ```
    function printLength(value: string | number): void {
        if (typeof value === "string") {
        console.log(`String length: ${value.length}`);
    } else {
        console.log(`Number value: ${value}`);
    }
    }
    printLength("Hello"); // Output: String length: 5
    printLength(123);     // Output: Number value: 123
    ```
- **How it works:**
    - The `typeof` operator is used to check the type of `value`.
    - If `value` is a string, `value.length` is used. If itʼs a number, just print the `number`.
4. **Union Types with Object :**
- Union types can also be used with objects, allowing different object shapes.
- Example with Object Union Types
    ```
    interface Cat {
        type: "cat";
        meow: () => void;
    }
    interface Dog {
        type: "dog";
        bark: () => void;
    }
    type Pet = Cat | Dog;
    function interactWithPet(pet: Pet): void {
        if (pet.type === "cat") {
            pet.meow();
        } else {
            pet.bark();
        }
    }
    const myCat: Cat = { type: "cat", meow: () => console.log("Meow!") };
    const myDog: Dog = { type: "dog", bark: () => console.log("Woof!") };
    interactWithPet(myCat); // Output: Meow!
    interactWithPet(myDog); // Output: Woof!
    ```
- **Key Points:**
- Pet can be either a Cat or a Dog.
- Type narrowing is used to handle the different methods ( meow or bark )  based on the type of pet.
- **How to Remember Union Types :**
    - Pipe Symbol (|) - Think of it as saying “or.ˮ You can have string or number.
    - Flexibility - Union types give you flexibility by allowing multiple possible types for a variable.
    - Type Narrowing - TypeScript helps you figure out which type youʼre dealing with at any point in your code.
- Union types are powerful tools in TypeScript that help you handle variables and functions that can work with multiple types, improving the flexibility and safety of your code.

6. ## Generics in TypeScript
- Generics in TypeScript are a way to create reusable components or functions that work with different data types. - They allow you to define a placeholder for a type, which you can then specify later when you use the omponent or function. 
- This makes your code more flexible and type-safe.
1. **Basics of Generics :**
- Generics use a placeholder `<T> (or any letter)` to represent a type. 
- You can then specify the actual type when you use the generic component or function.
- Example of a Generic Function
    - Hereʼs a simple generic function that returns the same type that it receives.
    ```
    function identity<T>(value: T): T {
        return value;
    }
    console.log(identity("Hello")); // Output: Hello
    console.log(identity(42));      // Output: 42
    ```
- **Key Points:**
    - `<T>` is a placeholder for any type.
    - The function identity works with any type (string, number, etc.) and returns that same type.
2. **Generics with Classes**
- Generics can also be used with classes to create data structures that can work with different types.
- Example of a Generic Class
    ```
    class Box<T> {
        private value: T;
        constructor(value: T) {
        this.value = value;
    }
    getValue(): T {
        return this.value;
    }
    }
    const stringBox = new Box<string>("A String");
    console.log(stringBox.getValue()); // Output: A String
    const numberBox = new Box<number>(123);
    console.log(numberBox.getValue()); // Output: 123
    ```
- **Key Points:**
    - `Box<T>` can hold a value of any type.
    - When creating a Box , you specify the type of value it will hold (string or number in this case).
3. **Generics with Interfaces :**
- Generics can be used with interfaces to define contracts for various types.
- Example of a Generic Interface
    ```
    interface Result<T> {
        data: T;
        error: string | null;
    }
    const successResult: Result<string> = {
        data: "Everything is fine",
        error: null,
    };
    const failureResult: Result<number> = {
        data: 0,
        error: "An error occurred",
    };
    console.log(successResult); // Output: { data: "Everything is fine", error: null }
    console.log(failureResult); // Output: { data: 0, error: "An error occurred" }
    ```
- **Key Points:**
    - Result<T> can describe the result of an operation with any type of data (string, number, etc.).
4. **Constraints on Generics  :**
- You can restrict the types that can be used with a generic by adding constraints. This ensures that the generic type adheres to a certain shape or behavior.
- Example of Generics with Constraints
    ```
    interface Lengthwise {
        length: number;
    }
    function logLength<T extends Lengthwise>(value: T): void {
        console.log(`Length: ${value.length}`);
    }
    logLength("Hello");      // Output: Length: 5
    logLength([1, 2, 3]);   // Output: Length: 3
    // logLength(42);        // Error: Argument of type 'number' is not assignable to parameter of type 'Lengthwis
    e'.
    ```
- **Key Points:**
    - T extends `Lengthwise` ensures that `T` has a length property.
    - This allows `logLength` to work only with types that have a length property.
- **How to Remember Generics:**
    - Placeholders for Types - Generics are like placeholders (`<T>`) for types. They let you write code that can handle many types, not just one.
    - Flexibility and Reusability - Generics make your functions and classes flexible and reusable with different types.
    - Constraints - You can limit what types can be used with generics to ensure they meet certain requirements (like having a length property).
- Generics in TypeScript help you create flexible and reusable components while maintaining type safety, making your code more robust and adaptable.

7. ## Type Inference in TypeScript
- Type Inference is a feature in TypeScript where the compiler automatically determines the type of a variable based on its value. 
- This means you donʼt always need to explicitly specify types because TypeScript can "infer" them from the context.
1. **How Type Inference Works -**
- When you declare a variable and assign a value to it, TypeScript will infer the type of the variable from the assigned value.
- Example of Type Inference
    ```
    let message = "Hello, TypeScript!"; // TypeScript infers 'string'
    let count = 42;                     // TypeScript infers 'number'
    let isValid = true;                 // TypeScript infers 'boolean'
    // message = 123;  // Error: Type 'number' is not assignable to type 'string'
    ```
- **Key Points:**
    - message is inferred as string because of the initial value "Hello, TypeScript!".
    - You cannot assign a value of a different type to the variable after initialization.
2. **Type Inference in Functions**
- For functions, TypeScript can infer the return type based on the function's implementation.
- Example of Type Inference in Functions
    ```
    function add(a: number, b: number) {
        return a + b; // TypeScript infers the return type as 'number'
    }
    const result = add(10, 20); // TypeScript knows 'result' is a number
    console.log(result);        // Output: 30
- **Key Points:**
    - TypeScript infers the return type of the add function as number from the a + b operation.
    - Explicitly declaring the return type is optional when inference works correctly.
3. **Contextual Typing**
- TypeScript can infer the type of a variable or function based on its context, such as in event handlers or callbacks.
- Example of Contextual Typing
    ```
    document.addEventListener("click", (event) => {
        console.log(event.clientX, event.clientY); // 'event' is inferred as MouseEvent
    });
    ```
- **Key Points:**
    - The event parameter is automatically inferred as a `MouseEvent` because the callback is used in a click event handler.
4. **Best Practices with Type Inference**
- While type inference reduces the need for explicit type annotations, there are situations where you should still provide explicit types for clarity, especially for function parameters and return types.
- Example of Explicit Types vs. Inferred Types
    ```
    // Inferred type
    let name = "Alice"; // TypeScript infers 'string'
    // Explicit type (useful for clarity or complex scenarios)
    let age: number = 25; // Explicitly declares 'number' type
    ```
- **When to Use Explicit Types:**
    - When the inferred type is not obvious.
    - When the code's readability or intent can benefit from explicit annotation.
- **How to Remember Type Inference:**
    - Saves Effort - TypeScript automatically assigns types based on values, saving you from writing redundant type annotations.
    - Automatic but Smart - TypeScript will infer types wherever it can, but you can always explicitly declare them if needed.
    - Clarity is Key - Rely on type inference for simple cases, but use explicit types for complex ones or when the inferred type isnʼt clear.
- Type inference is a powerful feature in TypeScript that simplifies coding while maintaining type safety.
  
8. ## Optional Properties/Parameters:
- In TypeScript, you can define properties and parameters as optional.
- This means the value is not required, and the property or parameter may or may not be provided.
1. **Optional Properties in Interfaces**
    - When defining an interface, you can make a property optional by adding a `?` after its name. If the property is not provided, TypeScript will not throw an error.
    - Example:
    ```
    interface User {
        name: string;
        age?: number; // 'age' is optional
    }
    const user1: User = { name: "Alice" };       // Valid: 'age' is not provided
    const user2: User = { name: "Bob", age: 30 }; // Valid: 
    'age' is provided
    console.log(user1); // Output: { name: "Alice" }
    console.log(user2); // Output: { name: "Bob", age: 30 }
    ```
- **Key Points:**
    - The ? makes the age property optional.
    - If age is not provided, TypeScript does not raise an error.
2. **Optional Parameters in Functions**
- When defining a function, you can make a parameter optional using the same `?`. Optional parameters must always come after required parameters.
- Example:
    ```
    function greet(name: string, age?: number): string {
        if (age) {
            return `Hello, ${name}. You are ${age} years old.`;
        }
        return `Hello, ${name}.`;
    }
    console.log(greet("Alice"));       // Output: Hello, Alice.
    console.log(greet("Bob", 30));     // Output: Hello, Bob. You are 30 years old.
- **Key Points:**
    - `age` is an optional parameter. It can be provided or omitted.
    - The function handles both cases (age provided or not) correctly.
3. **Using Optional Properties with Default Values -**
- Optional properties do not have default values unless explicitly assigned.
- Example:
    ```
    interface Config {
        timeout?: number; // Optional, default behavior depends on usage
    }
    const defaultConfig: Config = {};
    const customConfig: Config = { timeout: 5000 };
    console.log(defaultConfig.timeout); // Output: undefined
    console.log(customConfig.timeout);  // Output: 5000
    ```
- **Remember This:**
    - Syntax - Use `?` to make properties or parameters optional.
    - Optional Properties - Allow objects to omit certain fields.
    - Optional Parameters - Allow functions to be called with fewer arguments.
    - Safe Usage - Always handle the possibility of `undefined` when accessing optional values.
- By using optional properties and parameters, you can make your code more flexible and easier to use, while still maintaining type safety.

9. ## Enums in typeScript
- Enums are a special feature in TypeScript that allow you to define a set of named constants. 
- They make code more readable and maintainable by 
grouping related values together.
- Types of Enums in TypeScript :
1. **Numeric Enums**
- Default behavior: Members are automatically assigned numeric values starting from 0.
- Example:
    ```
    enum Status {
        Pending,   // 0
        InProgress, // 1
        Completed   // 2
    }
    console.log(Status.Pending);     // Output: 0
    console.log(Status.InProgress);  // Output: 1
    console.log(Status.Completed);   // Output: 2
- **Key Points:**
    - The first member `( Pending )` gets 0 by default, and the rest increment by 1.
    - You can access enum values using both names `(Status.Pending )` and numbers `( Status[0] )`.
2. **Custom Numeric Enums**
- You can assign custom numbers to enum members. Subsequent members will increment from the assigned value unless explicitly defined.
- Example:
    ```
    enum ResponseCode {
        Success = 200,
        BadRequest = 400,
        NotFound = 404
    }
    console.log(ResponseCode.Success);    // Output: 200
    console.log(ResponseCode.BadRequest); // Output: 400
    console.log(ResponseCode.NotFound);   // Output: 404
    ```
- **Key Points:**
    - Members can have arbitrary numeric values.
    - Thereʼs no restriction on the order of values.
3. **String Enums**
- Enums can also store strings, which are often more descriptive.
- Example:
    ```
    enum Direction {
        North = "NORTH",
        South = "SOUTH",
        East = "EAST",
        West = "WEST"
    }
    console.log(Direction.North); // Output: "NORTH"
    console.log(Direction.West);  // Output: "WEST"
    ```
- **Key Points:**
    - Each member must have a manually assigned string value.- Unlike numeric enums, string enums do not auto-increment.
4. **Heterogeneous Enums**
- Enums can mix numeric and string values, but this is not recommended for readability.
- Example:
    ```
    enum Mixed {
        Yes = 1,
        No = "NO"
    }
    console.log(Mixed.Yes); // Output: 1
    console.log(Mixed.No);  // Output: "NO"
    ```
- **Key Points:**
    - Mixing types can make the enum harder to understand and maintain.
- **Reverse Mapping (Only for Numeric Enums)**
- Numeric enums support reverse mapping, allowing you to get the name of the enum member using its value.
- Example:
    ```
    enum Status {
    Pending = 1,
    InProgress,
    Completed
    }
    console.log(Status[1]); // Output: "Pending"
    console.log(Status[2]); // Output: "InProgress"
    ```
- **Key Points:**
    - Reverse mapping works only for numeric enums, not string enums.
- **Enum as Types** 
- Enums can be used to type variables or parameters to ensure they have only valid values.
- Example:
    ```
    enum Role {
        Admin,
        User,
        Guest
    }
    function assignRole(role: Role) {
        if (role === Role.Admin) {
            console.log("Admin access granted.");
        }
    }
    assignRole(Role.Admin); // Output: Admin access granted.
    // assignRole(1);        // Error in strict mode if Role is not directly referenced
    ```
- **Use Cases of Enums**
    - Readable Constants - Replace magic numbers or strings with meaningful names.
    - Grouping Values - Group related constants like roles, directions, or states.
    - Type Safety - Prevent invalid values from being assigned.
- **Best Practices**
    - Use String Enums - Prefer string enums for descriptive and human readable values.
    - Avoid Heterogeneous Enums - They can lead to confusion.
    - Use Reverse Mapping Only If Needed - Numeric enums support it, but itʼs rarely required.
- Enums are a powerful feature that helps you organize related constants in a type-safe and maintainable way.
 
 
