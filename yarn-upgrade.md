Yarn upgrade and package.json

Why doesn't yarn upgrade update the package.json?

When we run upgrade, the way the upgrade happens depends on the way the package version is specified in the package.json.
Most probably you might see that the yarn lock got updaded when the upgrade command was executed.

Let's dig deeper

[Advanced version ranges](https://classic.yarnpkg.com/en/docs/dependency-versions#toc-advanced-version-ranges) of yarn says 
how verisons can be specified in package json.

###Caret ranges

default verison syntax when you run `yarn add package`
Look out for the first non zero digit in a version and allow changes unless the upgrade changes that non zero digit

^3.1.5 allows >=3.1.5 and <4.0.0
^0.3.1 allows >=0.1.0 and < 0.2.0
^0.0.2 allows >=0.0.2 and <0.0.3

###Hyphen ranges 

example : 

2.0.0 - 3.0.0  expands to >=2.0.0 and <=3.0.0
2.0 - 3 expands to >=0.2.0 and <=3.0.0

###X-ranges

X, x or * can be used

* means any version and expands to >=0.0.0
4.x means match major versions and expands to >=4.0.0 and <3.0.0 
3.1.x means match major and minor verisons and expands to >=3.1.0 and <3.2.0

###Tilde ranges

~3 means allow allow minor versions and expands to >=3.0.0 and <4.0.0
~3.2 means allow patch changes and expands to >=3.2.0 and <3.3.0
~3.2.1 means allow patch changes from the patch specified and expands to >=3.2.1 and <3.3.0


