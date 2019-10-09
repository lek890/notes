**Continuous Integration**

Code quality is an integral part of software development. With fast development schedules on a sprint, we need quality gates 
to ensure the code quality when n number of developers push code to the repository. This is a hard task to be done manually.
But we have continous integration for our rescue.

Using continuous integration, you can run linting, unit tests, e2e test, build the pack and even deploy. And you can configure what to run to do when - means you can configure pipeline to do certain tasks to be run only on master, any specific branch pattern or only on tags.

Gitlab supports CI/CD by default and you can configure the pipeline using .gitlab-ci.yml file. Github doesn't support CI/CD by default but nevertheless CircleCI can be used to achieve the same. CircleCI has an enormous free tier, so no problem at all.

Lets see how to configure CI/CD in github using CircleCI.

1. First lets create a sample react app. I have forked the calculator sample from react sample projects list. You can find the repo here https://github.com/lek890/calculator

2. Now you can login to circleCI using you github profile, so that you can see all your projects listed there. If you don't have a profile sign up here - https://circleci.com/signup/

3. Click on add projects in the left pane. <ADD_IMAGE> Filter the project you want to work on now and click on the Set Up Project button on the right.

4. Now, things are very easy. You need to create a `config.yml` on the root of the repo to write the CI configurations.

5. Add a folder named `.circleci` in the root of the repo and create a file named config.yml inside it. To get started, we can use the sample config.yml file that the circleCI gives 

`version: 2
jobs:
  build:
    docker:
      - image: debian:stretch

    steps:
      - checkout

      - run:
          name: Greeting
          command: echo Hello, world.

      - run:
          name: Print the Current Time
          command: date
`
6. Let's push the changes and click `Start Building` in the circleCI.
7. Now, if you got to the Workflows, you can see the list of pipelines ran. Click on succeeded button and then on the build button. Now you can see the steps in the pipeline listed. You can check what happened in each step by opening the sections.

Voila, that was easy peasy!

1. CI with gitlab
2. CI in github with CircleCI
