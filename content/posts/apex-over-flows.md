+++
title = 'Why you should always use Apex instead of Flows'
date = 2024-03-12T12:34:07-04:00
draft = true
categories = ['salesforce', 'apex', 'flows']
keywords = ['salesforce', 'apex', 'apex class', 'apex trigger', 'flows', 'record triggered flow', 'lightning flow', 'declarative', 'programmatic']
+++

Programmatic vs declarative solutions, and why programmatic always wins.

## Apex vs Flows
We've all heard the pitch. Flows are the declarative solution to automation in Salesforce. Flows are getting better with every release. Flows offer a low barrier to entry. Flows are so simple a child could make them. Flows saved my family and solved world hunger.

In most trainings, Flows are recommended as the go-to solution, with Apex as a secondary option if the logic becomes too complex. This is not a good pattern to design a system with. If given the option, an Engineer should always choose Apex over declarative solutions.

To be clear, there are use cases for Flows. If there isn’t a developer on hand, or there is a large legacy system with limited developer bandwidth, then code might not be the way to go. Also, this article is only considering record-triggered flows, as opposed to screen flows. That being said, it's important to keep in mind that any software solution needs to be able to scale. For a company hoping to provide the smoothest transition into Salesforce, it needs to be viewed as a complex system from the start and designed by engineers. Otherwise, the organization is being setup for failure. 

## The Case for Apex
When it comes down to it, engineers need to be allowed to engineer. This means using the best tools on hand, and Apex provides this. Let’s break down the reasoning.

### Handling Complex Logic
A small sales organization will probably not need much customization in Salesforce right away. Simple problems are easily solved by point-and-click tools. However, as time goes on and the organization grows, complexity compounds. Suddenly Salesforce needs to communicate with numerous systems, process large batches of records, and perform complex SOQL queries, all of which Flows struggle to deliver.

Flows are often touted as easier to build, which is certainly true if you’re not a developer, but otherwise not so. Valuable time can be wasted during a sprint trying to get a flow to handle a complex operation (such as processing many child records when a parent is updated), only to eventually be abandoned and have the processing handled in an invocable Apex action. This extra development time can be avoided if the solution is designed in Apex from the beginning.

### Maintenance
If complex processes are built out in flows then it quickly becomes difficult to maintain. Over time, flows might end up looking like this:

[image of large flow]

It might become necessary to split out functionality from flows into apex triggers instead. Now, automations are handled in two different places and the order of execution needs to be considered to ensure expected outcomes still hold. It’s also very tedious to move elements from one flow to another, in the event logic needs to be broken up or moved. With Apex, code can be easily designed to be reusable without significant  development overhead.

### Tracking Changes
Version control is essential for any engineering team, Salesforce teams included. Flows have a versioning system, but it’s far from enough. Luckily, flow metadata can be checked into a git repository and tracked from there.

What’s the problem then?

The metadata is in xml, and not human readable. The only viable way to perform a code review on a Flow is to open it in a sandbox and view it in the UI. This isn’t feasible if it was developed in a scratch org, meaning the reviewer will have to do their best to read the xml. The problem is even worse if non-Salesforce developers are reviewing the change. A Java developer should be able to trace through Apex without much issue, but stick a Flow in front of them and it will be harder to parse.

### Writing Tests
Flows offer almost the same power as Apex but with a simpler learning curve, which is usually considered a positive. There’s a huge problem with this reasoning though. Apex code requires a minimum threshold of code coverage before deploying to production. Flows by default, do not.

If a tool can make external callouts to systems, reassign records, expose data, or any other number of high impact operations, there needs to be a certain level of secuirity. Not to mention the reliability of a system that doesn't have a set of standardized tests in place. Declarative flow tests [link to release notes] have recently been released to the public, but they don’t replace the full functionalities of Apex test classes. Namely, the ability to set up complex sets of test data and compare related records. 

There is a way to enforce flow test coverage, which is something any organization with any number of complex flows should utilize.  [link to documentation on flow test coverage] However, the fact that it’s not enabled by default is a big concern. If a developer is available to write unit tests in Apex at the start of the development process, then there’s no reason not to have written the business logic in apex as well. A developer can easily break code up into testable units and mock database calls within apex, things that are more cumbersome in a flow.

## Conclusion
Flows have their place in the Salesforce ecosystem, but when it comes to picking the right tool for the job, Apex comes out on top almost everytime. Software engineering teams should be encouraged to embrace code rather than avoid it.


<br>*If you have any comments, disagree with anything above, or just want to reach out send me a message through one of my socials.*