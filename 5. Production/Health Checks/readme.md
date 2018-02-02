
### Table of Content
***
1. [What are health checks?](#what-are-health-checks)
1. [Why use health checks?](#why-use-health-checks)
1. [How do we implement health checks?](#how-do-we-implement-health-checks)

### What are health checks?
***
We use health checks to constantly check if a service is capable of handling requests. 

### Why use health checks?
***
Depending on the design of a service, the service would be running but at the same time be incapable of handling requests. Such an error would be caused by the service being unable to connect to the database or some other connectivity problems. Health checks work to generate alerts once such an incidence occur.

### How do we implement health checks?
***
We use kubernetes health checks ([liveness and readiness probe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/)).

* kubernetes health checks make periodic HTTP 1.1 requests but our microservices receive and respond to requests using RPC. 
* In order to bridge the gap, we bundle a tiny [ lightweight golang application](https://github.com/andela/grpc-health) into the microservice docker image which would receive and respond to the health check response.   
* The golang application determines the health status of the microservice by making a HTTP 1.1 request to the microservice and responds to the health check response based on that.
 We spin a simple health service using go-lang's proto. We make the server of a particular service to export the health service. The golang application will receive health status from the simple health service. Here is the health service;
```
syntax = "proto3";
package grpc.health.v1;

message HealthCheckRequest {
  string service = 1;
}

message HealthCheckResponse {
  enum ServingStatus {
    UNKNOWN = 0;
    SERVING = 1;
    NOT_SERVING = 2;
  }
  ServingStatus status = 1;
}

service Health {
  rpc Check(HealthCheckRequest) returns (HealthCheckResponse);
}
```
We get the status of a service by calling the check method of the health service.
