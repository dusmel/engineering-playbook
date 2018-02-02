We have found that a short checklist is valuable when setting up a new production environment or preparing for a launch:

- For a new `frontend application`:
  - Are we using SSL?
- For a new `backend service`:
  - Are we following our default service [structure](https://docs.google.com/document/d/1HJnk8cqvblyW6NOGN6xkSsWVvtMmYBrumfXN145ZTL4/edit#heading=h.gdbmzxpjdr5r)?
  - Are long-running processes being run in [background jobs](https://docs.google.com/document/d/1HJnk8cqvblyW6NOGN6xkSsWVvtMmYBrumfXN145ZTL4/edit#heading=h.kr4s147l12xl)?
  - Is config stored in environment variables?
  - Are we sending logs to Stackdriver with the [epic logger](https://www.npmjs.com/package/@andela/logger) library?
  - Are we tracking errors with bugsnag?
  - Are we monitoring performance and uptime with datadog?
  - Are we monitoring new API endpoint in runscope?
  - Are we auditing all edit actions in the service? Example [here](https://docs.google.com/document/d/1HJnk8cqvblyW6NOGN6xkSsWVvtMmYBrumfXN145ZTL4/edit#heading=h.qwit764xu5h)
  - Are we backing up our production database?
  - If releasing a new version, have we run all needed regression tests at the application level?
