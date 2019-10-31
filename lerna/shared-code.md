***Code sharing***

Code sharing is not hard. but the complexity increases when there are mode modules that consume 
the shared code and when there is a high rate of change.


*** Scalability challenges ***

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



