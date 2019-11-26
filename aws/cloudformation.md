so basically

the public domain bridge.moebel.de is not yet created. but if we hit the load balancer, he would route us to the bridge. so 
we found the load balancer host name from `aws > ec2 > loadbalancers > public alb > DNS name` and gave it for resolution in 
local terminal using `host dns_name_of_load_balancer`. It got resolved to an ip. 

Now that ip is added to the`/etc/hosts` in the format `ip bridge.moebel.de spell.moebel.de` so that these host names resolve 
to that ip.

Now we needed to check whether the service was up. For that we went to `ec2 > load balancers > public alb > listners >
https > edit rules`. Now we couldn't see the service spell running on the list. But there was one called enduser-frontend.searchhub.moebel
.de. 

so we started editing the cloudformation template of the searchhub project. so we added a public rule to the list
as spell.portal.market and removed the old one called searchhub.moebel.de. 
Deployment succeeded. so it was done for spell.

Now for the bridge, again added rule for public access and corrected the conditions for the different environments. 

On deploying again, there was some syntax errors. to save time we tried to validate the cloudformation xml using aws>
cloudformation > sandbox > replace template > proceeding to the validations page. if any errors are there, they could 
be seen on the proceeding pages.

Once all syntaxes are fixed, there was an issue that - since so many rules are edited, aws thinks its a new service. so 
we  deleted the stack and created a new one. 
we deleted the ecr repositories also once so that it gets recreated properly. For that go to `ECR > ur app > select the
images in the repo and run delete` . Later, delete the whole repo of the service itself. now on redeployment a new ecr repo
is created. now since the packing stage is already ran, the pack is missing. so we ran the packing stage once more.

to check the the service is running, again go to the load balancers in ec2. Go to the pub-auth-moebel.de link and go to
health check to see which url needs to be hit to health check the service. 

to see the events happening during a deployment which are configured in the cloudformation template, go to aws > cloudformation
and select the service and see events tab

in  moebel.de

sandbox is running on ec2
staging and prod always needs to there so they are run in fargate using ecs and ec2.
only prod has ecr
