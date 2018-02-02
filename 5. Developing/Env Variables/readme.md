 
During the course of software development, there will come a time where you may need to create a new environment variable.

In development environment using the development toolkit [https://github.com/andela/development-toolkit]:

- Create a new branch
- Add environment variable key-value (set environment) in respective service’s .env file in the [development toolkit env_file directory](https://github.com/andela/development-toolkit/tree/master/env_files) 
- Submit a PR (adding a member of the devops team as reviewer) with your change to be merged by the devops team


In staging or production environment:

- Create a new branch on the micro-deployment-scripts repository.
Add environment variable following the instructions in the [micro-deployment-script’s readme](https://github.com/andela/micro-deployment-scripts/blob/develop/README.md)
- Submit PR with your change (PR would only be accepted if environment variable exists in development toolkit env file for the project. Add the link to the PR in the comment )  to be merged by the devops team
If environment variable is a secret value:

  - When a new value for a new environment variable :
    - Ensure the value is saved in lastpass or 1password.
    - State the location of the value in lastpass in the pull request comment.
  - When a new value for an existing environment variable :
    - Ensure the value is updated in lastpass.
    - Submit a ticket in DevOps PT Board with concrete details including the NAME and location of value in lastpass.
