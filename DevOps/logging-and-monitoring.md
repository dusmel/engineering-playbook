## Available Tools and References:
***
1. [Runscope](#runscope)
2. [Bugsnag](#bugsnag)
3. [Datadog](#datadog)
4. [Stackdriver](#stackdriver-logs---gcp)
5. [Known Errors/Issues DB](#known-errorsissues-db)

Awesome and helpful [Presentation](https://docs.google.com/presentation/d/1lCgjXZUzxMxjXXaIwOQNxJRB90rmxvocHD_MpCthNVw/edit#slide=id.g1fbbe19905_0_338)

## Runscope
***
_**Getting Access:**_ Credentials available on 1password

_**Link:**_ https://www.runscope.com 
 
Runscope is a tool used by Technology for API performance testing, monitoring and debugging. Runscope currently does half-hourly monitoring of Staging and quarter-hourly monitoring of Production GET requests using defined assertions to validate response data.


> ![Runscope Overview](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/runscope-overview.png)
_Runscope Overview_

> ![Runscope Single Service Overview](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/runscope-single-service-overview.png)
_Runscope Single Service Overview_


Failed tests mean that either an assertion failed or another error like a network connection error occurred. To help in debugging, checkout the error log for the specific service. Failed tests for the individual services in staging and production are sent as slack alerts to [#downtime-staging](https://andela.slack.com/messages/downtime-staging/) and [#downtime-production](https://andela.slack.com/messages/downtime-production) respectively with a link to view result.


> ![Runscope Error Overview](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/runscope-error-view.png)
_Runscope Error View_


## Bugsnag
***
_**Getting Access:**_ Credentials available on 1password

_**Link:**_ https://app.bugsnag.com 
 
Bugsnag is used to monitor errors in applications. Error alerts point to the line of code where the error occurred further narrowing down the debugging process. These alerts are sent either the [#technology](https://andela.slack.com/messages/technology) channel or to the specific application/service Slack channel.


> ![Bugsnag Overview](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/bugsnag-overview.png)
_Bugsnag Overview_

> ![Bugsnag Error](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/bugsnag-error.png)
_Bugsnag Error_


## Datadog
***
_**Getting Access:**_ Requires invite from technology (Access can be granted by TTLs)

_**Link:**_ https://app.datadoghq.com 
 
**Reliability First Dashboard**

This dashboard allows us to have all key metrics in one place. It has metrics such as container errors, unhealthy pods, 401, 4xx and 5xx responses, Kafka errors etc. Here is the link to the public URL: https://p.datadoghq.com/sb/69dc84c46-be0bac3c1b 



**Gateway Service Monitor**

This service monitors all api-gateway endpoints on both staging and production. It reports hits, latency and error metrics.


> ![Datadog Service View](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/dd-service-view.png)
_Datadog Service View_


**Interpreting service errors**

A peak in error rate is indicative of a problem with the service. To troubleshoot this, check for the error in the service or traces page and follow up on Stackdriver logs on GCP(Google Cloud Platform). Refer to Bugsnag errors as well for more detail. Slack alerts from this monitor are sent to [#devops-alerts](https://andela.slack.com/messages/devops-alerts). 


> ![Datadog Service Error](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/dd-service-error.png)
_Datadog Service Error_


## Stackdriver Logs - GCP
***
_**Getting Access:**_ Requires invite from technology

_**Main Link:**_ https://console.cloud.google.com 

_**Staging Logs:**_ https://goo.gl/On6RBb 

_**Production logs:**_ https://goo.gl/rpzt2O  
 
 
Stackdriver provides monitoring, logging, and diagnostics which give insight into the health, performance, and availability of applications making it easier to find and fix issues. 

Log levels are classified by severity into critical, error, warning, info and debug.

Logs can be filtered by:
- time span 
- andela applications or microservices
- Google cloud services


> ![Stackdriver Overview](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/stackdriver-overview.png)
_Stackdriver Overview_


Under the select a project menu, choose [andela](https://goo.gl/rpzt2O) for production logs and microservices(https://goo.gl/On6RBb) for staging logs. Check for the error in the textPayload field of the logs.

> ![Stackdriver Choose Environment](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/stackdriver-choose-environment.png)
_Stackdriver Choose Environment_


> ![Stackdriver Error Log](https://s3.amazonaws.com/andela-wiki-assets/monitoring-and-logging/stackdriver-error-log.png)
_Stackdriver Error Log_


## Known Errors/Issues DB
***
_**Getting Access:**_ One needs to be part of the Andela Engineering team on Github

_**Link:**_ https://github.com/andela/known-errors-db 

The known errors/issues database is a repository where a log of already known errors is kept and new errors are logged. This is a great place to start when a user encounters an error in our applications or services.