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
  - [ ] TS toy project

- [ ] Other
  - [x] [AWS Amplify](https://aws.amazon.com/getting-started/hands-on/deploy-react-app-cicd-amplify/) - [GitHub repo](https://github.com/ParisaTork/amplifyapp) + [URL](https://master.dq83h9g14lssn.amplifyapp.com/)
  - [ ] [Managing Remote Teams with Upwork (Udacity)](https://classroom.udacity.com/courses/ud942) - [notes](#upwork)

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

### Managing Remote Teams with Upwork (Udacity) <a name="upwork"></a>

#### Leading Remote Teams Effectively

- Update your **expectations**:
The single most effective change a company (or the leader of a team) can make is to take a remote-first approach. Don’t just tolerate remote team members as add-ons to your regular meetings: assume that everyone is or may be remote at any time.

- Focus on **results**:
Set **expectations for output early**, and reinforce them often. Focus on results. Companies that consider themselves “results-only work environments” focus on what each team member actually delivers, not on where, how or even when they work.

- Embrace technology:
Choose collaboration technologies that are **simple, reliable and accessible** enough for all to use **easily (and frequently)**

- Create a **“virtual water cooler”**:
Provide opportunities for team members to socialize online, for instance, through Slack, to replace the “water cooler” moments they will be missing from the real-world office. Done right, virtual communication can be even better than in-person.

- Keep tabs on **conversation**:
Managers need to pay close attention to team communication channels, as you will need to be constantly adjusting, coordinating, **clarifying** and helping avoid misunderstandings.

- Be thoughtful about **support**:
Make sure voices are heard during meetings. 

- Realise that it's hard for remotes to read **body language/interject** in video meetings - Solution: 'Hey, what do you think?' to each employee. 

- Be thoughtful about giving remote employees the **floor**

- If in a hybrid (some remote, some not) team, consider having meetings remotely so **EVERYONE interfaces through camera**

#### Tools for Success
- Collaboration capabilities (Google Drive, Google Docs, GSuite, GitHub, Bitbucket, GitLab, Jenkins)
- Communication (Slack, Dash, Google Meet, Zoom, Email, Chromebox)
- Screen Capture and Image Sharing (Jing, Snagit)
- Functional testing tools (TestNG, Selenium, PhantomJS, Sauce Labs)

#### Skills for Success
- Communication (frequent = good)
- Organization
- Understand your schedule + set boundaries

#### Hiring the right people
- Grit & Drive
- Autonomy (esp. self-autonomy)
- Track Record of Success
- Locate teams in same or close timezones
- Ability to use the latest technology
- Results-driven attitude
- Relevant background (i.e. work with prior clients, prior self-employment, entrepreneurial projects, etc.)
- Flexibility & Humility

#### Growing Pains without right tools/tech

- **Vague or poorly defined process**:
When the development lifecycle is not well defined, things can easily become a mess. For those overseeing the process, it’s crucial to understand that communication with a remote team can be scarce compared to communication in an office. There should be no room for implications or interpretations.

- **Version control issues, duplicate code, or messy code**:
Remember, the idea behind distributed teams is that they allow you to get more work done separately, but if developers aren’t communicating effectively you can create new problems and new headaches.

- **Dependencies between teams**:
Divvying up work to get it done faster is great, but you never want one team to be waiting on another to complete their work before they can move forward. These scenarios are known as dependencies and they can negate the efficiency of dividing up the project—unless, that is, you strategically break up code to minimize these dependencies.

- **Lack of coordination between teams**:
While autonomous teams can be highly efficient, you do run the risk that they could progressively diverge and stop communicating important information with each other.

- **Lack of steps/documentation or unclear delineation of processes and clarification on each member's role in the process**:
Remote teams benefit from a shared understanding and documented distinctions and clear process steps.

#### Best Tools for Remote Teams

<ins>Centrally locating project progress and issue tracking</ins>

For more simple development processes, an issue tracker like that built into Github/Gitlab may be sufficient. Using progress assignment, coordination, and tracking tools can help set to-do’s and let everyone check in on the status of a project, no matter where they are. Some projects might be large enough to require two types of project tracking (e.g., Basecamp for high-level project views and JIRA for granular, technical issue tracking).

Suggested tools:
- JIRA for issue and bug tracking
- Asana
- Confluence for documentation
- Basecamp
- Trello
- Float
- Issue tracking in Github/Gitlab

<ins>Prototype apps for a tighter feedback loop</ins>

Prototyping apps is crucial for rapid iteration. For mobile apps and user-facing software, prototyping allows for feedback and testing early on. Try one of these platforms to transform static designs into interactive mockups, allowing stakeholders to get the end view of a product.

Suggested tools:
- InVision
- Flinto
- Origami Studio
- Justinmind
- Marvel
- AdobeXD

<ins>Develop, deploy, and monitor in the cloud</ins>

Software is getting more modular, and so are the IT environments we use to build, test and launch that software. Embracing this approach also makes sense for teams adopting a more distributed model. If you aren’t looking to invest in a large, expensive suite of integrated DevOps software, consider using different tools to divvy up aspects of your development cycle such as collaboration, testing, deployment, or monitoring. Some tools can multitask, so pick the one with the features you need.

Suggested tools:
- Bamboo
- Capture for Jira
- Docker
- CircleCI
- Hipchat
- Amazon Web Services (AWS)
- Other tools for monitoring: BigPandaHostedGraphite, Nagios, New Relic, Pager Duty, Pingdom, Splunk

<ins>Consider security when sharing data and information</ins>

What about protecting the data, systems, and communications that happen when you’re hiring remote freelancers? You might opt to use a virtual private network (VPN) to encrypt connections, grant limited FTP access, or limit rights and permissions when granting access to your server. Download Upwork’s Data Security whitepaper for practical tips on securely working with remote freelancers.

Suggested tools:
- Dropbox
- SmartFile
- Google Drive

#### Best Practices for Rapidly Adopting a Remote Work Strategy

Three Trust Pillars
1. Trust that each person knows how to do the work.
2. They’re accountable to each other.
3. They’re doing their best in uncertain circumstances.

*Consider these tips to help support your team as you all move forward:*

- **Be available.** Communication is pivotal to your team’s success—and that includes creating space if someone needs to talk. Sometimes, people just need to feel heard, whether they have a conflict with a colleague, struggle with working on their own, or are anxious about news in their community.
- **Create a sense of community.** Working from home can be isolating—something that can impact wellbeing as well as productivity. Find ways for your team to stay connected on a regular basis. Here are some ideas:
    - **Daily coffee breaks:** A daily “coffee break” can give everyone a chance to catch up and talk about their day.
    - **Weekly team meetings:** A weekly team meeting can help everyone share successes and stay in the loop.
    - **Video calls:** Use video calls to keep your team engaged. Meetings have different dynamics when you aren’t sitting around the same table. Circulate an agenda ahead of time so your team can be prepared, and call on each person so everyone has a chance to speak. Pause frequently so there’s room for questions that may come up.
- **Err on the side of overcommunication.** Particularly while everyone adjusts to new working arrangements, share frequently—whether it’s updates from the executive team or a progress report on current projects.
- **Set clear expectations, roles, and responsibilities.** Reduce duplicated efforts and cross-communication by defining individual roles and responsibilities. For example, you might be the only one with remote access to sensitive customer information; another person may liaise with IT to troubleshoot tech problems.

#### Keeping Remote Employees on Task
- Communication is key - local employees get information through osmosis - remote employees don't have that context
- Manager's job is to ensure employees make decisions effectively
- Members who typically struggle with priorities and setting goals may require more frequent check-ins, where you may need to break down their goals into sub-goals.
- By setting aside time as part of creating a community, you may find team check-ins can focus on specific agendas.
- It is important to prioritize the emotional and personal needs of team members - so make yourself available for conversations more frequently.

#### Hiring

##### Craft a work description:
An ideal job post has a few key components, but to make yours truly shine, it’s important to showcase your company, bring your underlying mission to the fore, and attract the right professionals. Beyond simply attracting talent, you want to help them quickly identify that your company is the kind they want to work for.
- Include specifics about what the work will entail. The more detail you can add, the better
- Provide more detail about your company—the culture, the vibe, what it is that you do and what you’re all about as a business
- Specify the must-have requirements, such as specific expertise level and skills you’re looking for

##### Cast a wide net:
While engaging remote freelancers can often be a quicker and smoother process than traditional hiring, to find the perfect talent for your team, you might also want to take some initiative. Posting your job and hoping for the best may not be enough—search Upwork’s global talent pool for potential hires that might be in the market for this kind of work, then approach them directly to see if they might be interested.

##### Evaluate prospects and respond quickly:
When the proposals start rolling in, create a shortlist of your top proposals and reach out to them promptly. Having a detailed list of the top qualities you’re looking for will help during this process and make it easier to quickly identify your prime talent.

##### Interview your shortlist:
When it comes to interviewing remote team members, pay close attention to how your top candidates respond during the interview setup process. Because excellent communication skills are so vital to a successful remote team dynamic, it’s helpful to see how candidates respond when setting up a video interview. From there, try a phone or video chat, and prepare some interview questions to help guide the conversation.

##### Create a solid foundation for your remote team:
Think about the entire work relationship, from vetting to communicating to paying. It’s not enough just to assemble a team of great people—you’ll want to build your remote team with a plan and give them all the resources they need to be successful. Start by asking:

- What types of projects or workflows will the team tackle?
- How will the workflow look? How will you handle prioritization, collaboration, reviews, and approvals?
- What is your plan for scalability—say when demand spikes or slows?
- What resources will you put in place to reduce dependencies and help your remote team be self-sufficient?

#### Onboarding Process
- Their specific team will get them up to speed
- New hire presentations
- If hybrid, have employees come onsite and soak in culture
- Give new employee a 'buddy'
- Get feedback so onboarding improves

#### Set your new remote team up for success.
Your project is most likely to get off to a strong start if you’ve already organized the details and resources the team will need to hit the ground running. You’ll want to plan for and provide:

- A regular team meeting: Once you make a new hire or finish assembling your remote team, you may want to facilitate a group meeting to get everyone acquainted so everyone knows who’s doing what. It also helps initiate collaboration, which is important when team members are scattered around the world.
- Clear goals and expectations: Take the time to establish clear expectations and set goals for your remote team from the very beginning. Have this all clearly defined up-front to help avoid miscommunication and potential conflicts.
- The right mix of collaboration and communication tools to keep operations on track: Find tools that align with your team’s work delivery system, whether it’s a content team editing drafts, engineers merging code, or marketers sharing calendars and analytics. Look into virtual whiteboards, document sharing like GoogleDocs, and project management software like JIRA, Basecamp or Asana.
- An advancement path: While you may start your team off on some smaller assignments, creating pathways for future advancement can be a great way to build incentive.
- Share meeting agenda for people to contribute too
- Send meeting invitation to all stakeholders
- Share out clear team role expectations and process documentation
- Added links to appropriate collaboration and communication tools in the meeting invite
- Set up separate 1:1 for individual team members
- Set up buddy system

#### Arguments in favour of a distributed team

- Unlimited access to talent:
When you can work with anyone from virtually anywhere, you suddenly have access to the best developers in the world, whether they are in Singapore or Los Angeles There are prestigious universities outside the U.S. that rival Stanford or MIT, and their graduates are often looking for opportunities beyond local job markets. Even within the U.S., there are many talented developers located far from major tech centers. By building a distributed team, you get access to the very best talent. Period.

- Mutually beneficial work relationships:
When a full-time team member leaves, that skill gap can bring critical projects to a grinding halt. With a mix of traditional and distributed talent, you can avoid this scenario altogether. Give people the opportunity to work on projects they care about and the flexibility to work when, where, and how they want, and most will call that a dream job. This is why distributed team members tend to form work relationships that stand the test of time. Compare that to a typical Silicon Valley start-up in which recruiters are constantly trying to poach your engineers.

- Lower overall cost.
As more and more businesses compete for local talent, engineers in the U.S. (and especially in the Bay Area) are commanding higher pay than similarly skilled international engineers. So for the same budget, you may be able to afford many times the engineering talent remotely than you would locally. Depending on your funding situation and your profitability goals, this may be a big decision factor. However, the axiom “you get what you pay for” applies here. Given the cost savings, we would advise that you work with only the best remote engineers, even if they are significantly more expensive than the average. You can afford the “10x engineers,” the “unicorns,” so take the opportunity!










