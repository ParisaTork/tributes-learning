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

#### Set your new remote team up for success
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

- Lower overall cost:
As more and more businesses compete for local talent, engineers in the U.S. (and especially in the Bay Area) are commanding higher pay than similarly skilled international engineers. So for the same budget, you may be able to afford many times the engineering talent remotely than you would locally. Depending on your funding situation and your profitability goals, this may be a big decision factor. However, the axiom “you get what you pay for” applies here. Given the cost savings, we would advise that you work with only the best remote engineers, even if they are significantly more expensive than the average. You can afford the “10x engineers,” the “unicorns,” so take the opportunity!

#### Top tips for creating a successful distributed engineering team:
- Find the best talent, and don’t focus only on cost
- Communicate and collaborate.
- Be persistent and expect there to be a learning curve.
- Create overlapping availability for your team to be online.
- Use technology for asynchronous and synchronous communication and collaboration.
- Make remote team members feel just as valued as on-site engineers.

#### Overcoming common concerns about online work:
- “Outsourcing product development is a terrible idea.”
Distributed work done right creates a well-oiled hybrid team of employees and independent talent who get to know and respect each other. Traditional outsourcing, not so much. When you work online, your process should be the same as it would be with someone who lives down the block. Interviewing, team coordination, open communication and collaboration, and everything else that goes into building a traditional team still applies. This isn’t about finding the cheapest person and sending them tasks to check off. (You wouldn’t take this approach with local talent—why do so when working with someone remotely?) The bottom line is that if you treat distributed team members as important contributors, they will deliver better results. Remember, you aren’t simply outsourcing—you’re building relationships.

- “The process is going to be too slow.”
You might think that hiring online is too slow or tedious. In reality, it is much faster than hiring through traditional sources. On Upwork, that’s definitely the case—a quarter of our site’s job posts are filled within 24 hours, and the average time to hire is only three days. Traditional hiring can take months. With online hiring, you can enjoy the flexibility of meeting online, there is no commuting, and you can learn a lot by reading personal online profiles before you decide to contact a professional.

- “There won’t be any trust.”
The issue of trust when working with a distributed team is one of the most common—and one of the most misplaced—concerns. When it comes down to it, an on-site worker can just as easily do bad things as someone working online. Proximity does not guarantee integrity. Hiring online often provides more transparency, since you can see feedback from previous clients and more easily “test-drive”your relationship. If your ability to enforce IP rights and other legal aspects of the relationship is a concern, simply consider narrowing down the countries you work with or invest in legal services. Keep in mind that independent talent who use online marketplaces rely on great feedback, testimonials, and references to secure more work in the future. They are professionals with reputations to protect and families to support. They want to do a great job.

#### How to maintain a mutually beneficial remote working relationship

Focus on the relationship:
Hopefully by now you see the strengths of distributed team-building over traditional outsourcing. The next step is to turn the relationship into a scalable one. We have engaged some of our developers and technical talent on and off for more than five years. Our team leads have been able to maintain these mutually beneficial work relationships by following three rules of thumb:

1. Establish from the start that there is mutual interest in longer relationships
2. Take steps to make your remote team members feel valued
3. Focus on motivation and engagement

Identify mutual interest in longer relationships:
This is a relatively simple thing to do and just requires being candid and up front about your intentions and expectations. When hiring, find out if candidates are interested in building a meaningful work relationship with you and your company. Of course, in order for them to make this decision, they need to be clear on your expectations and their role in the work.Share as much information as you’re comfortable with to help them understand the project and give you an honest answer.

Make distributed team members feel valued:
Whether they are local or online, treat all of your developers as though they are equally valued players. This means:

- giving them the relevant information
- sharing with them the same successes or failures
- collaborating with them throughout the project.

Rely on your collaboration technology to make this easy, and consider giving them certain high priorities or allowances to keep them engaged.

