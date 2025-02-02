# 3.2 User Interfaces

## 3.2.0 Introduction

User Interfaces or UI are a type of exposer components that mainly targets humans for interaction with core business layer. Unlike Communication protocols which are mainly for distributed systems. UIs are forever evolving in terms of technologies and methedologies of which humans can interact with any given system. This goes from web applications to virtual/augmented realities. Voice activated systems and more recently brain-waves activated systems.

Developing user interfaces can be much more challenging in terms of experiences. There isn't a global standard today for what an inuitive experience is. It heavily relies on culture, commonalities and so many other forever changing variables in the world today. This Standard will outline the principles and rules for building modular, maintainable and pluggable UI components. But there will be a different Standard for outlining user experiences, human interactions and the theory of inuitiveness.

This Standard also breifly highlights certain guidelines in terms of rendering choices, server, client or hybrid as is the case with the tri-nature of everything. Let's dive deeper into the principles and rules that govern building UI components.

### 3.2.0.0 Principles & Rules

Just like every other exposer component type. UIs are required to be able to map processes, results and errors to their consumers. Some of these UI components will require a test-driven approach. Some others are more like Brokers where they are just wrappers around 3rd party or native UI components. Let's talk about these principles here.

#### 3.2.0.0.0 Progress (Loading)

The most important principle in building UI component is to develop intelligence to keep the user engaged while a certain process is going. You may have seen some of these with a simple spinner or a progress bar to keep users informed at all times of what's going on behind the scenes in the system.

It's a violation of The Standard to indicate a progress of any type if nothing really is going in the background. It falls into the practice of wasting end-users time and basically lying to them about the actual status of the system. But assuming the system is actually busy working on a certain request, there are three levels of communication that can happen on an exposer component to communicate a progress. Let's discuss those in detail:

#### 3.2.0.0.0.0 Basic Progress

The basic progress approach is where you present a status with a label like "Waiting ..." or a spinner with no further indication. This is the bare minimum of progress indication and no UI should just freeze or stop their hanging while requests are being processed in the background assuming an eventual-consistency pattern is not attainable for the current business need.

Some web applications choose to show a forever progress bar at the very top of the page to indicate a progress is happening. From an experience perspective and depending on the visibilty level of these progress bars it may or may not be easy to miss by end users. Some other engineering teams have chosen to play a simple animation to keep users engaged with visual progress without any indication of the details of that progress.

#### 3.2.0.0.0.1 Remaining Progress

A bit above the bare minimum, there are indication of remaining time or remaining progress to be completed before the request is processed. An indication such as "40% remaining" or something more specific like "5 minutes remaining ..." to help end-users understand or guestimate how long time or effort is left. There are patterns where engineers would indicate how tasks are left without any indication of what these tasks are.

Sometimes a reamining progress update is as detailed as UI engineers can get. For instance, if you are downloading a file from the internet. You can't be more detailed than saying x percent of the bits remaining to be downloaded with no further details. Some game developers choose to also visualize the internet speeds and available disk space all to just keep the end-user engaged in the system. And these are all acceptable pattern in this Standard.

#### 3.2.0.0.0.2 Detailed Progress

The highest level of reporting progress is the detailed progress type. Where the UI component is fully transparent with it's consumers by reporting every step of progress. This type of progress is more common in scientific applications. Engineers in debugging mode may enable a feature where all the underlying activity in the system is visualized through the UI.

This type helps end-users understand what is happening behind the scenes but also allows them to communicate better details to support engineers to help them fix an issue if the process happens to fail. But this process isn't always preferred in terms of experience considering that some details needs to be hidden for security reasons.

In summary, selecting the right type of progress in UI is mainly dependant on the business flow, type of users who will interact with the system and several other variable which we will be discussing in The Experience Standard.

#### 3.2.0.0.1 Results

UI exposer components will report a result to indicate the completion of a certain request by end-users. Consider registering a new student in a schooling system. There are several ways to indicate the registration process have been completed successfully. Let's discuss those type of results visualization in detail here.

**3.2.0.0.1.0 Simple**

