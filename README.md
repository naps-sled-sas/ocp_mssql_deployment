# What is this?
- An OpenShift template for deploying a containerized deployment of Microsoft SQLServer

- This will deploy the following resources
    - A SQLServer 2019 pod with 1gb PVC
    - A secret
    - A service

# How to use?
0) Deploy a Windows server VM with [SQLServer Management Studio (SSMS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16) installed. This is optional just needed if you actually want to show a DB connection.

1) Create a namespae if you don't have an existing one from step 0
```
oc new-project ms-sqlserver2019
```

2) Deploy the resources
```
oc apply -k base
```

3) At this point it's available via pod networking on the service like any other DB pod. You can connect to this with SSMS with a VM on the pod network or an external VM if you edit the service to expose a node port. The login user is "sa" and the password in the created secret. You will need to check the "Trust server certificate" option.
