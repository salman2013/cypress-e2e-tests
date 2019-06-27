# cypress-e2e-tests

This repo contains e2e tests written in Cypress for different edX applications

---
---

## Introduction to Cypress

Cypress is a relatilvely new automated tests tool which is gaining popularity at a very rapid pace

Here is the home page for Cypress if someone wants to look it up

<https://www.cypress.io/>

Cypress has very strong documentation so a new comer could find most of the information from their own site

<https://docs.cypress.io/guides/overview/why-cypress.html#In-a-nutshell>

Also as a starting point it would be good to go through thes tutorial videos

<https://docs.cypress.io/examples/examples/tutorials.html#Best-Practices>

---
---

## E2E Tests Repo

This repo is meant to contain multiple projects, for now there are two projects

MIT Journals (Deprecated)
Enterprise Admin Portals (Active)

With time we will add more projects in the repo

---
---

## Protocols for Test Design

We don't yet have well defined protocols for writing Cypress tests for edX application, so this work was mostly experimental

The first project was MIT Journals, in this project following protocols were followed

* Page Object model was not used because Cypress site does not recommend.

* es6 Arrow functions are used in this project.

* Cypress Commands and customized utility functions are used to minimize code repetition

The tests for Journals and helper files are present in following path

<https://github.com/edx/cypress-e2e-tests/tree/master/cypress/integration/journals>

---

In the second project a slightly different approach is used

* Page Object model is used inspite of what Cypress site says, it increases redability of code and is much easier to manage

* Instead of using arrow functions traditional named functions are used, this is done to to be able to use **this**, which is not working with arrow functions

* Cypress commands and helper functions are still utilized

The tests for Enterprise Admin Portal are present in following path

<https://github.com/edx/cypress-e2e-tests/tree/master/cypress/integration/admin_portal>

To manage multiple projects customized config files are used so user is able to run any project without making any change in the code

Config files for both these projects are placed here

<https://github.com/edx/cypress-e2e-tests/tree/master/config>

---
---

## Test Setup

### Installations

You need to have Node.js installed before using Cypress.

For rest of the installations move to project folder in command prompt and type

`npm install`

which will install Cypress and other supporting tools

---

### Environment Varaibles

Following Environment Vars should be set before running the tests

`CYPRESS_EDX_NORMAL_USER_EMAIL`

`CYPRESS_EDX_NORMAL_USER_PASSWORD`

_Note_: The above are credentials for a normal edX user who does not have access to admin portal

`CYPRESS_ADMIN_PORTAL_USER_EMAIL`

`CYPRESS_ADMIN_PORTAL_USER_PASSWORD`

_Note_: The above are credentials for a admin portal valid user

---

### Run Tests

To run admin portal tests in interactive mode use following command

`npm run cy:open_admin_portal`

T run admin portal tests in normal mode use following command

`npm run cy:run_admin_portal`

---

### Using ES LInt

ESLint is also setup in the repo, you can use it by typing following command in terminal

`npm run lint`

---

### Running Tests in Docker

Docker setup is also available for those who want to run the tests without doing any installations

To run the tests in Docker

* Provide the values for environment variables in the env_vars.env
* Type `docker-compose up` in terminal
