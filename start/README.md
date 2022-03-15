<!---
 Copyright IBM Corp. 2021
-->
# EmployeesApi
The `start` project can be enhanced to allow users to create, read, update, and delete employees in the Db2 sample employee table (DSN8B10.EMP).

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

## Development
You will need to create z/OS assets for the Db2 native REST services you want to use. These z/OS assets will then need to mapped into your API. You will then need to define the responses and map each response case. The `Test` button can be used to test your API incrementally as you develop it. 

See the `Create your first z/OS Connect API` topic in the IBM documentation for more details on using the IBM z/OS Connect Designer.

## Contents
The operations and paths that can be created in the API are as follows:
- GET | PUT | DELETE : /employees/{id}
- GET | POST : /employees

Review `start/src/main/api/openapi.yaml` for the full API description.