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
