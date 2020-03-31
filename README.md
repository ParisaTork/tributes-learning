# tributes-learning

## Learning for this [project](https://github.com/tuyetngo1/Tributes):

- [ ] React / GraphQL
  - [ ] [Docs - Intro to React](https://reactjs.org/tutorial/tutorial.html)
  - [ ] [Docs - Hooks at a Glance](https://reactjs.org/docs/hooks-overview.html)
  - [ ] [Maximilian Schwarzmüller](https://learning.oreilly.com/videos/react-the/9781789132229)
  - [ ] [Wes Bos*](https://reactforbeginners.com/)
  - [ ] [Stephen Grider](https://www.udemy.com/course/the-complete-react-native-and-redux-course/)
  - [ ] [Advanced React and GraphQL (Wes Bos)*](https://advancedreact.com/)
  - [ ] [GraphQL docs](https://graphql.org/learn/)
  - [ ] [Create a front-end app with React](https://www.codecademy.com/learn/paths/build-web-apps-with-react)
  - [ ] [Learn ReactJS: Part I](https://www.codecademy.com/learn/react-101)
  - [ ] [Learn ReactJS: Part II](https://www.codecademy.com/learn/react-102)
  - [ ] React toy project
  - [ ] GraphQL toy project

- [ ] Next.js / CSS-in-JS
  - [ ] [Next.js + CSS-in-JS (Next.js docs)](https://nextjs.org/learn/basics/getting-started)
  - [ ] [Universal React with Next.js](https://learning.oreilly.com/videos/universal-react-with/9781839210792)
  - [ ] Next.js toy project
  - [ ] CSS-in-JS toy project
  
- [ ] TypeScript 
  - [ ] [TS in 5 minutes](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html)
  - [ ] [Introduction to TypeScript (Tamas Piros)](https://learning.oreilly.com/videos/introduction-to-typescript/10000DIHV201907)
  - [ ] [Mastering TypeScript Programming Techniques (Tamas Piros)](https://learning.oreilly.com/videos/mastering-typescript-programming/9781787121416)
  - [ ] TS toy project

- [ ] Other
  - [ ] [AWS Amplify](https://aws.amazon.com/getting-started/hands-on/deploy-react-app-cicd-amplify/)
  - [ ] [Managing Remote Teams with Upwork (Udacity)](https://classroom.udacity.com/courses/ud942)

(*) = For Wes Bos courses, buy through r/groupdeals

***

## Notes:

### TS in 5 minutes

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

#### <ins>Interfaces - [TBT](https://github.com/sebastianchristopher/acebook-ePact/wiki/Interfaces-(Parisa))</ins>

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

The interface LabeledValue is a name we can now use to describe the requirement in the previous example. It still represents having a single property called label that is of type string. Notice we didn’t have to explicitly say that the object we pass to printLabel implements this interface like we might have to in other languages. Here, it’s only the shape that matters. If the object we pass to the function meets the requirements listed, then it’s allowed.

It’s worth pointing out that the type checker does not require that these properties come in any sort of order, only that the properties the interface requires are present and have the required type.

#### <ins>Classes</ins>

TypeScript supports new features in JavaScript, like support for class-based object-oriented programming.

Here we’re going to create a Student class with a constructor and a few public fields. Notice that classes and interfaces play well together, letting the programmer decide on the right level of abstraction.

Also of note, the use of public on arguments to the constructor is a shorthand that allows us to automatically create properties with that name.

***























