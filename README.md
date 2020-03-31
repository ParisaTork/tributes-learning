# tributes-learning

## Learning for this [project](https://github.com/tuyetngo1/Tributes):

- [ ] [React](https://reactjs.org/docs/getting-started.html) / [GraphQL](https://graphql.org/learn/)
  - [ ] [Docs - Intro to React](https://reactjs.org/tutorial/tutorial.html)
  - [ ] [Docs - Hooks at a Glance](https://reactjs.org/docs/hooks-overview.html)
  - [ ] [React (Maximilian Schwarzmüller)](https://learning.oreilly.com/videos/react-the/9781789132229)
  - [ ] [React for Beginners (Wes Bos)*](https://reactforbeginners.com/)
  - [ ] [Stephen Grider](https://www.udemy.com/course/the-complete-react-native-and-redux-course/)
  - [ ] [Advanced React and GraphQL (Wes Bos)*](https://advancedreact.com/)
  - [ ] [Fullstack Tutorial for GraphQL](https://www.howtographql.com/)
  - [ ] [Exploring GraphQL: A Query Language for APIs (edX)](https://www.edx.org/course/exploring-graphql-a-query-language-for-apis)
  - [ ] [Create a front-end app with React](https://www.codecademy.com/learn/paths/build-web-apps-with-react)
  - [ ] [Learn ReactJS: Part I](https://www.codecademy.com/learn/react-101)
  - [ ] [Learn ReactJS: Part II](https://www.codecademy.com/learn/react-102)
  - [ ] React toy project
  - [ ] GraphQL toy project

- [ ] [Next.js](https://nextjs.org/learn/basics/getting-started) / [CSS-in-JS](https://cssinjs.org/?v=v10.1.1)
  - [ ] [Next.js + CSS-in-JS (Next.js docs)](https://nextjs.org/learn/basics/getting-started)
  - [ ] [Universal React with Next.js](https://learning.oreilly.com/videos/universal-react-with/9781839210792)
  - [ ] Next.js toy project
  - [ ] CSS-in-JS toy project
  
- [ ] [TypeScript](https://www.typescriptlang.org/docs/handbook/release-notes/overview.html) 
  - [x] [TS in 5 minutes](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html) - [notes](#ts5mins)
  - [ ] [Introduction to TypeScript (Tamas Piros)](https://learning.oreilly.com/videos/introduction-to-typescript/10000DIHV201907) - [notes](#tsintro)
  - [ ] [Mastering TypeScript Programming Techniques (Tamas Piros)](https://learning.oreilly.com/videos/mastering-typescript-programming/9781787121416)
  - [ ] TS toy project

- [ ] Other
  - [x] [AWS Amplify](https://aws.amazon.com/getting-started/hands-on/deploy-react-app-cicd-amplify/) - [GitHub repo](https://github.com/ParisaTork/amplifyapp) + [URL](https://master.dq83h9g14lssn.amplifyapp.com/)
  - [ ] [Managing Remote Teams with Upwork (Udacity)](https://classroom.udacity.com/courses/ud942)

(*) = For Wes Bos courses, buy through r/groupdeals

***

## Notes:

### TS in 5 minutes <a name="ts5mins"></a>

VSCode = best IDE for TS

#### <ins>Running the TS compiler in the CL</ins>

```
tsc filename.ts
```

#### <ins>Type Annotations</ins>

Type annotations in TypeScript are lightweight ways to record the intended contract of the function or variable. 

We can specify the type using :Type after the name of the variable, parameter or property

Example: Type Annotation of Varibles:
```
var age: number = 32; // number variable
var name: string = "John";// string variable
var isUpdated: boolean = true;// Boolean variable
```
Example: Type Annotation of Parameters:
```
function display(id:number, name:string)
{
    console.log("Id = " + id + ", Name = " + name);
}
```

Example: Type Annotation in Objects:
```
var employee : { 
    id: number; 
    name: string; 
}; 

employee = { 
  id: 100, 
  name : "John"
}
```

#### <ins>Interfaces - [TBT](https://github.com/sebastianchristopher/acebook-ePact/wiki/Interfaces-(Parisa))</ins> - To read: [Interfaces](https://www.typescriptlang.org/docs/handbook/interfaces.html)

An interface is a syntactical contract that an entity should conform to. In other words, an interface defines the syntax that any entity must adhere to.

The interface keyword is used to declare an interface. The interface name is typically capitalized.

In TypeScript, two types are compatible if their internal structure is compatible. This allows us to implement an interface just by having the shape the interface requires, without an explicit implements clause.

Example of an interface:
```
interface Person {
    firstName: string;
    lastName: string;
}

function greeter(person: Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}

let user = { firstName: "Jane", lastName: "User" };
```

The easiest way to see how interfaces work is to start with a simple example:

```
function printLabel(labeledObj: { label: string }) {
    console.log(labeledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
```

- The type checker checks the call to the function (printLabel). 
- The printLabel function has a single parameter that requires that the object passed in has a property called label of type string. 
- Notice that our object actually has more properties than this, but the compiler only checks that at least the ones required are present and match the types required. 
- There are some cases where TypeScript isn’t as lenient, which we’ll cover in a bit.

<ins>Summary of bullet points above:</ins>
- Parameter of function required to have object with specific property (label: string)
- Object will 'pass' the compiler if has this property - superfluous properties don't matter *this* time

We can write the same example again, this time using an interface to describe the requirement of having the label property that is a string:

```
interface LabeledValue {
    label: string;
}

function printLabel(labeledObj: LabeledValue) {
    console.log(labeledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
```

- The interface LabeledValue is a name we can now use to describe the requirement in the previous example. 
- It still represents having a single property called label that is of type string. 
- Notice we didn’t have to explicitly say that the object we pass to printLabel implements this interface like we might have to in other languages. 
- Here, it’s only the shape that matters. If the object we pass to the function meets the requirements listed, then it’s allowed.
- It’s worth pointing out that the type checker does not require that these properties come in any sort of order, only that the properties the interface requires are present and have the required type.

<ins>Summary of bullet points above:</ins>
- Interface = requirement
- No explicit 'implements'
- If object passed to function meets requirements (has a property of the interface), it'll 'pass' the compiler
- Property order doesn't matter

My funner example 🤵🏽🕴🍾:

```
interface AppropriatelyDressed {
    blackTieOutfit: string;
}

function metrosexualBouncer(randomPerson : AppropriatelyDressed) {
    console.log("Nice " + randomPerson.blackTieOutfit + " !");
}

let Brian = {blackTieOutfit: "Tuxedo", comportment: "Tipsy"};
printLabel(Brian);

/** Brian will get in, because of his black tie outfit.
Even though he's slightly drunk.
I don't make the rules.
*/
```
<ins>Optional Properties</ins>
Interfaces with optional properties are written similar to other interfaces, with each optional property denoted by a ? at the end of the property name in the declaration.

Example of interface with optional properties:
```
interface SquareConfig {
    color?: string;
    width?: number;
}

function createSquare(config: SquareConfig): {color: string; area: number} {
    let newSquare = {color: "white", area: 100};
    if (config.color) {
        newSquare.color = config.color;
    }
    if (config.width) {
        newSquare.area = config.width * config.width;
    }
    return newSquare;
}

let mySquare = createSquare({color: "black"});
```
The advantage of optional properties is that you can describe these possibly available properties while still also preventing use of properties that are not part of the interface. For example, had we mistyped the name of the color property in createSquare, we would get an error message e.g. if we had a color property and spelt it as 'clor', the error message would be: Error: Property 'clor' does not exist on type 'SquareConfig'

<ins>Summary of Optional Properties</ins>
- Can be denoted with a ? e.g. color?:string
- Useful in case of misspellings

<ins>Readonly Properties</ins>

Use readonly keyword before property name:
```
interface Point {
    readonly x: number;
    readonly y: number;
}
```
TypeScript comes with a ReadonlyArray<T> type that is the same as Array<T> with all mutating methods removed, so you can make sure you don’t change your arrays after creation (can be overridden with a type assertion though):
  
```
let a: number[] = [1, 2, 3, 4];
let ro: ReadonlyArray<number> = a;
ro[0] = 12; // error!
ro.push(5); // error!
ro.length = 100; // error!
a = ro; // error!
```
<ins>readonly vs const</ins>

Variables use const whereas properties use readonly.

<ins>Excess Property Checks</ins>

```
interface SquareConfig {
    color?: string;
    width?: number;
}

function createSquare(config: SquareConfig): { color: string; area: number } {
    // ...
}

let mySquare = createSquare({ colour: "red", width: 100 });
```

mySquare would fail, because object literals get special treatment and undergo excess property checking when assigning them to other variables, or passing them as arguments. If an object literal has any properties that the “target type” doesn’t have, you’ll get an error.

**Got to 'Excess Property Checks' [here](https://www.typescriptlang.org/docs/handbook/interfaces.html)**

#### <ins>Classes</ins> - To read: [Classes](https://www.typescriptlang.org/docs/handbook/classes.html)

TypeScript supports new features in JavaScript, like support for class-based object-oriented programming.

Here we’re going to create a Student class with a constructor and a few public fields. Notice that classes and interfaces play well together, letting the programmer decide on the right level of abstraction.

Also of note, the use of public on arguments to the constructor is a shorthand that allows us to automatically create properties with that name.

```
class Student {
    fullName: string;
    constructor(public firstName: string, public middleInitial: string, public lastName: string) {
        this.fullName = firstName + " " + middleInitial + " " + lastName;
    }
}

interface Person {
    firstName: string;
    lastName: string;
}

function greeter(person: Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}

let user = new Student("Jane", "M.", "User");

document.body.textContent = greeter(user);
```

#### <ins>Running your TypeScript web app</ins>

greeter.html file
```
<!DOCTYPE html>
<html>
    <head><title>TypeScript Greeter</title></head>
    <body>
        <script src="greeter.js"></script>
    </body>
</html>
```
1) Create this greeter.html file
2) Open greeter.html file in the browser
***

### Introduction to TypeScript (Tamas Piros) <a name="tsintro"></a>























