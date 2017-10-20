
-bash-4.2$ hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - ernest  usa             0 2017-10-20 09:26 /user/ernest
drwxrwxrwx   - mapred  hadoop          0 2017-10-20 09:23 /user/history
drwxrwxr-t   - hive    hive            0 2017-10-20 09:23 /user/hive
drwxrwxr-x   - hue     hue             0 2017-10-20 09:24 /user/hue
drwxrwxr-x   - oozie   oozie           0 2017-10-20 09:24 /user/oozie
drwxr-xr-x   - siwicki emea            0 2017-10-20 09:26 /user/siwicki


[root@ip-172-31-19-20 lib]# curl -u admin:admin "http://localhost:7180/api/v14/hosts"
{
  "items" : [ {
    "hostId" : "b5735928-a802-4a60-a198-e70c05fad6f3",
    "ipAddress" : "172.31.16.124",
    "hostname" : "ip-172-31-16-124.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-19-20.eu-central-1.compute.internal:7180/cmf/hostRedirect/b5735928-a802-4a60-a198-e70c05fad6f3",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "4ca3ce45-5229-4ae5-8e7a-7d275ca06c8c",
    "ipAddress" : "172.31.19.20",
    "hostname" : "ip-172-31-19-20.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-19-20.eu-central-1.compute.internal:7180/cmf/hostRedirect/4ca3ce45-5229-4ae5-8e7a-7d275ca06c8c",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "65876290-4bd1-4899-813c-723f83f38c21",
    "ipAddress" : "172.31.21.148",
    "hostname" : "ip-172-31-21-148.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-19-20.eu-central-1.compute.internal:7180/cmf/hostRedirect/65876290-4bd1-4899-813c-723f83f38c21",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "3076ecfa-1efe-4414-871b-ef7e5836008d",
    "ipAddress" : "172.31.24.153",
    "hostname" : "ip-172-31-24-153.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-19-20.eu-central-1.compute.internal:7180/cmf/hostRedirect/3076ecfa-1efe-4414-871b-ef7e5836008d",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "f3b842f3-79a6-4284-abb7-3ea49804ce21",
    "ipAddress" : "172.31.31.254",
    "hostname" : "ip-172-31-31-254.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-19-20.eu-central-1.compute.internal:7180/cmf/hostRedirect/f3b842f3-79a6-4284-abb7-3ea49804ce21",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  } ]
}[root@ip-172-31-19-20 lib]