#### Formal vs Informal Meetings
- Formal:
  - For larger groups
  - Structured agendas
  - Town hall-type capabilities
  - Plan for Q&A
  - Note taking for records
  - Voting
- Informal:
  - Google Hangouts
  - Encourage micro-communications

#### Managing a Remote Team Effectively
- Delegate and de-centralize wherever possible.
- May often want to form a number of remote teams, grouped by similar time zones, to support collaboration.
Where team members are not in similar time zones, find overlap time when you can hold your key team meetings, scrum sessions, etc.
- But some engineering teams like the site reliability group, will often use a "follow the sun" model, where they want to have global coverage by time zone, to ensure someone is available 24/7 to troubleshoot site downtime issues.

Get everyone on board, right at the start:
Get everyone together as quickly as possible right in the beginning and straighten out basics. 
- Define requirements, basic terminologies, metrics for progress and success, and objectives that need to be achieved. 
- Get everyone’s schedule beforehand so that the chances of someone missing out are minimized.
- Be as considerate as possible when accommodating time zone differences and locations but try to get the entire team together for the initial meeting. If everyone is in sync and team members are clear about their role and objectives, then you’re setting up a self-sustaining model for collaboration that will lead to minimum hassle.

Keep communication simple and natural:
The more is not the merrier when it comes to communication tools. People like simple ways to get information across. 
- By having an email client, a messaging service, a product wiki, a task board, an instant messenger, and everything under the sun to talk to team members, you’re only increasing their headache. Keep the interaction as natural as possible. Find the right tools, not all the tools. 
- Most tools offer integrations with a wide variety of other tools to create a simplified workflow. It is best to minimize setup overhead. Consider tools that fill in the holes in your process rather than create a noisy channel.

Update tasks daily:
Keep everyone in the loop. 
- When people are distributed all over the world, giving them something that can make them feel part of the team helps. This avoids creating a feeling of “us and them”. 
- A transparent process keeps communication simple and reduces the number of times someone has to be updated about task progress. Employing an efficient ticketing or issue tracking system is a good investment, in that regard. 
- A well-maintained backlog of tasks and issues organized in one central location can do wonders to create a smooth sailing ship. Think about it — would you like one platform to know where things stand or ten different small ones to piece together the puzzle? Teams have sufficient context and everyone is on the same page.

Keep subsequent meetings relevant:
- Apart from one big stand up where everyone is involved, keep subsequent meetings relevant and on point. 
- Some managers have a daily update meeting, while some do it once a week. This will vary from team to team. Depending on the project’s timeline and complexity, different teams will require varying attention.
- Only bring in team members who are concerned with that specific aspect of the project. Narrower scope of meetings, wherever possible, increase the chance to go into details about each issue and get more done. As your team increases in size, it becomes all the more important to hit the nail and focus attention on specifics.

Check in for One-on-one meetings:
- Reach out and check with team members for face-to-face meetings, periodically. Letting your team know that you’re available for a one-on-one meeting helps foster trust and reliability. Remove communication barriers wherever possible, after all the biggest resource on your team are the people. Make sure they are comfortable and on board. Motivation can be hard to sustain if you’re working alone in one corner of the world. This is why letting teammates know that they are valued and equal owners on the project is all the more important.

Smooth onboarding for new members:
- Create a system where new team members can get up to date and integrated into the team as soon as possible.
- Have a consistent set of documentation that contains details of the project, relevant requirements, basic terms and definitions, and standard guidelines. Minimizing the onboarding time adds to how quick new recruits can add productively to your project. This aspect also highlights the importance of having well-defined processes and the corresponding documentation to go with it.

Get the team together to bond:
- Nothing beats the impact and effectiveness of face-to-face communication. Fostering team spirit is easiest when team members can meet in person. While it’s not possible for all teams to afford to get everyone together routinely, any such opportunity that arises should be welcomed and taken. This leads to better engagement and collaboration.
- Having a fun activity to complement the team’s meeting helps bring everyone closer and create a sense of belonging among the team. In case face to face meetings are not possible, group video calls that are aimed at breaking the ice and team building rather than just discussing work are helpful alternatives in such scenarios.

