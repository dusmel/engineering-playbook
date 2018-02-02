![Architecture Diagram](https://s3-us-west-2.amazonaws.com/architecture-diagram/Architecture+Diagram.png)

### Table of Content
***
1. [Introduction](#introduction)
1. [Client Applications](#client-applications)
2. [API Gateway](#api-gateway)
    1. [Scalability](#scalability)
    1. [Inter Process Communication](#inter-process-communication)
    1. [Failure Handling](#failure-handling)
3. [Microservices](#microservices)
    1. [Defining APIs](#defining-apis)
    1. [Evolving APIs](#evolving-apis)
    1. [Internal Architecture](#internal-architecture)
    1. [Instrumentation](#instrumentation)
    1. [Monitoring](#monitoring)
    1. [Deployment](#deployment)
4. [Message Broker](#message-broker)
    1. [Event Sourcing](#event-sourcing)
5. [Additional Resources](#additional-resources)

### Introduction
***
Essentially, **microservice architecture** is a method of developing software applications as a suite of independently deployable, small, modular services in which each service provides a unique business capability, runs in its own process and communicates through a well-defined, lightweight mechanism.

### Client Applications 
***
Client applications access the data & functionality provided by the services solely via a single API hosted by the API Gateway. We have a multitude of Web clients, and soon Mobile clients.

### API Gateway
***
The API Gateway is a server that is a single entry point into the system. The API Gateway encapsulates the internal system architecture and provides an API that is tailored to each client.

#### Scalability
***
It is important we build the API Gateway using a language/platform that is highly concurrent or that supports asynchronous, non-blocking I/O to ensure it can scale to handle high loads. Some options are Golang, JVM based libraries e.g Netty, Vertx, Spring Reactor etc and Node.js. We will use Golang since it’s highly concurrent, lightweight and easy to learn.

#### Inter Process Communication
***
We use gRPC framework for all synchronous communications between services. gRPC provides a lot of benefits when used in building microservices. These benefits are highlighted in their [website](http://www.grpc.io/).

Building a microservice starts with defining the interface for the service using protocol buffers. This interface is defined in a separate repo called `micro-shared` and pulled into the microservice repo as a subrepo. An example interface for a microservice can look like this:

```
syntax = "proto3";
package fellowship_roles;

service micro {
    rpc Create (RoleRequest) returns (Empty) {}
    rpc Delete (RoleIdRequest) returns (Empty) {}
    rpc Update (RoleRequest) returns (Empty) {}
    rpc Get (RoleIdRequest) returns (Role) {}
    rpc List (Empty) returns (RoleList) {}
}

enum Level {
    BOOTCAMP = 0;
    D0A_MONTH_ONE = 1;
    D0A_SIMULATIONS = 2;
    D1_DEVELOPER = 3;
    D2_DEVELOPER = 4;
    D3_DEVELOPER = 5;
    D4_DEVELOPER = 6;
}

message RoleRequest {
    int32 id = 1;
    string name = 2;
    Level level = 3;
    repeated int32 skills = 4;
}

message RoleIdRequest {
    int32 id = 1;
}

message Empty {}

message Skill {
    int32 id = 1;
    string name = 2;
    string description = 3;
    int32 score_guideline_id = 4;
}

message Role {
    int32 id = 1;
    string name = 2;
    Level level = 3;
    repeated Skill skills = 4;
    string created_at = 5;
    string updated_at = 6;
}

message RoleList {
    repeated Role roles = 1;
}
```
The above interface shows that the service exposes 5 RPC endpoints with the given inputs and outputs.

#### Failure Handling
***
The API Gateway should never block indefinitely waiting for a downstream service. Depending on the case, partial failure will be handled by:
- Returning partial results
- Returning cached results
- Implementing a [Circuit Breaker](https://en.wikipedia.org/wiki/Circuit_breaker_design_pattern) pattern

[Netflix Hystrix](https://github.com/Netflix/Hystrix) is an incredibly useful library for writing code that invokes remote services. It implements a circuit breaker pattern, which stops the client from waiting needlessly for an unresponsive service. Since Hystrix runs on the JVM, we will be using alternative Hystrix implementation with other languages. We will be using [Hystrix-Go](https://github.com/afex/hystrix-go) when building services in Golang and [HystrixJS](https://bitbucket.org/igor_sechyn/hystrixjs) when building services using Node.

### Microservices
***

#### Defining APIs
***
A service’s API is a contract between the service and its clients. Protocol buffers provides an interface definition language (IDL) to define our APIs. We will basically be using an [API‑first approach](http://www.programmableweb.com/news/how-to-design-great-apis-api-first-design-and-raml/how-to/2015/07/10) to defining services. Development of a service will begin with writing the interface definition and reviewing it with the client developers. It is only after iterating on the API definition that we will implement the service. Doing this design up front increases our chances of building a service that meets the needs of its clients. Markdown documentation can be generated from the protobuf definition.

#### Evolving APIs
***
Minor changes to a service’s API should be backward compatible and not break existing clients. The service provides default values for the missing request attributes and the clients ignore any extra response attributes. Protocol buffers is a message format that can be used to easily evolve APIs in this way.

For major changes to a service’s API, a service must support older versions of the API for some period of time while clients switch to the new version. In which case, we will need to deploy different instances such that each handle a particular version.

#### Internal Architecture
***
![Internal Architecture of a Microservice](https://s3-us-west-2.amazonaws.com/architecture-diagram/internal-architecture.png)

#### Instrumentation
***
Details coming soon...

#### Monitoring
***
Details coming soon...

#### Deployment
***
We will be deploying our microservices using [Service Instance per Container](http://microservices.io/patterns/deployment/service-per-container.html) pattern. This means each service instance runs on it’s own docker container. Since we will be deploying a lot of microservices, [Kubernetes](http://kubernetes.io/) will be used as a cluster manager to manage all our containers. We will set up Kubernetes cluster on [Google Cloud](https://cloud.google.com/) platform since they have a managed Kubernetes service in their plan. Their pricing is also far better than that provided by Amazon AWS and Microsoft Azure.

### Message Broker
***

The message broker will be used primarily as publish/subscribe messaging channel between our services. Each service publishes an event when something notable happens, such as when it updates a business entity. Other services subscribe to those events. When a microservice receives an event it can update its own business entities, or trigger a process. We will be using [Google Pub/Sub](https://cloud.google.com/pubsub/docs/) as our message broker of choice.

#### Event Sourcing
***
Read [Event sourcing and CQRS - A look at kafka](https://medium.com/@ikem/event-sourcing-and-cqrs-a-look-at-kafka-e0c1b90d17d8?source=user_profile---------1-) for an in-depth overview of event sourcing, kafka, cqrs and how they all tie together to give you a scalable microservice infrastructure. 

### Additional Resources
***
#### Microservices
- [Introduction to Microservices](https://www.nginx.com/blog/introduction-to-microservices/)
- [Migrating from a Monolith to a Microservices Architecture](https://medium.com/@briceicle/migrating-from-a-monolith-to-a-microservices-architecture-99cecf8af366)
- [Building Out an Antifragile Microservice Architecture @ Andela — Design Consideration](https://medium.com/@ikem/building-out-antifragile-microservice-andela-design-consideration-d6e03a185d6a#.nozg0ksq1)

#### gRPC
- [gRPC Website](http://www.grpc.io/)
- [gRPC Github Organisation](https://github.com/grpc/grpc)
- [Building a gRPC service with Node.js](https://codelabs.developers.google.com/codelabs/cloud-grpc/index.html#0)
- [gRPC: The Story of Microservices at Square](http://apigee.com/about/resources/webcasts/grpc-story-microservices-square)

#### Protocol Buffers
- [Protocol Buffers Website](https://developers.google.com/protocol-buffers/)
- [5 Reasons to Use Protocol Buffers](http://blog.codeclimate.com/blog/2014/06/05/choose-protocol-buffers/)
- [Schema evolution in Avro, Protocol Buffers and Thrift](https://martin.kleppmann.com/2012/12/05/schema-evolution-in-avro-protocol-buffers-thrift.html)

#### Event Sourcing
- [Building Scalable Applications Using Event Sourcing and CQRS](https://medium.com/@ikem/event-sourcing-and-cqrs-a-look-at-kafka-e0c1b90d17d8#.6zg1q7iuu)

#### Kubernetes
- [kubectl Cheat Sheet](https://kubernetes.io/docs/user-guide/kubectl-cheatsheet/)