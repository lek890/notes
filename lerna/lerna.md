***Lerna***


***What is lerna?***

Lerna is a monorepo tool. There are other tools like bit, yarn, npm, git submodule etc for the same purpose.  
Bit was primarily build for code sharing in multirepo  codebases.

Before knowing what is lerna, we should know what is monorepo. 

Monorepo - multi package repositories - The overhead of managing multiple packages in multiple repositories lead to the concept of 
monorepo. Monorepo is a source control pattern where all the source code is kept in a single repository. such packages are called workspaces or packages. Multirepos are where parts of your project go into different repos.

Going monorepo means turning a repo into a multipackage repo. From this repo we could publish multiple 
packages. This belongs to multi-repo architecture.

When using a monorepo approach, the packages/workspaces can share the same node_modules dependencies. 

Projects like Babel, React, Angular, Ember, Meteor, Jest, and many others develop all of their packages within a single repository.

lerna and yarn workspaces gives us the ability to build libraries and apps in a single repo without forcing
us to publish to npm or other registries. These tools can find the package dependencies by analyzing 
package.json of the each projects root folder. This way, manual symlinks or npm linking can be avoided.

with one lerna command we can iterate through all or particular packages and running a series of opertaions on each package. that way it complements the yarn workspaces dependency management.

An example: We have a react app and some components of the react app are to be used by another app 
called contentful. So we need to share the components between the app and contenful. So earlier we 
kept the items for contentful and app as a same package and at times it was getting bigger and overwelhming.

So we thought about the monorepo.

Again, what was monorepo - so monorepo is a repo where multiple packages co exist. And they are not 
interwined as spaghetti code.
Basically, they contain multiple packages published from the same repository.

If you are building a library where there are multiple components that can be used on their own, then 
Bit would be a more convenient option.

If it's an application where there are modules, componets etc which can be separated out as packages, 
then lerna can come in handy.

Vue-CLI is using lerna 
ramda  uses bit


Lerna - Lerna is a tool that optimizes the workflow around managing multi-package repositories with git and npm.

Lerna can reduce the time and space requirements for numerous packages in developn ent and build environments - normally
a downside for dividing a project into many npm packages. This happens through hoisting. todo https://github.com/lerna/lerna/blob/master/doc/hoist.md

How does lerna repo look like?

```
lerna-repo
  -package.json
  packages
    -package1
      -package.json
    -package1
      -package.json
```

What can lerna do?

lerna bootstrap links all the dependencies in the repo together.
lerna publish will help publish any updated packages.

How it works?

1. Fixed/Locked mode

Fixed mode lerna projects work on a single version file. The version is kept in lerna.json file at the root of the 
project under the version key. When lerna publish is run, if a module is updated since the last time a release was made, it will be upodated to the newer version you are releasing. This means that you publish a newer version only when its 
needed.

Use this mode when you want to automatically tie all the package versions together. One drawback - change in one package
will result in all the packages having a newer version.


2. Independent mode

`lerna init --independent`

Now each package can have their own version that can be incremented independently. Set the version key in the lerna.json to run the independent mode.

configuration to note

command.bootstrap.scope: an array of globs that restricts which packages will be bootstrapped when running the lerna bootstrap command.

the packages config in lerna json is a list of globs that matching directories containing a package.json which is how
lerna knows about the leaf packages ( vs the root package.json which is intended to manage the dev dependencies and scripts for the entire repo)

Managing dev dependencies

To pull a dev dependency to the root use lerna link convert.

The above command will hoist the dependencies

Hoisting helps to 
1. all packages use the same version of the dependency
2. can keep dependecies upto date at a single place
3. Dependency installation time is reduced due to avoidal of duplication
4. Less storage is needed

Still if you need to run certain binaries inside the packages, they mneeds to be installed directly in the packagesa
as well. Example - lerna run nsp and npm run nsp inside the packages.

Todo:
walkthrough to get started.

Git hoisted dependencies


Troubleshooting

Lerna logs to lerna-debug.log on error.


references :
1. https://dev.to/giteden/5-questions-for-building-a-monorepo-4fl3
2. https://dev.to/anonimoconiglio/what-is-a-mono-repository-and-why-you-should-try-lerna-57lm - walk through on setup


todo :
1)https://dev.to/giteden/5-practical-ways-to-share-code-from-npm-to-lerna-git-submodules-and-bit-363m
 - https://medium.com/@jeffwhelpley/the-problem-with-shared-code-124a20fc3d3b -in progress
 - https://medium.com/@JonathanSaring/85c51b2d0049


