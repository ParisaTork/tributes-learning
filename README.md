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

- [ ] Next.js / CSS-in-JS
  - [ ] [Next.js + CSS-in-JS (Next.js docs)](https://nextjs.org/learn/basics/getting-started)
  - [ ] [Universal React with Next.js](https://learning.oreilly.com/videos/universal-react-with/9781839210792)
  
- [ ] TypeScript 
  - [ ] [TS in 5 minutes](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html)
  - [ ] [Introduction to TypeScript (Tamas Piros)](https://learning.oreilly.com/videos/introduction-to-typescript/10000DIHV201907)
  - [ ] [Mastering TypeScript Programming Techniques (Tamas Piros)](https://learning.oreilly.com/videos/mastering-typescript-programming/9781787121416)

- [ ] Other
  - [ ] [AWS Amplify](https://aws.amazon.com/getting-started/hands-on/deploy-react-app-cicd-amplify/)
  - [ ] [Managing Remote Teams with Upwork (Udacity)](https://classroom.udacity.com/courses/ud942)

(*) = For Wes Bos courses, buy through r/groupdeals

## Notes:

### TS in 5 minutes

VSCode = best IDE for TS

#### Running the TS compiler in Terminal

```
tsc filename.ts
```

#### Type Annotations 

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

#### Interfaces - [TBT](https://github.com/sebastianchristopher/acebook-ePact/wiki/Interfaces-(Parisa))

An interface is a syntactical contract that an entity should conform to. In other words, an interface defines the syntax that any entity must adhere to.

The interface keyword is used to declare an interface. The interface name is typically capitalized.

In TypeScript, two types are compatible if their internal structure is compatible. This allows us to implement an interface just by having the shape the interface requires, without an explicit implements clause.

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

#### Classes

TypeScript supports new features in JavaScript, like support for class-based object-oriented programming.

Here we’re going to create a Student class with a constructor and a few public fields. Notice that classes and interfaces play well together, letting the programmer decide on the right level of abstraction.

Also of note, the use of public on arguments to the constructor is a shorthand that allows us to automatically create properties with that name.