The simple indication of success is when the UI reports that the process was completed successfully without any further details. You may have seen some of these implementations for this type such as "Thank you, request submitted" or something as simple as a checkmark with a visualization of green color that indicates success in some way.

Simple results indications especially with submitted requests than retrieved data may add some more details in terms of the next course of action.

**3.2.0.0.1.1 Partial Details**

The other type of results or success indication is present end-users with partial details. An overview of the nature of the request, where it stands in terms of status and timestamps. Partial details are usually useful when it comes to providing the end-user with a "ticket number" to help end-users follow up on their requests later to inquire about the status. This pattern is very common in e-commerce applications where every purchase request may be returned with a tracking number to help customers and customer support personnel assess with the requests.

Partial detailed results can also be very helpful for the visualiztion of the success process. Especially with requests that contains multiple parts. Larger requests such as submitting an application to join a university or the likes, it may contain attachments, multiple pages of details and confidential information such as payment details or social security numbers.

**3.2.0.0.1.2 Full Details**

In some cases, it might also be preferred to report full details about the submitted request. Especially with smaller requests where it may be useful to help end-users review their requests. Some engineers prefer to display full details as an extra confirmational step before actually submitting the request. But full details can also include more than just the request details, it could include status update from the server a long with assigned point of contact or an officer from maintenance and support teams.

It's a violation of The Standard to redirect end-users at the submittal of their requests with no indication of what happened.

#### 3.2.0.0.2 Error Reports

Error reports main responsibility is to inform end-users of what happened, why it happened and what's the next course of action. Some types of error reports don't necessarily indicate any course of action which can be a poor exprience depending on the business flow. But the bare minimum in error reporting is the basic indication of the error itself with basic details. Let's talk about those types in here.

**3.2.0.0.2.0 Informational**

The bare minimum of error reports is the informational type. Indicating an error occurred and why it occurred. Something like: "Request failed. Try again" or "Request failed, contract support". There are also informational errors that are time based. Something like: "Our servers are currently experiencing a high volume of requests. Please try again later". These informational error reports are necessary to keep the end-user engaged in consuming the system in anyway.

Informational error reports are governed by the context and the type of users receiving them. In a scientific application the more details the better. For some other systems, it is important to shift the technical language of the errors to a more less technical language. For instance, we can't communicate: "Student Id cannot be null, empty or widespace". We should select a more readable language such as: "Please provide a valid student Id".

**3.2.0.0.2.1 Referencial/Implicit Actions**

The second type of error reports are the referencial type. When an erro occurs, it automatically take the action of informing the support team and returns a reference of a support ticket to end users so they can follow up on. You may see this a lot when video games fail to start, or certain applications is unable to initialize. Referencial error reports are the best when it comes certain business flows, since it takes care of all the actions, sends an email to the end user with the reference number then just follows up within a couple of days to report the status.

In general the less actions a certain system may require it's users to take after a certain failure has occurred, the better. Since end-users have already accomplished their tasks in terms of submitting requests. It becomes even more convenient if the original request is queued up such as the case with high volume enterprise systems so end-users don't have to re-submit the same data.

**3.2.0.0.2.2 Actionable**

The second type of error reports is the actionable reports. Errors that occur and provide an additional action for the users to go further in their request. For instance, there are error reports that will provide a button to try again. Or submitting an additional details request back to the engineering and support teams.

There are also reports that will provide a different route to accomplish the same task in more hybrid legacy and modernized applications. These actionable reports are more convenient than the informational reports, but they would still require their end-users to take more actions, more key strokes which leads to a certain level of inconvenience.

#### 3.2.0.0.3 Single Dependency

As is the case with any exposer component. it can only be integrated with a single dependency at all times. However, in the case of UI components, there is always the contract purity case where the UI is not supposed to be given more than what it needs in terms of data. This is where a new type of foundational-like services are implemented to ensure this pattern is enforced and all other details such as audit fields, timestamps and such are taken care of away from the UI component sight.

We will talk in detail about view services shortly as we progress talking about UI exposers.

#### 3.2.0.0.4 Anatomy

