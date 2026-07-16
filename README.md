<<<<<<< HEAD

# Capstone Project - DevOps and Software Engineering

Reflection of the build status:

![Build Status](https://github.com/christian-schw/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)

## Introduction

This capstone project / repository was created as part of IBM's `DevOps and Software Engineering` program. A template was used - see IBM repository: https://github.com/ibm-developer-skills-network/aolwx-devops-capstone-template. Many thanks to the IBM course team as well as John Rofrano (Primary Instructor) and all the other contributors!

### Scenario

```
You have been asked by the customer account manager at your company to
develop an account microservice to keep track of the customers
on your e-commerce website. Since it is a microservice, it is expected
to have a well-formed REST API that other microservices can call.
This service initially needs to create, read, update, delete,
and list customers.

You have also been told that someone else has started on this task.
They have already developed the database model and a Python
Flask-based REST API with an endpoint to create a customer account.

Tasks that need to be completed:
- Create and execute sprint plans
- Develop a RESTful Service using Test Driven Development (TDD)
- Add Continuous Integration (CI) and Security to the Repository
- Deploy the application to Kubernetes
- Build an automated CD DevOps Pipeline
```

### Preview Images

Preview images of the project:

![planning-kanban-done](https://github.com/user-attachments/assets/c25154e1-6da6-4fd2-b55f-c18f23680953)

![17 create error handler py and implement unit tests](https://github.com/user-attachments/assets/983e8d11-0ea4-4e4a-a14a-9069fb954a04)

![21 demo create an account terminal](https://github.com/user-attachments/assets/20641e33-7061-4679-99b7-8fcf95e04dd3)

![5 part 1 implementing ci build yaml](https://github.com/user-attachments/assets/1d81de8a-2ee4-45f9-ba64-ab6bfeca1cfe)

![6 failed build - linting flake8](https://github.com/user-attachments/assets/5030173a-5b92-42ff-acca-2dbb407595fe)

![17 output after adding Flask CORS](https://github.com/user-attachments/assets/cf33236c-db81-4b42-befd-f1bd80216adb)

![13 oc implementing ibm tip](https://github.com/user-attachments/assets/23cbf314-5b27-4d34-9666-e4b9f1aed1d3)

![12 pipeline succeeded task nosetests](https://github.com/user-attachments/assets/a843103c-6296-40ce-806c-a00b4bbe7cf5)

## Course Information

Title: DevOps and Software Engineering Type: Capstone Project Course Provider: IBM

## Information about the Project

### General

- Client: Myself
- Project Goal: Demonstrate the knowledge gained in the IBM Program `DevOps and Software Engineering` with a Capstone Project.
- Number of Project Participants: 1 (Cloned repository of IBM. Developed the rest on my own)
- Time Period: December, 2024
- Industry / Area: DevOps, Software Engineering
- Role: Developer
- Languages: English
- Result: Successfully built an account microservice. Demonstrated skills and acquired new knowledge.

### Tech Stack

With regard to my role:

- GitHub (Version Control, Kanban Board, Actions, ...)
- IBM Cloud IDE (based on Theia and Container)
- Programming Language: Python
- Python Webframework: Flask
- Python Unittest Framework: nose
- Python Linting: Flake8
- Containerization: Docker
- Container Orchestration: Kubernetes / OpenShift
- Image Registry: IBM Cloud Container Registry
- CI/CD Tool: Tekton

## What I have done as Part of the Project

### Task 1 - Creating and executing Sprint Plans

The RESTful microservice is created with the help of an agile plan (Scrum). This means, the first task is the Sprint 0. The main goal of Sprint 0 is to set up the team for future delivery by creating the basic project skeleton, defining the vision and preparing the product backlog. First, a user story template was created (can be found in: `.github/ISSUE_TEMPLATE`):

![planning-storytemplate-done](https://github.com/user-attachments/assets/0e30e5a5-c3f7-4cfd-8ecf-ac187585454e)

The template provides the basis for the user stories to be created for the sprints. It uses the Gherkin Syntax. Gherkin is a simple description language with very few rules for the structured formulation of scenarios in the context of behavior-driven software development according to BDD principles. Next, the user stories were created. The titles were provided by IBM as part of the project (e.g. `Update an account in the service`) and I filled them with content. Two examples (Note: Screenshots were taken later, therefore they are already labeled and assigned to a project):

![Issue Update an account in the service](https://github.com/user-attachments/assets/720a2d0c-ae14-4fc8-bbe1-4bdb22893df4)

![Issue Containerize microservice using docker](https://github.com/user-attachments/assets/34ad0d12-b211-4876-90c5-f9d2e94912ef)

The acceptance criteria define the status of `Done`. After the user stories were completed, a GitHub project (Kanban board) was created. All issues were assigned to the `New Issues` column:

![planning-userstories-done](https://github.com/user-attachments/assets/4f044fb0-be53-48a6-8c76-629379606fc5)

The issues were then moved either to the icebox or the product backlog, depending on their priority. For example, deploying is one of the last steps, which is why it ended up in the icebox. The priorities of the issues in the backlog have also been defined. P0 is the highest priority and is therefore listed at the top. P2 is the lowest priority and is therefore listed at the bottom.

![planning-labels-done](https://github.com/user-attachments/assets/47682d10-bf71-46ca-9d49-7948e675ef11)

The following was also assigned to the issues at the end:

- An iteration field `Sprint` which has a duration of 1 week. At this point, the date is 14/12/2024. This means that the 1st sprint starts on 14/12/2024 and ends on 20/12/2024.
- The size and estimated story points were also determined. The scale (provided by IBM) is 3, 5, 8, 13 = S, M, L, XL.

The issues were moved from the product backlog to the sprint backlog and the result is as follows:

![planning-kanban-done](https://github.com/user-attachments/assets/c25154e1-6da6-4fd2-b55f-c18f23680953)

Task 1 is finished. Task 2 can be started.

### Task 2 - Developing a RESTful Service using Test Driven Development

In this task, the REST API is expanded to include additional endpoints. Test Driven Development is used in this project. This means that the tests are always written first and then the actual code that is to fulfill the tests. The following rule applies: Code coverage must be at least 95 %. First, an overview of the API guidelines. Development is based on these.

### REST API Guidelines

The REST API guidelines were specified by IBM:

![1 REST API Guidelines](https://github.com/user-attachments/assets/f249989a-8b4e-471d-9182-8f87adcf5319)

### Setting up the Development Environment

Something is missing in the set-up of the development environment: Configuring the nosetests command with additional options. This will save us typing work when carrying out unit tests in the future. The modified `setup.cfg` file:

![2 setup dev environment nosetests](https://github.com/user-attachments/assets/2587d53b-6283-463f-acec-094a47f74304)

This completes the user story for setting up the development environment and the Kanban board is updated:

![3 user story complete and next user story read an account](https://github.com/user-attachments/assets/0c58ef13-3c0d-41f3-9d47-b931633d8151)

At the same time, the next user story was defined: Read an account from service (see column `In Progress`).

### Implementing API Endpoint - Read an Account

Following the TDD approach, the test cases to be fulfilled were defined first:

![4 implement test for read an account](https://github.com/user-attachments/assets/d023a22e-d09e-4d29-bd13-7944d0335152)

The code was then written to fulfill the tests. The code coverage is more than 95%. This means that everything fits.

![5 implement read an account function](https://github.com/user-attachments/assets/6c7acbc9-0895-403d-b9fd-47ae88579864)

At the same time, the next user story was defined: Update an account from service (see column `In Progress`):

![6 user story complete and next user story update an account](https://github.com/user-attachments/assets/f1d03679-5e86-457d-9714-40a99e7e6d44)

### Implementing API Endpoint - Update an Account

Following the TDD approach, the test cases to be fulfilled were defined first:

![7 part 1 implement test for update an account](https://github.com/user-attachments/assets/a7197e1a-b82e-492f-a8bb-7b8f3a08e838)

![7 part 2 implement test for update an account](https://github.com/user-attachments/assets/4aff4c7a-fc18-464f-a98a-20f77199df76)

The code was then written to fulfill the tests. The code coverage is more than 95%. This means that everything fits.

![8 implement update an account function](https://github.com/user-attachments/assets/64b422a2-c5e6-423f-973e-614daadc71e3)

At the same time, the next user story was defined: Delete an account from service (see column `In Progress`):

![update-accounts](https://github.com/user-attachments/assets/cca9c156-b74d-44e0-abd0-37d558f24081)

### Implementing API Endpoint - Delete an Account

Following the TDD approach, the test cases to be fulfilled were defined first:

![10 implement test for delete an account](https://github.com/user-attachments/assets/b42db249-da20-481d-b4bd-d44c04c12062)

The code was then written to fulfill the tests. The code coverage is more than 95%. This means that everything fits.

![11 implement delete an account](https://github.com/user-attachments/assets/1f3cb5e7-bfb5-4093-88ca-ef689a4d0978)

At the same time, the next user story was defined: List all accounts from service (see column `In Progress`):

![12 user story complete and next user story list all accounts](https://github.com/user-attachments/assets/6fa33993-7914-4c2e-baeb-5ac1b10cb2a6)

### Implementing API Endpoint - List all Accounts

Following the TDD approach, the test cases to be fulfilled were defined first:

![13 implement test for list all accounts](https://github.com/user-attachments/assets/95e8eb2e-42d1-4605-a0a0-d6b552812ed9)

The code was then written to fulfill the tests. The code coverage is more than 95%. This means that everything fits.

![14 implement list all accounts](https://github.com/user-attachments/assets/998d8047-63cc-44bc-a940-4a95b80cb22b)

The Kanban Board has been updated:

![15 user story complete list all accounts](https://github.com/user-attachments/assets/d86a2e37-ea34-4d2b-a5c5-5604176accd7)

As an additional task, the total code coverage is being improved.

### Improving Total Code Coverage

The total code coverage is currently below 95 %. There is a lot of potential for improvement in some areas (e.g. `error_handlers.py` file):

![16 improve code coverage error handlers potencial](https://github.com/user-attachments/assets/a53dd76a-02b1-42f5-9fe8-969ec653103e)

A new test file was created to test the error handlers: `tests/test_error_handlers.py`. The test suite for error handlers was set up (setup and teardown) and the unit tests were written:

![17 create error handler py and implement unit tests](https://github.com/user-attachments/assets/8b2dfc10-1e93-4b2c-879a-3200876e2f94)

The goal was achieved: The total code coverage is now above 95 %.

![18 total code coverage above 95 percent](https://github.com/user-attachments/assets/b8a1945c-753e-46c4-8106-14d839ced6c0)

Now comes the last step of the task: Demonstrating the REST API.

### Demonstration of the REST API

First, local access to the service is enabled. The following command is used to refresh the database:

```
flask db-create
```

Then use the command below to start the service with the new database:

```
make run
```

The terminal output:

![19 start service with new database terminal](https://github.com/user-attachments/assets/cc025051-cdad-4842-9eba-7cab41f66309)

The application is started using the `Launch Application` function in the IBM Cloud IDE. A port number is also required to start the application.

![19 5 launch application in ide](https://github.com/user-attachments/assets/79199f9e-5c85-46dc-8160-46f615fb96fb)

According to the terminal, the application listens to port 5000, so port 5000 is entered / required. The output:

![20 start service with new database application](https://github.com/user-attachments/assets/7b555cc9-4129-47ba-8351-83f17ddc3a17)

The service is now running. The curl command is used to make REST calls to the implemented endpoints. The demonstration of `Create an Account` endpoint using the following command:

```
curl -i -X POST http://127.0.0.1:5000/accounts \
-H "Content-Type: application/json" \
-d '{"name":"John Doe","email":"john@doe.com","address":"123 Main St.","phone_number":"555-1212"}'
```

![21 demo create an account terminal](https://github.com/user-attachments/assets/321f47f8-2856-45cf-9c82-33d229f53998)

The demonstration of `List all Accounts` endpoint using the following command:

```
curl -i -X GET http://127.0.0.1:5000/accounts
```

![22 demo list all accounts terminal](https://github.com/user-attachments/assets/f82ccc3a-f4ee-4a3a-ae41-b8d7f8e91bf5)

The demonstration of `Read an Account` endpoint using the following command:

```
curl -i -X GET http://127.0.0.1:5000/accounts/1
```

![23 demo read an account terminal](https://github.com/user-attachments/assets/164e5ba8-9f67-4cee-b026-90a6f0dc817c)

The demonstration of `Update an Account` endpoint using the following command:

```
curl -i -X PUT http://127.0.0.1:5000/accounts/1 \
-H "Content-Type: application/json" \
-d '{"name":"John Doe","email":"john@doe.com","address":"123 Main St.","phone_number":"555-1111"}'
```

![24 demo update an account terminal](https://github.com/user-attachments/assets/4e50c627-2395-4a99-93c5-b4b319dbf5bb)

The difference: The phone number ends now with a `1` instead of `2` (`555-1112` -> `555-1111`). The demonstration of `Delete an Account` endpoint using the following command:

```
curl -i -X DELETE http://127.0.0.1:5000/accounts/1
```

![25 demo delete an account terminal](https://github.com/user-attachments/assets/04f3b818-42a1-47cb-8315-2ffdf6d36aea)

After deletion, all accounts were displayed to show that the account had actually been deleted. The list is empty, so the account has been deleted. The REST API has been finished, Sprint 1 is now complete and the next task can now be started: Task 3 - Add Continuous Integration and Security to the Repository.

### Task 3 - Adding Continuous Integration and Security to the Repository

### Additional Scenario and Planning Sprint 2

In Task 3, a new scenario was added (defined by IBM):

```
Management has been looking for ways to increase developer productivity
and has noticed that developers spend a lot of time checking
that all the tests pass before approving each pull request.
Management has decided it is time to automate this task
by implementing continuous integration (CI) using GitHub Actions.

There have also been many stories in the news about security breaches
and exploits, and management is concerned about the security of your microservice.
In an effort to be proactive, they have decided that you need to
add defensive security measures to your microservice in the
form of security headers and cross-origin resource sharing (CORS) policies.
```

Two new user stories were created to fulfill the requirements. This time, these were specified by IBM. As Sprint 1 is complete, Sprint 2 is also planned. The newly created user stories are added here. Note: And yes... the week of Sprint 1 hasn't actually passed ;-) Currently on vacation from work, so lots of time. And I want to finish the project before Christmas (day I'm writing this: 16/12/2024). The first user story - Need the Ability to Automate Continuous Integration Checks:

![1 Feature CI Checks Issue](https://github.com/user-attachments/assets/7b6026c0-dffe-45b3-908e-f31c5318824a)

The second user story - Need to Add Security Headers and CORS Policies:

![2 Feature Security Headers and CORS Issue](https://github.com/user-attachments/assets/48f34b0c-6dc2-4d98-a48f-b2798beff764)

The updated Kanban Board / Sprint Plan 2:

![3 Sprint2 Plan](https://github.com/user-attachments/assets/84f61f86-1669-48ef-8935-fa3ef88496ac)

These stories are now being implemented.

### Implementing Continuous Integration Automation

A key practice in DevOps is Continuous Integration (CI), where developers continuously integrate their code into the main branch by making frequent pull requests. To make life easier for developers, a CI pipeline is now being implemented with the help of GitHub Actions. I assign the user story in the Kanban board to myself and move it to the `In Progress` column:

![4 CI in Progress Kanban Board and assign to myself](https://github.com/user-attachments/assets/a6531cc4-8f29-417b-9a47-90959430ebf5)

The implemented YAML file (`.github/workflows/ci-build.yaml`) for the Github Actions workflow:

![5 part 1 implementing ci build yaml](https://github.com/user-attachments/assets/93a920c6-cb85-4862-89c5-7814955c8faa)

![5 part 2 implementing ci build yaml](https://github.com/user-attachments/assets/c6ef03a5-1b1f-4f2b-b935-46a9860d8fcf)

Once the workflow has been implemented, the results are visible on Github under the `Actions` tab. Here it shows that the build failed because I did not complete my Python linting:

![6 failed build - linting flake8](https://github.com/user-attachments/assets/8b3d7a88-e146-41c1-8757-82b7fcfe36eb)

Part of the CI user story is also the addition of a badge in the `README.md`, which shows the build status. This also indicates that the build has failed:

![6 part 2 failed build badge readme md](https://github.com/user-attachments/assets/d6f211db-db2b-4bd1-9a4a-d23b20a35e0b)

After I fixed the linting problems, the CI workflow I created also works:

![7 part 1 successful build](https://github.com/user-attachments/assets/fe3c7184-e108-4a46-b924-bce53dd9a4b8)

![7 part 2 passing build bage readme md](https://github.com/user-attachments/assets/f518bee9-f6de-4561-9c80-54fe82422f59)

This completes all the acceptance criteria of the CI user story and the Kanban board can be updated. The CI user story was moved to the `Done` column and at the same time the next user story (Need to Add Security Headers and CORS Policies) was moved to the `In Progress` column:

![9 move security user story to in progress](https://github.com/user-attachments/assets/42cee458-f14a-4468-be7d-1f1c12474fd3)

Time to implement the next user story.

### Implementing Security Headers and CORS Policies

The next step is to increase the security of the microservice. First, security headers are implemented with the help of Flask Talisman. Flask Talisman forces the REST API clients to use the HTTPS protocol. Following the TDD approach, the test cases to be fulfilled were defined first:

![11 part 1 implement tests security header](https://github.com/user-attachments/assets/118bf3c4-e873-4ab8-87e9-0837ea84ce75)

![11 part 2 implement tests security header](https://github.com/user-attachments/assets/6486970e-76e3-49c9-b46a-1b65291f62b1)

Regarding the options / values of the headers: More information can be found in the Flask documentation or here: https://github.com/GoogleCloudPlatform/flask-talisman To fulfill the tests, Flask Talisman dependency was installed and a Talisman instance was created after the Flask app instantiation. The result is that all our previous tests fail... at least our newly written security unit test works ;-)

![12 adding Talisman tests failed](https://github.com/user-attachments/assets/e410976c-0a4e-4a76-b2a5-b899e059335d)

The reason for the failure is that Talisman enforces HTTPS - this is good in the production system, but not in testing, as HTTP is used here. Therefore, the HTTPS enforcement is switched off in the `test_XXXX.py` files. As a result, all our tests work again (including the newly written security unit test):

![13 disable https when testing](https://github.com/user-attachments/assets/078a2ce8-56eb-4243-8713-c315abc989e1)

We can test the security headers with the following command:

```
curl -I localhost:5000
```

Before the security headers were added:

![10 output before adding Flask Talisman security headers](https://github.com/user-attachments/assets/56597257-5b1a-4151-8af0-44dc4a973a08)

After the security headers have been added:

![14 output after adding Flask Talisman security headers](https://github.com/user-attachments/assets/c0a2dbd4-75d1-47e9-8c49-356e798ff073)

The options such as X-Frame-Options or Content-Security-Policy are included - everything works as intended. The status code is 302 FOUND instead of 200 OK, as the curl command searches for HTTP by default but finds / redirects to HTTPS (see Location in header). Now the second part of the security user story: Adding CORS policies. Following the TDD approach, the test cases to be fulfilled were defined first:

![15 implement tests cors policies header](https://github.com/user-attachments/assets/f7bf6cc8-74c6-4758-9272-6cd6569635b5)

To fulfill the tests, Flask CORS dependency was installed and a CORS instance was created after the Flask app instantiation. The result: All tests were successful:

![16 implement cors policies tests successful](https://github.com/user-attachments/assets/a1946b7f-a4d8-43aa-915f-0bebb0529db1)

We can test the CORS policies with the following command:

```
curl -I localhost:5000
```

The CORS policy is now also displayed (see red marking):

![17 output after adding Flask CORS](https://github.com/user-attachments/assets/4914d865-5d36-498c-8473-1bfe8a9d2bbe)

The Security user story in the Kanban Board is moved to the `Done` column:

![18 updated kanban board moved security user story](https://github.com/user-attachments/assets/dd005a41-6bd3-4e8d-a93d-97c2d8c458ed)

This ends Sprint 2 and we can start with the next task (Deploy the Application to Kubernetes).

### Task 4 - Deploying the Application to Kubernetes

### Additional Scenario and Planning Sprint 3

In Task 4, a new scenario was added (defined by IBM):

```
Management has been very pleased with the changes you have been making.
It's now time to create a sprint plan to implement the last two stories in your Product Backlog,
which are "Containerize your microservice using Docker" and "Deploy your Docker image to Kubernetes."

One more thing. There is a new requirement.
You did such a great job automating the CI pipeline with GitHub Actions that all of the
developers seem much happier because of it. Management has decided that if a little automation
is good, then more automation would be better. They would like you to automate the deployment
to Kubernetes using Tekton once you have figured out how to do it manually.
```

One new user stories were created to fulfill the requirements. The content was specified by IBM:

![1 new user story automate deployment](https://github.com/user-attachments/assets/e4f62a78-9e54-4def-81e5-d84d989afcf3)

As Sprint 2 is complete, Sprint 3 is also planned. The newly created user story is added here. The updated Kanban Board / Sprint Plan 3:

![2 Updated Kanbanboard Sprint 3](https://github.com/user-attachments/assets/a531a5e2-742a-4aaa-a58f-358db5a7a088)

These stories are now being implemented.

### Containerizing the Microservice using Docker

The user story `Containerize microservice using Docker` was moved to the `Progress` column and assigned to me. The updated Kanban board:

![3 assign container user story to myself and progress column](https://github.com/user-attachments/assets/40dbe165-c6c1-4ee6-82f4-da2a44b80031)

An image is required to create a container. And to create an image, a Dockerfile is required. Therefore, the Dockerfile is implemented first:

![4 Create Dockerfile](https://github.com/user-attachments/assets/8d6d52a3-2895-4540-9aaa-962808c45d68)

I would not have thought of certain commands and they were specified by IBM. These include the use of the option `--no-cache-dir` and the following lines, for example:

```
RUN useradd --uid 1000 theia && chown -R theia /app
USER theia
```

The Docker image is then built and the repository is tagged as `accounts` with the following command:

```
docker build -t accounts .
```

Check whether an image has been created with the following command:

```
docker images
```

The output which looks good:

![5 check docker images](https://github.com/user-attachments/assets/17e7adc5-4105-4c6b-8337-7e5511f64c62)

A container was then created using the image with the following command:

```
docker run --rm \
    --link postgresql \
    -e DATABASE_URI=postgresql://postgres:postgres@postgresql:5432/postgres \
    -p 8080:8080 \
    accounts
```

Explanation (see Docker documentation as well):

- `--rm` = Remove container when it exists
- `--link postgresql` = Link to another container (for using PostgreSQL database)
- `-e DATABASE_URI=postgresql://postgres:postgres@postgresql:5432/postgres` = Environment variable
- `-p 8080:8080` = Publish container's port to host
- `accounts` = Name of container image

The application is started again using the `Launch Application` function from the IBM Cloud IDE. The output:

![6 docker run and launch application](https://github.com/user-attachments/assets/a2ed57e3-f045-40ce-aad2-2a4a6ff1b0f9)

![7 output application](https://github.com/user-attachments/assets/afc54626-2d93-438e-80d3-30044ca4d242)

The image is then tagged and pushed to the IBM Cloud Registry with the following command:

```
docker tag accounts us.icr.io/$SN_ICR_NAMESPACE/accounts:1
docker push us.icr.io/$SN_ICR_NAMESPACE/accounts:1
```

`$SN_ICR_NAMESPACE` is an environment variable already predefined by IBM Cloud IDE and refers to my account:

![8 output env var NAMESPACE](https://github.com/user-attachments/assets/f926fd29-8516-4b84-9bc8-f7fa410f9b70)

The push is then checked with the following command:

```
ibmcloud cr images
```

The output:

![9 check ibmcloud container registry](https://github.com/user-attachments/assets/3e79db11-5918-4962-bcbc-2cc918a03b00)

The image is there and so everything fits. The user story (`Containerize microservice using Docker`) is now fully implemented and the next user story (`Deploy your Docker image to Kubernetes`) can be tackled. The updated Kanban board:

![10 move user stories after finishing containerizing](https://github.com/user-attachments/assets/6cf6a10f-9e8e-41dd-9723-38ced1ffc1d0)

### Deploying to Kubernetes

Manifests / YAML files must be created for the user story `Deploy your Docker image to Kubernetes` so that the microservice can be deployed consistently. For the time being, the microservice is deployed manually. It will be deployed automatically in `Task 5 - Building an automated CD DevOps Pipeline`. The manifests can then be reused. The PostgreSQL database is needed for the application. OpenShift provides a number of templates for creating services. IBM has already predefined the template (file `postgresql-ephemeral-template.json`). The resources are created and deployed using the template with the following commands:

```
oc create -f postgresql-ephemeral-template.json
oc new-app postgresql-ephemeral
```

With the command `oc get all` we can see that the Postgres service is running:

![11 create postgres ephemeral and pod is running](https://github.com/user-attachments/assets/aaec18fd-5d16-40c8-a5b1-49f99cef7546)

The manifests / YAML files can now be created. IBM provides the tip that you can write the definition of the deployment in a YAML file with the help of the flags `--dry-run=client` (= ensures that nothing is actually created) and `--output=yaml`. IBM also specifies that the image created earlier should be used in the IBM Cloud Registry and three replicas. I found more information with the `--help` command:

![12 oc --help tip from ibm](https://github.com/user-attachments/assets/43aa9fd1-5990-48ec-9f6c-b13327dbb20f)

The resulting command:

```
oc create deployment accounts \
    --dry-run=client \
    --output=yaml > deploy/deployment.yaml \
    --image=us.icr.io/sn-labs-christians21/accounts:1 \
    --replicas=3
```

The output / YAML-file (`deploy/deployment.yaml`):

![13 oc implementing ibm tip](https://github.com/user-attachments/assets/f414e5e4-8aaa-480f-9ebd-510aba17b880)

After applying the deployment to the cluster:

![14 oc applying deployment yaml](https://github.com/user-attachments/assets/5e4f2a1f-42f8-4569-8946-c295fd64cce0)

To access the postgres database, according to IBM the following environment variables are needed:

- DATABASE_HOST
- DATABASE_NAME
- DATABASE_USER
- DATABASE_PASSWORD

A secret for Postgres was also created using the service template. It contains the names of the variables that are inserted into `deployment.yaml` as environment variables. The command `oc describe secret postgresql` was used to get the information. The result:

![14 oc implementing env vars secret](https://github.com/user-attachments/assets/6f11594a-e847-4e08-8398-7806e247f271)

The file `deployment.yaml` was then applied to the cluster again with the command `oc create -f deploy/deployment.yaml`. A service object was created in order to be able to use the service from outside. Here, the definition was also written with a command in a YAML file. The command:

```
oc expose deploy accounts \
   --dry-run=client \
   --output=yaml > deploy/service.yaml \
   --port=8080 \
   --type=NodePort
```

The result:

![15 expose service yaml with dry run](https://github.com/user-attachments/assets/aa0b5547-af33-4111-ad42-49848a2bfe75)

After applying the file `deploy/service.yaml` to the cluster:

![16 check service](https://github.com/user-attachments/assets/0e530045-055f-468a-a482-2c7cab603374)

A route object was created to obtain the URL of the service using the following command:

```
oc create route edge accounts --service=accounts
```

The result with the command `oc get routes` (URL is marked red):

![17 create route and copy url](https://github.com/user-attachments/assets/fac8cdea-fc84-479b-988b-e28b65baaa83)

If you enter the URL in your browser, our service will appear:

![18 url route output](https://github.com/user-attachments/assets/e125be42-6963-4497-ba0c-0b8405a6f1da)

Everything works. This means that manual deploying with Kubernetes / OpenShift is done and the Kanban board can be updated. The next user story can be implemented.

![19 update kanban board move next user story to progress](https://github.com/user-attachments/assets/6aa4e714-ead0-4512-807a-aaa7559e2dfa)

### Task 5 - Building an automated CD DevOps Pipeline

The detailed view of the last user story:

![1 user story cd pipeline](https://github.com/user-attachments/assets/29640fa1-8e4c-4f02-bd48-1c105b9169a8)

Here is an overview of the related tasks in the pipeline:

![2 overview of pipeline tasks](https://github.com/user-attachments/assets/1f34bde8-2db7-4e45-b9bf-e5ffd5aa8779)

First, a storage / workspace (`PersistentVolumeClaim`, `PVC`) was set up for the pipeline and the pipeline itself with the following commands:

```
oc create -f tekton/pvc.yaml
oc apply -f tekton/tasks.yaml
oc apply -f tekton/pipeline.yaml
```

Verification that everything has been created as intended:

![3 verifying tasks pvc and pipeline](https://github.com/user-attachments/assets/d4151c08-47f8-44b2-a89c-a2ca3d8ce4d9)

Part of the pipeline has already been implemented. The following tasks:

- init
- clone

See screenshot of `tekton/pipeline.yaml` below as well:

![4 initial pipeline tasks](https://github.com/user-attachments/assets/314fa9ed-60b6-46ef-836d-d57e3dd37e74)

The task has already been defined in the pipeline: `git-clone`. This does not have to be written in `tekton/tasks.yaml` itself, because a predefined task already exists in the Tekton Hub. This is installed in the cluster with the following command:

```
tkn hub install task git-clone
```

Verification of the installation of task `git-clone`:

![5 verifying installation git-clone](https://github.com/user-attachments/assets/aa1b9288-727b-4277-82b5-9962b3827919)

The pipeline is now started in order to see the output. The following command is used:

```
tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/christian-schw/devops-capstone-project.git" \
    -p branch="main" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    -s pipeline \
    --showlog
```

Use option `-h` for more information on passing the values for PVC etc.. The value of branch can be exchanged for test purposes (e. g. `cd-pipeline` instead of `main`). The result: the pipeline succeeded.

![6 starting pipeline and verifying succeeded](https://github.com/user-attachments/assets/1dccdb54-c27b-4c1e-a623-8023fb01ee1e)

The next task is `lint` with Flake8. This does not have to be written in `tekton/tasks.yaml` itself, because a predefined task already exists in the Tekton Hub. This is installed in the cluster with the following command:

```
tkn hub install task flake8
```

Verification of the installation of task `flake8`:

![7 verifying installation flake8 task](https://github.com/user-attachments/assets/4c5629c4-ad65-4fc0-b031-79c119dac26d)

The task is built into `tekton/pipeline.yaml`, applied with the command `oc apply -f tekton/pipeline.yaml` and the pipeline is restarted with the following command:

```
tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/christian-schw/devops-capstone-project.git" \
    -p branch="main" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    -s pipeline \
    --showlog
```

The logs:

![8 implementing lint and failed linting](https://github.com/user-attachments/assets/403f7288-7a11-4c45-8cdd-8629fb8b4ae7)

As you can see, the pipeline failed because I didn't do my linting correctly... After I fixed my linting problem, the pipeline works:

![9 fixing linting and pipeline succeeded](https://github.com/user-attachments/assets/6a19cd4d-45dd-4c9d-afc7-d6907f51192a)

The next task is `tests` with nose. This time there is no predefined task in the Tekton Hub. We have to create it ourselves. The definition is in `tekton/tasks.yaml`. The implemented code:

![10 implementing task nosetests](https://github.com/user-attachments/assets/87bc60b6-fc38-4ae1-9ec3-9e064e9a9faf)

The task was then added to the pipeline (`tekton/pipeline.yaml`):

![11 implementing pipeline task nosetests](https://github.com/user-attachments/assets/ccb21fc1-fcc6-4fd7-a8eb-5f9b57a30567)

The two changes were then added to the cluster:

```
oc apply -f tekton/tasks.yaml
oc apply -f tekton/pipeline.yaml
```

Then start the pipeline again to see the results of the `tests` task:

```
tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/christian-schw/devops-capstone-project.git" \
    -p branch="main" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    -s pipeline \
    --showlog
```

![12 pipeline succeeded task nosetests](https://github.com/user-attachments/assets/5f9296bd-aab8-45fa-9d63-3eb96ffb53f0)

Everything fits. Now the next task in the pipeline: `build`. This is required to build the image. There is a task for this in the Tekton Hub: `buildah`. It does not need to be installed separately as it has already been installed as a `ClusterTask`. ClusterTasks are not only available to a single pipeline, but to several. With the command `tkn clustertask ls` you can see all ClusterTasks and the `buildah` task is listed:

![13 clustertask buildah](https://github.com/user-attachments/assets/75f8330b-5202-4187-ac91-d57037a4094c)

The `build` task (with reference to `buildah`) was then integrated into the pipeline and the changes applied with command `oc apply -f tekton/pipeline.yaml`:

![14 part 1 implementing buildah task to pipeline](https://github.com/user-attachments/assets/49666199-b75b-4ef3-a17c-e435e55c62e3)

![14 part 2 implementing buildah task to pipeline](https://github.com/user-attachments/assets/1fd9bc4d-9984-4493-b149-8bdb6d2a6a5e)

Start the pipeline again - this time with an additional parameter (`build-image`):

```
tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/christian-schw/devops-capstone-project.git" \
    -p branch="main" \
    -p build-image="image-registry.openshift-image-registry.svc:5000/$SN_ICR_NAMESPACE/accounts:1" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    -s pipeline \
    --showlog
```

Everything works:

![15 pipeline succeeded task buildah](https://github.com/user-attachments/assets/380ea541-c55e-4db6-9252-c9dd246b32df)

Now comes the last task: `deploy`. There is a task for this in the Tekton Hub: `openshift-client`. It does not need to be installed separately as it has already been installed as a `ClusterTask`. Command `tkn clustertask ls`:

![16 clustertask openshift-client](https://github.com/user-attachments/assets/cef9e1ea-69b6-464a-b65a-0cfc6634b195)

The `deploy` task (with reference to `openshift-client`) was then integrated into the pipeline and the changes applied with command `oc apply -f tekton/pipeline.yaml`:

![17 implementing pipeline task deploy](https://github.com/user-attachments/assets/daa38367-4740-41bb-be95-bc0e507f151a)

![17 part 2 implementing pipeline task deploy](https://github.com/user-attachments/assets/c15c81e6-3769-43d7-b4bb-a6e1bf212914)

Start the pipeline again:

```
tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/christian-schw/devops-capstone-project.git" \
    -p branch="main" \
    -p build-image="image-registry.openshift-image-registry.svc:5000/$SN_ICR_NAMESPACE/accounts:1" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    -s pipeline \
    --showlog
```

The logs:

![18 pipeline succeeded task deploy](https://github.com/user-attachments/assets/dc7251d9-750f-400e-b2e9-2e519c3ca7bb)

The user story is complete, Sprint 3 is finished and the Kanban board has been updated:

![19 updated kanban board](https://github.com/user-attachments/assets/71e303ad-517b-40c0-8001-52cc54de997b)

That completes the project. If you have read this far, thank you very much for your attention! :-)

## Getting Started

### Development Environment

Important: This project is designed to be executed in the IBM Developer Skills Network Cloud IDE with OpenShift. Run the following command after cloning the repository (_Note: DO NOT run this program as a bash script. It sets environment variable and so must be sourced_):

```bash
source bin/setup.sh
```

This will install Python 3.9, make it the default, modify the bash prompt, create a Python virtual environment and activate it. After sourcing it, the prompt should look like this:

```bash
(venv) theia:project$
```

### Useful Commands

Under normal circumstances you should not have to run these commands. They are performed automatically at setup but may be useful when things go wrong:

#### Activating the Python Virtual Environment

Activate the Python 3.9 environment with:

```bash
source ~/venv/bin/activate
```

#### Installing Python Dependencies

These dependencies are installed as part of the setup process but should you need to install them again, first make sure that the Python 3.9 virtual environment is activated and then use the `make install` command:

```bash
make install
```

#### Starting the Postgres Docker Container

This project uses Postgres running in a Docker container. If for some reason the service is not available you can start it with:

```bash
make db
```

You can use the `docker ps` command to make sure that postgres is up and running.

### Project Folder Layout

The code for the microservice is contained in the `service` package. All of the test are in the `tests` folder. The code follows the **Model-View-Controller** pattern with all of the database code and business logic in the model (`models.py`), and all of the RESTful routing on the controller (`routes.py`).

```
├── service         <- microservice package
│   ├── common/     <- common log and error handlers
│   ├── config.py   <- Flask configuration object
│   ├── models.py   <- code for the persistent model
│   └── routes.py   <- code for the REST API routes
├── setup.cfg       <- tools setup config
└── tests                       <- folder for all of the tests
    ├── factories.py            <- test factories
    ├── test_cli_commands.py    <- CLI tests
    ├── test_models.py          <- model unit tests
    └── test_routes.py          <- route unit tests
```

### Data Model - Account

The Account model contains the following fields:

| Name         | Type        | Optional |
| ------------ | ----------- | -------- |
| id           | Integer     | False    |
| name         | String(64)  | False    |
| email        | String(64)  | False    |
| address      | String(256) | False    |
| phone_number | String(32)  | True     |
| date_joined  | Date        | False    |

### Local Kubernetes Development

This repo can also be used for local Kubernetes development. It is not advised that you run these commands in the Cloud IDE environment. The purpose of these commands are to simulate the Cloud IDE environment locally on your computer. At a minimum, you will need [Docker Desktop](https://www.docker.com/products/docker-desktop) installed on your computer. For the full development environment, you will also need [Visual Studio Code](https://code.visualstudio.com) with the [Remote Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension from the Visual Studio Marketplace. All of these can be installed manually by clicking on the links above or you can use a package manager like **Homebrew** on Mac of **Chocolatey** on Windows. Please only use these commands for working stand-alone on your own computer with the VSCode Remote Container environment provided.

1. Bring up a local K3D Kubernetes cluster
   ```bash
   $ make cluster
   ```
1. Install Tekton
   ```bash
   $ make tekton
   ```
1. Install the ClusterTasks that the Cloud IDE has
   ```bash
   $ make clustertasks
   ```

You can now perform Tekton development locally, just like in the Cloud IDE lab environment.

## Contact

If you have any questions, please feel free to reach out via email: christian-schwanse (at) gmx.net
