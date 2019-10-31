***Code sharing*** 

***Part - 1***

Code sharing is not hard. but the complexity increases when there are mode modules that consume 
the shared code and when there is a high rate of change.


***Scalability challenges***

When scaling, the following can contribute to difficutly

1. Refactoring

So something changed at the shared code, say renaming a key in the data model. Now all the places
where the key is used needs to be updated assuming this is consumed in a hell lot of other places.

//okay, so how does monorepo solve this?

2. Versioning

So when a downstream depedency is changed, there are two options
1. Force all upstreams to update
2. Let the upstreams update anytime on their own.

Overheads :
#1 -  update  and  test all upstreams right   away
#2 -  maintain different versions for the upstreams to  work correctly

It would be hard trace back the time when a bug  was introduced into the system as well.

3. Testing

Integration and e2e tests can be tricky when the projects scales.

4. Reviewing 

When there are many pull requests that needs to be tracked over multiple repos the overhead is huge. 
Gatekeeping could be counter productive.

5. Consistency

Maintaing the standard consistent across the repos could be hard.

6. Deploying

When faced with multiple smaller repos problem as noted above, people could switch to one large repo.
the problem now is that many deployment tools expect exactly one configuration file. This is a problem 
when multiple deployable projects are in a repo because they all expect a config file of same configuration.

 7.Size

Large repos will be hard to work on on a daily basis, developer experience would be bad.



***So what should we do to share code efficiently at scale?***

To find a solution, lets use - 
1. A decision framework that can help to find which solution works for a situation
2. Identify specific tools and implementation details.