Gather feedback and iterate on processes:
- Listen to team members for what they think can be better during remote collaboration. Whether those concerns are technical, organizational or cultural, get feedback from everyone on what processes can be improved and how they can feel more comfortable on the team. 
- Iterate on your processes like you would iterate on your project. No setup is perfect right away. It takes continuous evaluation and feedback to reach peak performance.

#### Best Practices for Managing Remote Teams Effectively

- Hire people you trust, and build trustworthy cooperation.
- Communicate frequently and sufficiently.
- Use modern tools to facilitate work and communication processes.
- Set reachable and clear goals.
- Use a transparent and fair report and control system.
- Let people know that their work matters.
- Give and gather feedback.
- Invest in traveling to have in-person meetings with the team.

#### Challenges faced by remote teams and how Agile can help overcome these issues
- Timezone issues
- Communication problems regarding code and requirements
- Availability and response time for inquires
- Lack of interaction and rapport
- Cultural differences

# Stages of an Agile Scrum Workflow
There are 3 stages to an Agile Scrum Workflow:
Sprint planning
Sprint review
Sprint retrospective

During the sprint there is also a daily meeting, scrum or stand up. They tackle a lot of the drawbacks and challenges that remote workers face.

Sprint Planning:
The planning stage lays the groundwork for the entire sprint and establishes the sprint goal. By working remotely you can get a handle of what you need to do in the next couple of weeks (depending on the sprint duration) and who you need to work with. Sprint planning can be done remotely using tools like Jira. It should also be done through video calls where all members of the team take part. This type of meeting is highly beneficial for working remotely, offering several touch base and chat opportunities that might not come up naturally. The planning stage brings together all the people working on the project, no matter where they are.

Stand Up or Scrum:
This is a recurring meeting, happening daily, for up to 15 minutes. During stand up you tell people what you did the day before, what do you plan to do today and if you have any roadblocks. This daily type of communication with the entire team offers opportunities to establish rapport and discuss important matters. From a remote perspective regular meetings, with everybody involved, give a lot of perspectives and build connections as people working individually can easily get boxed in and lose focus of the team.

Sprint Review:
In this stage the sprint goal set during planning is assessed. The entire team takes part, including the Product owner and the Scrum master. The sprint review is focused on deliverables, on the product increments, on the software itself and the actual work that was done. For remote teams this is an important stage of analysis, discussion of problems, of solutions to those problems, estimations that might have been misleading or other issues that came up in the sprint. The review meeting is very informal, builds rapport, trust and increases the level of collaboration between team members.

Sprint Retrospective:
While the sprint review focuses on deliverables and software, the sprint retrospective focuses on reflection and improvement in the teams processes and collaboration, on what went well and what went wrong. It covers the team dynamics, how can the workflow improve and what particular things should be changed. The review is all about the product and the retro is all about the processes. The lack of a physical presence can be compensated by these discussions that focus on process and continuous improvement.

#### Preparing for a Remote Position
- Prepare your work environment 
- Make availability known
- Be remote friendly in your management structure - don't be biased towards local or remote, if hybrid
- Ensuring everyone is in the loop
- Communication flows through the right channels
- Tracking progress
- Making everyone feel included as a team
- Respecting everyone’s time

#### Remote Communication Skills
- Always provide context
- Turn camera on for human connection - try to make eye contact
- Encourage small talk

#### Multiple Time Zones
- Be cognizant of employee locations and try to limit multiple time zones
- Be thoughful of everyone's work/life balance
- Set expectations
- Include employees in group emails or messages during off hours but let them know beforehand

#### Helping your team manage stress and anxiety
- Over communication can be helpful
- Look for source of anxiety
- Find root cause of anxiety and figure out solution

