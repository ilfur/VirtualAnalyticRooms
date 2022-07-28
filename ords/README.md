<!--- app-name: Oracle ORDS -->

## Oracle REST Data Services 
# Description
This container will start a server instance with ORDS (Oracle Rest Data Services) and APEX (Oracle Application Express). At startup the container will install or upgrade ORDS and APEX in the specified database. The target default database pool for ORDS is specified in a file (conn_string.txt) that the container reads at startup. The database connection string is necessary to install/upgrade the database components. The file is deleted during the startup process. Although the container is intended to be removed when the container stops the ORDS and APEX database components will remain in the database available for other ORDS instances.

NOTE: This image is for testing purposes only, as such it is unsupported and should not to be used in a production environment.

A mid-tier Java application, ORDS provides a Database Management REST API, SQL Developer Web, a PL/SQL Gateway, SODA for REST, and the ability to publish RESTful Web Services for interacting with the data and stored procedures in your Oracle Database. See https://www.oracle.com/rest for more information.

Oracle Application Express (APEX) is a low-code development platform that enables you to build scalable, secure enterprise apps, with world-class features, that can be deployed anywhere. See https://apex.oracle.com/ for more information.

# Version matrix
Each image uses Oracle Linux with a specific version of ORDS and APEX. When an image is published it is tagged with the ORDS version it contains. In general, the version of APEX included in the image is the released version publicly available at the time the image was created. It is advised to always use the image with the latest tag so that the most recent ORDS and APEX is used.

22.2.0 - ORDS 22.2.0 and APEX 22.1.0

# Before Running the ORDS container
First, create a secret in the target namespace containing the connect string, username and password to the target database service.
The secret should be of type "opaque", contain a key named "conn_string.txt" and it's value should be in the form "user/password@hostname:port/service_name". A user with SYSDBA privilege is required, like SYS. Enter the name of the secret in the values.yaml.

Installation of APEX/ORDS may fail due to a strong password verification policy in the database.
If that happens (by looking into the container'S /tmp/ords_logs/install_logs_DB/* files),
temporarily switch off strong password protection in the Oracle Database by running the following SQL command as SYS or SYSTEM:
alter profile default limit password_verify_function null;
Then kill the pod, it will restart and re-try.

# Using an ORDS configuration volume.
You can set a configuration mount with your ORDS configurations pointing to /etc/ords/config and the container will try to start the service with configurations on the mount point.

# Set an SSL configuration.
To start a secure service on the ORDS container, create a folder called "ssl", put your Certificate and Key files in this folder, the files needs to be named "cert.crt" and "key.key".

If the container detects the certificate and key files it will start the ORDS service on secure mode.

# Custom scripts.
If you need to run a custom script on the container you can add a volume with shell scripts pointing to /ords-entrypoint.d.

The ontainer will install/upgrade APEX and ORDS and before start the ORDS service will run alphabetically all the shell scripts on /ords-entrypoint.d.

# Login to APEX
Open browser on localhost with the mapped port by docker (http://localhost:8181/ords) and use below credentials:

- Workspace: internal
- User:      ADMIN
- Password:  Welcome_1
It is strongly recommend that this password is changed.

# Using SQL Developer Web

There must be a database user which is ORDS enabled prior to using SQL Developer Web. Use APEX to create a user and enable it for ORDS. Then, You will be able to log in to SQL Developer Web through e.g. http://localhost:8181/ords/sql-developer or through the user's ORDS URL like http://localhost:8181/ords/testuser/_sdw.

# Important Notes
The database credentials specified must have SYSDBA access because this is the database account that will be used to install/upgrade APEX and ORDS database components.
If the database already has an earlier version of APEX installed the container will upgrade it to the version packaged in the container. That is if the major versions of the release are the same. For compatibility in the upgrade process, should the major versions of the APEX release not be the same then the container will stop.

