# DoS - DDD of SAD

DoS stands for Domain-Driven Design of Software Architecture Document. Maybe the name could sound pretty stupid at
 the beginning, but if you read it slower and think about it, you will notice it is actually stupid.

## What is DoS

DoS is a software architecture that surrounds all the development and the infrastructure in the documentation.

The idea of DoS is to run all your development from a documentation source. MkDocs or Docusaurus are projects that will
 help you on that. Applying DoS, you will have to be able to fully document yourself from the root project, and you will
 be able to make all the setup of the project from and only from the documentation. When we talk about documentation, we
 are talking about technical documentation. All about business can be moved to Confluence or you can create a new domain
 inside the root documentation project for that content. Anyway, in case of you are working under Hexagonal Architecture,
 the domain of the project will have business logic, as that part of the project is the representation of your business.

- A SAD.md should be added in the Root Documentation repository in order to define not only what a SAD usually contains,
 but also the collection of practises are agreed with the project. TDD or SOLID, for example.

- Versioning for Root Documentation repository should be a rolling release. A typo on the documentation will break nothing.

- The projects' documentation will be designed in domains, a domain for each project, typically. The subdomains inside
 the project's domain will have to follow the same structure that the project's one.

- The documentation should be oriented to why and not how-to. Example: Explaining why the shopping_cart domain have some
 constrains and not how-to are they applied.

- Add images to each page. It costs you time once, avoid multiple interactions.

- An implementation of DoS will have 4 roles at least:

1. Root Documentation rol. It hosts the documentation: MkDocs, Docusaurus or a html repository if you want to.
1. Scripting rol. It will make the setup and useful commands: Make, bash, python, php...
1. Software rol. These are your software applications: MEAN, Qt, Symfony, Spring Boot, Django...
1. Virtualization rol. All the needed to virtualize the environment: Docker, Vagrant, LXC/LXD, VirtualBox...

Example of implementation:

### Example Stack

- MkDocs: Root Documentation rol
- Make: Scripting rol
- ReactJS: Software rol
- Symfony: Software rol
- Docker: Virtualization rol

### MkDocs

This is the base project. In this repository we won't host only the documentation, but all the needed to make a setup
 of the full project. This way we force the developer to go through the documentation.

### Make

It will help the user to be able to run all the need to work with the project. Examples:

- With no arguments it will show the make documentation and some suggestion: "You can run $ make install to get start!"
- install: It will perform all the clones and default configuration needed for the project. In this case it will run the
 git clone of ReactJS and Symfony's project on a specific directory in case of not existing.
- up: It will perform all the docker compose commands needed to build the documentation in MkDocs ($ mkdocs build), serve
 on local as a website, build the reactjs website, create the PHP container, redis and dependencies from Symfony and
 to serve frontend and backend on local with docker.
- down: It will kill all the docker containers.
- test:unit: It will execute all the unit tests from the project.
- test:integration: It will execute all the integration tests from the project.
- deploy-prod: Useful commands to deploy. You can use ssl certificates to manage who has the access to perform this.

The paradigm would be to execute the following commands and to have all working:

$ make install && make up && make test:unit && make test:integration

### ReactJS

Just used for the frontend of the application.

### Symfony

Just used for the backend of the application.

### Docker

Docker and Docker compose will be used to allow the developer to make a quick working setup.

## Why DoS

It's noticeable that software development is going against documentation. We write self-documented code to avoid comments
 on code. Documentation usually goes for business and for project setup.

Reasons why you should use DoS:

1. Quick developers integration to the project.
1. New developers are autonomous to get start in the project.
1. Friendly to junior developers.
1. Guarantees the setup and prevents dirty fixes that are not versioned. It works.

## When DoS

Cases when you would get an extra value using DoS:

1. Your development team has a high rotation ratio.
1. Your project is opensource, and you would like to get help from thirds.
1. Your project is a side-project, so you develop it casually.

## Other practises or architectures friendly with DoS

- RTFM, maybe it's not a practise, but hf, read it.
- TDD
- SOLID
- Clean architectures (Onion, Hexagonal...)

If you follow the good practises, your software will have a quick setup, good testing coverage, fast development of new
 features and a good project documentation.
