## Mongo - shell commands

1. Find field

db.collection(query, projection)

```
db.user_auth.find(
{email : "consumer_pepcogf_user@tfbnw.net"},
{_id: 1,newsletterPermission: 1})
.pretty()

```

2. update and return new field

db.collection.findOneAndUpdate(
filter,
update,
options
)

```
db.user_auth.findOneAndUpdate(
{email : "consumer_pepcogf_user@tfbnw.net"},
{$set : { newsletterPermission : false }},
{
projection : { newsletterPermission : 1},
returnNewDocument : true
}
)
```

Mongo db
/usr/local/etc/mongod.conf

databases are
/usr/local/var/mongodb/

You have to change your mongod.conf file to disable authorization before creating such admin user

security:
authorization: disabled
After that, restart the mongod service and open mongodb shell to create the admin user

use admin
db.createUser({user:"RootAdmin",pwd:"blahblah",roles:["root"]})

db.createUser({
user: 'test_user',
pwd: 'test',
roles: [
{ role: "userAdmin", db: "test" },
{ role: "dbAdmin", db: "test" },
{ role: "readWrite", db: "test" }
]
})

db.updateUser("admin",{roles : ["userAdminAnyDatabase","userAdmin","readWrite","dbAdmin","clusterAdmin","readWriteAnyDatabase","dbAdminAnyDatabase"]});

https://stackoverflow.com/questions/34559557/how-to-enable-authentication-on-mongodb-through-docker
