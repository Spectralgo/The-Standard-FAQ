# 3 Exposers

## 3.0 Introduction

Exposers are disposable components in any system that has the single responsibility of exposing your core business logic functionality by mapping its responses to a certain protocol. For instance, in RESTful communications, an API controller would be responsible for returning a `200` code for a successful response. The same thing applies to other protocols such as gRPC or SOAP or any other protocol of communication between distributed systems.

Exposer components are similar to Brokers. They are the last point of contact between the core business logic and the outside world. They are built with the intent that they will be detached from the current system at some point in time to allow the very same core logic to integrate with modern systems, protocols or interfaces.

\


![](https://user-images.githubusercontent.com/1453985/147638000-d0896f11-4117-476a-9f22-43d2b5a7d732.png)

\


## 3.0.0 Purpose

In general, exposure components main responsibility is to allow someone or something to interact with your business logic. In that core purpose a precise mapping bit by bit to every possible response from your core business logic should be communicated cautiously with the consumer to that logic. I say cautiously because sometimes certain internal issues in the system are not required to be exposed to the outside world. This mapping of responses can usually be a zero effort as the protocol and the language your code business logic communicate are the same such as the case with libraries produced to run on the system that use the same technologies or programming languages.

But there are occassions where the outside world stateless protocol doesn't necessarily match the same value of a response. In which case it becomes an exposer component responsibility to make a successful mapping both ways in and out of the system. API controllers are a great example of that. They will communicate a `4xx` issue when there's a validation exception of some type and return a deserialized JSON value if the communication was successful. But there are also more details around problem details, error codes and other levels of mapping and communication that we will discuss in upcoming chapters within this section.

### 3.0.0.0 Pure Mapping

The most important aspect of exposure components is that they are not allowed to communicate with brokers of any type. And they are not allowed to contain any form of business logic within them. By business logic here I mean no sequence of routine calls, no iteration or selection/decision making. The same way it is with brokers, they only link an existing realm with the outside realm to achieve a certain value.

## 3.0.1 Types of Exposure Components

Exposure components have three different types. Which are either communication protocols, user interfaces or simply an IO routine. Let's talk about those breifly.

### 3.0.1.0 Communication Protocols

An exposure component that is a communication protocol can vary from simple RESTful APIs, to SOAP communication or gRPC. They can also be a simple client in a library where consumers would just install the library in their projects and consume your core logic through the client APIs. These examples are all of the same type of exposure components.

The differentiator here is that a communication protocol is usually event-based. Triggered by an incoming communication and treated with a response of any kind. Communication protocols are usually for system-to-system integrations but they can be accessible and understandble by humans for testing and debugging purposes.

### 3.0.1.1 User Interfaces

Another type of exposer components are user interfaces. This can vary from Web, mobile or desktop applications including simple command lines. They mainly target end-users for communication but can be automated by other systems. Especially with command line user interfaces.In this day and age, user interfaces can also include virtual and augmented realities, metaverses and any other form of software.

There are occasions where Human-Machine-Interfaces (HMI) can also fall into that level of exposure components. For instance, the buttons on a cellphone, keyboards we use everyday and any form of hardware that can interact directly with core business logic interfaces as an exposure component. The same theory applies to the Internet of Things (IoT) components and many others where a human has to utilize a component to leverage a certain capability to their own advantage in anyway.

### 3.0.1.2 I/O Components

Some exposure components are not necessarily a system interfacing with another system. Neither they are purposed to communicate with humans. They are daemons or IO based components that do something in the background without a trigger. usually these components are time-based and they may leverage existing protocols or just simply interface directly with the core business logic which are both viable options.

## 3.0.2 Single Point of Contact

Exposure components are only allowed to communicate with one and only one service. Integrating with multiple services would turn an exposure component into either orchestration or aggregation services which are both not allowed to exist as core logic in that realm of exposure.

The single point of contact rule also ensures the ease of disposability of the exposure component itself. It ensures the integration is simple and single-purposed enough with controlled dependencies (only one) that it can be rewired to virtually any protocol at any point in time with the least cost possible.

## 3.0.3 Examples

Let's take API controllers as an example for a real-world exposure component in any given system.

```csharp
[HttpPost]
public async ValueTask<ActionResult<Student>> PostStudentAsync(Student student)
{
    try
    {
        Student registeredStudent =
            await this.studentService.RegisterStudentAsync(student);

        return Created(registeredStudent);
    }
    catch (StudentValidationException studentValidationException)
        when (studentValidationException.InnerException is AlreadyExistsStudentException)
    {
        return Conflict(studentValidationException.InnerException);
    }
    catch (StudentValidationException studentValidationException)
    {
        return BadRequest(studentValidationException.InnerException);
    }
    catch (StudentDependencyException studentDependencyException)
    {
        return InternalServerError(studentDependencyException);
    }
    catch (StudentServiceException studentServiceException)
    {
        return InternalServerError(studentServiceException);
    }
}
```

The code snippet above is for an API method that `POST` a student model into the core business logic of a schooling system (OtripleS). In a technology like ASP.NET, controllers take care of handling mapping incoming JSON request into the `Student` model so the controller can utilize that model with an integrated system.

However, you will also see the controller code tries to map every possible categorical exception into it's respective REST protocol. This is just a simple snippet to show what an exposure component may look like. But we will talk more about the rules and conditions for controllers in the next chapter in The Standard.

## 3.0.4 Summary

In summary, exposure components are very thin layer that doesn't contain any intelligence or logic in it. it is not meant to orchestrate, or call multiple core business logic services. And it only focuses on the duplex mapping aspect of the communication between one system and another.