#### Things you can do to support yourself
- Take breaks from watching, reading, or listening to news stories, including social media. Hearing about the pandemic repeatedly can be upsetting.
- Take care of your body. Take deep breaths, stretch, or meditate. Try to eat healthy, well-balanced meals, exercise regularly, get plenty of sleep, and avoid alcohol and drugs.
- Make time to unwind. Try to do some other activities you enjoy.
- Connect with others. Talk with people you trust about your concerns and how you are feeling.
- Reduce stress in yourself and others.
- Explore Mindfulness practice that you can do at home, both individually and as a family.

#### Tips for Supporting Your Team Member
- Be extra communicative
- Monitor and manage your own anxiety
- Consider childcare and other personal challenges your people may have while young people are out of school and parents are working at home. Be flexible and aim to be accommodating of special needs.
- Show your colleagues that you care about them personally, and you are invested in this relationship with them for the long term. Everyone reacts differently to stressful situations. How you respond to an outbreak like the Coronavirus can depend on your background, the things that make you different from other people, and the community you live in.
- Share the facts about COVID-19 and understanding the actual risk to yourself and people you care about can make an outbreak less stressful.

#### Advice for Going Remote
- Think about the stepping stones
- Quickly create teams that are self contained units
- Look at your technology and processes
- Centralize and standarize things that are going to scale

#### Scaling Up for the Long Term - Key Points

Move From Centralized to More Distributed Teams:
Allow smaller teams to innovate.

Centralize and Standardize Some Functions:
Some functions and practices, like hiring, should most efficiently remain standardized, rather than burden each small team with needing to re-invent the wheel in that area.

Shift mindsets companywide:
Success with a distributed model may (and often does) start gradually with a single team or initiative. But true agility happens when all lanes merge. As your organization moves forward, encourage everyone to embrace all talent equally for the skills and capabilities they can contribute, location or employment status aside.

Help your workforce be fluid, agile, and adaptive:
It’s easier to nurture this shift when you have reliable access to who you need, when you need them. Develop an agile workforce that includes both employees and external talent. When teams need to ramp up, allocating and scaling knowledge will be more fluid.

Take a hybrid approach to collaboration and contribution:
Adaptive companies are more modular than hierarchical, with a focus on efficiency and productivity. To wit, many teams take a common hybrid approach: Employees focus on core work and the strategic part of their role that makes them experts at what they do, while independent talent handles peripheral projects, such as repeatable or highly specialized work. The key is thinking about external talent as integral contributors, not just a link in the supply chain.

#### How do you scale your distributed team?
As your team requirements increase, you will need additional developers. So how do you go from one distributed team member to two or five or ten? Follow these three tips to scale your team effectively:

1. Avoid being the hub
2. Use technology
3. Create teams within the team

Avoid being the hub:
In the beginning, you are naturally the hub through which everything passes. Any piece of information or decision that needs to be made goes through you. However, as your distributed team starts to grow, this structure becomes less and less scalable. Eventually this will slow work down, create longer decision times, and put an overwhelming amount of stress on you. This is obviously not what you want. As your team grows, you need to empower other members to make decisions, whether they are product-related or about adding new members to the team.

Use technology:
Technology is the glue that holds your team together, especially as it grows and becomes increasingly distributed over time. Whether you rely on videoconferencing, collaboration platforms, instant messaging, or software building tools, technology will enable your team to succeed. Make sure to continually evaluate new technologies as your team grows.

Create teams within the team:
At a certain point, your organization will grow so much that you need to form teams within your larger team. You might have just a handful of developers involved in a variety of projects at the beginning, but eventually some team specialization will be required. For example, you may need a separate group to focus on front-end development and another one to focus on back-end development. A good rule of thumb is that if more than three people work on a specific function or area, it might be a good idea to formalize that group as a team. Setting up official teams is great because they can own their respective areas—and that allows you to scale without pulling your hair out.

