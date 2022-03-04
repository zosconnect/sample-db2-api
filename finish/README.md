<!---
 Copyright IBM Corp. 2021
-->
# EmployeesApi
The `finish` project allows users to create, read, update, and delete employees in the Db2 sample employee table (DSN8B10.EMP).

## Configuration
To be able to connect to your Db2 instance in which you have the employee table sample installed you must first configure a `<zosconnect_db2Connection />` in this project. Create a file named `db2.xml` in the directory `./src/main/liberty/config`. Copy and customize the following contents into this file.
```
<server>
    <featureManager>
        <!-- This enables the db2 functionality -->
        <feature>zosconnect:db2-1.0</feature>
    </featureManager>

    <!-- This is the SAF user and password which will be used to connect to Db2 -->
    <zosconnect_credential userName="${DB2_USERNAME}" password="${DB2_PASSWORD}" id="commonCredentials"/>

    <!-- This is the host and port for the connection which will be used to connect to Db2 -->
    <zosconnect_db2Connection id="db2Conn" host="${DB2_HOST}" port="${DB2_PORT}" credentialRef="commonCredentials"/> 
</server>
```

The variables (e.g. `${DB2_USERNAME}`) values must be provided as environment variables when the designer image is started. The provided environment variable values will then be substituted in when the connection is used.

## Contents
The operations and paths available in the API are as follows:
- GET | PUT | DELETE : /employees/{id}
- GET | POST : /employees

Review `finish/src/main/api/openapi.yaml` for the full API description.