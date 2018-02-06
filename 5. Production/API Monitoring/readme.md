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
