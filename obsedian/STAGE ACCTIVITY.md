
The following details will be given in the JIRA as follow:

**Component:** MariaDB / Percona / Aerospike / Drove / Nixy / RMQ / 
**Version:** (-specific version of that respective component-)  
**Cluster Pattern:** stg-corecertified / -critical 
here; 
	stg-corecertified is an stage environment 
	stg-critical is an prod-mirror (pre-production) or feature -environment 

**User_Creation:** Yes /No
here;
	Yes - creds are already created, we need to ask the dev. for the same
	Np - need to create the username by given some relavant name and for password create a random pass. on terminal: `pwgen -1 8 | tr "\n" "$"  && pwgen -1 8`

**shard_names:** 

Rules:
1 User - 2 Shards - 50 CONNECTIONS
	*(depends on the services)*

### DataBase Creation (Shard creation)

> ssh to the traffic taking node from the core-certified , preferable Third node
> sudo su
> mysql -u stgsresd -p
> 	we do this basically to perform the activity being the superadmin here
> Enter the password
> 
> Follow the following example of commands to run;
```
CREATE DATABASE nimbus_shard_1;
CREATE DATABASE nimbus_shard_2;
 
create user plutus_rw@% identified by 'pohki4Oh#@321' WITH MAX_USER_CONNECTIONS 50;
 
GRANT SELECT, INSERT, UPDATE, CREATE, ALTER, DELETE, DROP ON nimbus_shard_1.* TO mf_connector_user_admin@%;
GRANT SELECT, INSERT, UPDATE, CREATE, ALTER, DELETE, DROP ON nimbus_shard_2.* TO mf_connector_user_admin@%;
```
> Verify if the shards are being created using the following queries;
> 	`SHOW DATABASES;`
> 	Login with the user we have created and then run `SHOW DATABASES;`and check me the shards that are created are visible in the list.


### MIGRATION + DB CREATION

```
mysql> CREATE DATABASE bbps_db_1;
mysql> CREATE DATABASE bbps_db_2;

mysql> create user `bbps_db_rw`@`%` identified by 'aeghai7@looJu3eez' WITH MAX_USER_CONNECTIONS 50;
mysql> GRANT SELECT, INSERT, UPDATE, CREATE, ALTER, DELETE, DROP ON `bbps_db_1`.* TO `bbps_db_rw`@`%`;
mysql> GRANT SELECT, INSERT, UPDATE, CREATE, ALTER, DELETE, DROP ON `bbps_db_2`.* TO `bbps_db_rw`@`%`;

mysql> SHOW DATABASES;

mysqldump -u stgsresd -p --set-gtid-purged=OFF bbps_db_1 > bbps_db_1.sql
ls -lrth
mysqldump -u stgsresd -p --set-gtid-purged=OFF bbps_db_2 > bbps_db_2.sql
ls -lrth
python3 -m http.server

//Note 
//diff type of backup - mysqldump



ssh stg-corecertifiedpxc801.phonepe.nb6
wget [http://stg-perconapp801.phonepe.nb6:8000/bbps_db_1.sql](http://stg-perconapp801.phonepe.nb6:8000/bbps_db_1.sql)
wget [http://stg-perconapp801.phonepe.nb6:8000/bbps_db_2.sql](http://stg-perconapp801.phonepe.nb6:8000/bbps_db_2.sql)
mysql -u stgsresd -p bbps_db_1 < /bbps_db_1.sql
mysql -u stgsresd -p bbps_db_2 < /bbps_db_2.sql
```


### AEROSPIKE: NAMESPACE CREATION
> rollout service 
> ssh stg-corecertified / -critical  aerospike 
> 
> check the service running or not `
```
> systemctl status aerospike`
```
> 
> edit the main configuration 
```
> `vim /etc/aerospike/aerospike.conf`
```
> 
> add the namespace 

```
namespace merchantservice {
    memory-size 2G
    replication-factor 2
    default-ttl 1
    nsup-period 120
    high-water-disk-pct 60
    high-water-memory-pct 70
    stop-writes-pct 90
    storage-engine device {
        file /var/lib/aerospike/merchantservice.dat
        filesize 8G
        data-in-memory false
        write-block-size 128K
        defrag-lwm-pct 50
        defrag-startup-minimum 10
    }
}
```

> add namespace stanza in the XDR stnaza as per requirement
> 
```
> wq!
```
> 
> check the service running or not `
```
> systemctl status aerospike
```
> 
> restart the service running or not `
```
> systemctl restart aerospike
```
> 
> check the service running or not `
```
> systemctl status aerospike
```
> 
> debug if anything failed:
> 
> push the changed to the git by following the following steps


Now we need to create the user for this particular ns, use the below commands:
```
asadm -U .......... -P
Password: 

Admin > enable 
Admin+> show roles
Admin+> show users
Admin+> manage acl create role iris_rw priv read-write;
Admin+> manage acl grant role iris_rw priv data-admin;
Admin+> manage acl create user iris_rw password Zoomar4kiethiex1 role iris_rw;

```


//salt 
//why using salt
//what are master minion 
//how the gitlab
//and does gitlav is used for

```
1037  cd aerospike-formula-configs/nb/nb6/stg-corecertifiedaerospike80x
1038  git checkout -b STGSHARED-733
1039  vi cluster.TEMPLATE
1040  git diff
1041  git add .
1042  git status
1043  git commit -m "STGSHARED-733|Aerospike Namespace Modification"
1044  git push origin STGSHARED-733
```







