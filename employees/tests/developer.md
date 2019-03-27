# Technical Test

The purpose of this exercise is for us to get a sense of how you would approach designing and implementing a simple MESG Service before we get you in for an interview. We’ve tried to avoid tricky algorithmic tests in favor of something that shows how you would organize a codebase and solve problems.

There is no time limit, but we expect most applicants to spend roughly 2-3 hours working on the test. Once complete, please share your GitHub repository.

Feel free to explore the documentation of MESG and get inspiration from existing repositories.

- https://docs.mesg.com
- https://github.com/mesg-foundation

# Requirements

You will need to create a MESG Service in Go.

The Service should work with the `mesg-core service test` command and should have the following functionalities:

## Emit events

The service should expose a HTTP server that listens for POST requests.

When receiving a request, the service should emit an event with key `onRequest` to MESG Core, with the following data:
- `date`: the date and time of the request
- `id`: an unique id of the request
- `body`: the body of the request


## Task that executes a HTTP request

The service should have a task with key `execute` that executes a HTTP POST request.

This task should accept the following as an input:
- `url`: the URL of the request
- `body`: the body of the request

And as outputs:
- `success` with the following data:
  - `statusCode`: the status code of the response
  - `body`: the body of the response

- `error` with the following data:
  - `message`: the error's message


## [Bonus] Task that executes multiple HTTP POST requests

As a bonus, the service could have a task with key `batchExecute` that executes multiple HTTP POST requests on multiple URLs.

You are free to define the inputs and outputs of this task.

# Deliverables
Please submit the following deliverables to jobs@mesg.com:
- A GitHub repository link containing the source code
- [Optional] Tell us what you thought of the test and the documentation, and how long it took you to complete
