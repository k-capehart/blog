+++
title = 'Why you should always use Apex instead of Flows'
date = 2024-03-12T12:34:07-04:00
draft = true
+++

We've all heard the pitch. Flows are the declarative solution to automation in Salesforce. Flows are getting better with every release and are almost just as powerful as Apex. Flows offer a lower barrier to entry to create and maintain. Flows are so simple a child could make them. Flows saved my family and solved world hunger.

I want to offer a different perspective, that may disagree with the standard guidance provided by Salesforce. In almost all training I’ve seen, Flows are always recommended as the go-to solution, with Apex as a secondary option if the logic becomes too complex. I disagree. Apex should be chosen over declarative solutions in Salesforce 100% of the time.

Now first, let me get some things out of the way because I recognize there are use cases for Flows. If you don’t have a developer on hand, or you’re building a system that will need to be maintained by non-developers then code might not be the way to go. You might also be dealing with a legacy system and not enough bandwidth to convert everything over. However, if you do find yourself leading an organization that’s moving to adopt Salesforce then I think there’s something very important to keep in mind. Salesforce offers a lot of out-of-the-box tools, but if you’re doing your job right as a sales organization then it needs to be able to scale. To provide the smoothest transition, Salesforce needs to be viewed as a complex system from the start and designed as such by engineers. Otherwise, it’s being setup for failure. 

When it comes down to it, engineers need to be allowed to engineer. This means using the best tools on hand, and Apex provides this. Let’s break down the reasoning.

Apex handles complexity better
A small sales organization will probably not need too much customization in Salesforce right away. As time goes on however, and the organization grows, complexity compounds. Suddenly Salesforce needs to communicate with numerous systems, it needs to process large batches of records, it needs to perform complex SOQL queries. If these processes are built out in flows then it quickly becomes difficult to maintain. Your flows might end up looking like this.
[image of large flow]
It might become necessary to split out some more complex functionality from flows into apex triggers instead. Now, automations are handled in two different places and the order of execution needs to be considered to ensure expected outcomes still hold.
I often hear the argument that flows are easier to build, which is certainly true if you’re not a developer, but otherwise not so. I’ve often run into scenarios where I waste valuable time during a sprint trying to get a flow to handle a complex operation (such as processing many child records when a parent is updated), only to eventually give up and move the processing to an invocable Apex action. This extra development time can be avoided if the solution is designed in Apex from the beginning.

Apex is easier to review and track changes
Version control is essential for any engineering team, Salesforce included. Flows have a versioning system, but it’s far from enough. Luckily flow metadata can be checked into a git repository and tracked from there.
What’s the problem then?
The metadata is in xml, and not human readable. The only viable way to review a Flow is to open it in a Salesforce sandbox and trace through it. This isn’t feasible if it was developed in a scratch org, meaning a code reviewer is not going to be able to trace through the logic with 100% accuracy. The problem is even worse if non-Salesforce developers are reviewing the change. A Java developer can trace through logic in Apex no problem, but stick a Flow in front of them and it might take some time to parse through the purpose.

Apex is easier to write unit tests for
One of the most often repeated benefits of Flows is that they offer almost the same power as Apex but with a simpler learning curve. There’s a huge problem with this reasoning though. Apex code requires a minimum threshold of code coverage before deploying to production. Flows by default, do not.
This is a huge security concern for me. If anyone can automate business logic, make external callouts to systems, reassign records, expose data, and any number of other operations, it needs a certain level of oversight. As already discusses, it can be difficult to review flows. Declarative flow tests [link to release notes] have recently been released to the public, but they don’t offer nearly as many features as I would want. Namely, the ability to set up complex sets of test data and compare related records. There is a way to enforce flow testing coverage from Apex tests, which is something any organization with many complex flows should utilize.  [link to documentation on flow test coverage]
[picture of setting to enable flow coverage]
However, the fact that it’s not on by default is a big concern and quite difficult to rectify after the fact if many flows have been created. If a developer is available to write unit tests in Apex at the start of the development process, then there’s no reason not to have written the business logic in apex as well. A developer can easily break code up into testable units and mock database calls within apex, things that are a little more cumbersome in a flow.

Apex code is easier to maintain


