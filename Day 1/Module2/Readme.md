# Module 2 - Declare variable types in typescript



## Lessons Learned

- Types in Typescript
- Enum
- Union & Intersection type
- Type Assertion
- Unknown Type



## Types

All types in TypeScript are subtypes of a single top type called the any type. The any type is the one type that can represent any JavaScript value with no constraints. All other types are categorized as primitive types, object types, or type parameters. These types introduce various static constraints on their values.

The primitive types are the boolean, number, string, void, null, enum and undefined

void - Functions with no return value

The object types are all class, interface, array, and literal types 


## Enum
An enum is a symbolic name for a set of values. Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.
```typescript

enum ContractStatus {
     Permanent,
     Temp,
     Apprentice
}

```
Enums allow you to specify a list of available options. They're especially useful when you have a set of values that a particular variable type may take.

## Union & Intersection type

Union - A union type describes a value that can be one of several type
Intersection

```typescript

let multiType: number | boolean;
multiType = 20;         //* Valid
multiType = true;       //* Valid
multiType = "twenty";   //* Invalid

```
Intersection - Intersection types are closely related to union types, but they're used differently. An intersection type combines two or more types to create a new type that has all properties of the existing types. An intersection allows you to add together existing types to get a single type that has all the features you need.

An Intersection type uses the ampersand (&) to separate each type.

Intersection types are most often used with interfaces.

```typescript

interface Employee {
  employeeID: number;
  age: number;
}
interface Manager {
  stockPlan: boolean;
}
type ManagementEmployee = Employee & Manager;
let newManager: ManagementEmployee = {
    employeeID: 12345,
    age: 34,
    stockPlan: true
};

```

## Type Assertion

If you need to treat a variable as a different data type, you can use a type assertion. It tells the compiler "trust me, I know what I’m doing".

Type assertions have two forms. One is the as-syntax:

(randomValue as string).toUpperCase();

The other version is the "angle-bracket" syntax:

(<string>randomValue).toUpperCase();

```typescript

let randomValue: unknown = 10;

randomValue = true;
randomValue = 'Mateo';

if (typeof randomValue === "string") {
    console.log((randomValue as string).toUpperCase());    //* Returns MATEO to the console.
} else {
    console.log("Error - A string was expected here.");    //* Returns an error message.
}

```

## Unknown Type

The unknown type is similar to the any type in that any value is assignable to type unknown. However, you can't access any properties of an unknown type, nor can you call or construct them.

```typescript 
let randomValue: unknown = 10;
randomValue = true;
randomValue = 'Mateo';

console.log(randomValue.name);  // Error: Object is of type unknown
randomValue();                  // Error: Object is of type unknown
randomValue.toUpperCase();      // Error: Object is of type unknown
```