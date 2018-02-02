We have found that a short checklist is valuable when setting up a new production environment or preparing for a launch:

- Are we following our default service [structure](https://docs.google.com/document/d/1HJnk8cqvblyW6NOGN6xkSsWVvtMmYBrumfXN145ZTL4/edit#heading=h.gdbmzxpjdr5r)?
- Are long-running processes being run in [background jobs](https://docs.google.com/document/d/1HJnk8cqvblyW6NOGN6xkSsWVvtMmYBrumfXN145ZTL4/edit#heading=h.kr4s147l12xl)?
- Are we using SSL for Web applications?
- Is config stored in environment variables?
- Are we sending logs to Stackdriver with the [epic logger](https://www.npmjs.com/package/@andela/logger)?
- Are we tracking errors with bugsnag?
- Are we monitoring performance and uptime with datadog?
- Are we auditing all edit actions in the service? Example [here](https://docs.google.com/document/d/1HJnk8cqvblyW6NOGN6xkSsWVvtMmYBrumfXN145ZTL4/edit#heading=h.qwit764xu5h)
- Are we backing up our production database? See Heroku PGBackups.