Just like the data flow in any service. We have brokers -> Services -> Exposers. UI components also form their own data flow in terms of rendering. let's take a look at the anatomy of UI exposers in this illustration:

\
![](https://user-images.githubusercontent.com/1453985/147816980-e7d30d70-c01d-49db-9bae-6c9bc11f3ff7.png)\


UI exposer components as shown above can be Bases, Components or Containers. Each one of these types has a specific responsibility to ensure the maintainbility and pluggability of the system is at it's highest scores according to The Standard. Let's discuss these three types here:

**3.2.0.0.4.0 Bases**

Base or Base Components are just like Brokers in the data flow. They are simple thin wrappers around native or 3rd party components. Their main responsibility is to abstract away the hard dependency on non-local components to allow the configurability of the system to switch to any other external or native UI components with the least effort possible.

Base components also makes it easier to mock out any external or native components behavior, and focuses the effort on ensuring the local component is performing the way its expected. We will discuss in the next chapter base components for web applications in Blazor and other technologies.

**3.2.0.0.4.1 Components**

UI Components are a hybrid between a Service and a Controller in the data pipeline. In a way components contain _some_ business logic in terms of handling interactions with certain base components. But they are also limited by integrating with one and only one view service. Components are test-driven, they require writing tests to ensure they behave as expected. But they also contain almost no iteration, selection or sequencing data logic within them.

The most important aspect about UI components is that they are at the intersection between the UI flow and the data flow. They are responsible for leveraging their data dependency (view services) and their base components to become easily pluggable into container components (like pages with routes in web applications).

**3.2.0.0.4.2 Containers**

Container components are orchestrators/aggregators of components. They are the actual route or the page end-users interact with. Containers cannot have any level of UI logic in them. They cannot leverage base components. And they may have any number of UI components as the business flow requires.

As it is the case with every category of components, containers cannot integrate with other containers. The rule applies across the board for every data or UI component of any type.

#### 3.2.0.0.5 UI Component Types

UI components come in all different shapes and sizes. The hosting environment and the type of devices that serve these components play a big role in determining the technologies and the capabilities a certain UI component may have. Let's talk about the different types of UI components in this section.

**3.2.0.0.5.0 Web Applications**

The most popular type of UI applications are web apps. Web applications are the most popular and dominant due to their ease-of-use. They require no installation of any kind. They have no dependency on the operating system running the system or the type of devices users may be using. They can run on PCs, tablets, mobile phones and even TVs and watches that support web browsing.

In the last few years, web frameworks have evolved a lot due to the aforementioned popularity. There are frameworks that allow engineers to write web applications in so many programming languages today. The web assembly evolution have also opened the door for engineers to develop even more scalable frameworks with their preferred technologies and languages.

Web applications are developed in two different types in terms of rendering. Server-side applications and client-side applications. We will discuss the advantages and disadvantages of each type in addition to the hybrid model in the next few chapters of The Standard.

**3.2.0.0.5.1 Mobile Applications**

The second most popular platform today to develop UIs is the mobile world. Developing mobile applications comes with its own set of challenges as they are heavily dependant on the operating system, the size of the phone in terms of resolution and the available native controls. Mobile applications are also always client-side apps. They are just like Desktop applications, they require to be compiled, provisioned and published to an app store so consumers can download them, install them and leverage them in their daily activities.

The biggest advantage of mobile applications is that they allow for offline interactions. Like mobile games, editing apps and streaming services with offline capabilities. But building mobile applications with web frameworks is becoming more and more popular. The universal eco-system that allows end-users to experience software the same way on their PCs, browsers and mobile applications the exact same way. This trend shall eventually allow engineers to develop systems for all different eco-systems at least cost possible.

**3.2.0.0.5.2 Other Types**

There are other types for UI components that we may not cover in our Standard. These types are like, console/terminal applications, desktop applications, video games and virtual/augmented reality software in addition to wearable devices and voice activated systems. The world of Human-Machine-Interface HMI is evolving so rapidly in the age of metaverse that we might need to create at some point special chapters for these different types.
