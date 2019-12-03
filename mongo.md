todo - december


i installed something inside docker container, does it persisit?
how do i install some software using docker compose file


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
                { role: "dbAdmin",   db: "test" },
                { role: "readWrite", db: "test" }
             ]
})

db.updateUser("admin",{roles : ["userAdminAnyDatabase","userAdmin","readWrite","dbAdmin","clusterAdmin","readWriteAnyDatabase","dbAdminAnyDatabase"]});

https://stackoverflow.com/questions/34559557/how-to-enable-authentication-on-mongodb-through-docker

