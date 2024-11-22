<!--- app-name: Oracle ORDS -->

# Oracle REST Data Services 
## Description
ORDS is a mid-tier Java application, providing a Database Management REST API, SQL Developer Web, a PL/SQL Gateway, SODA for REST, and the ability to publish RESTful Web Services for interacting with the data and stored procedures in your Oracle Database. See https://oracle.com/rest for more information.

This image is purposefully built to provide all the ORDS services on a simple container. Users will be able to bind mount (folders or docker volumes) configurations, wallets, certificates, APEX images, etc. and with the Oracle REST Data Services (ORDS) command line interface user will be able to configure/install or run ORDS services in one or multiple containers.

## Version matrix
Each image uses Oracle Linux with a specific version of ORDS and APEX. When an image is published it is tagged with the ORDS version it contains. In general, the version of APEX included in the image is the released version publicly available at the time the image was created. It is advised to always use the image with the latest tag so that the most recent ORDS and APEX is used.

22.2.0 - ORDS 22.2.0 and APEX 22.1.0
24.3.0 - ORDS 24.3.0 and APEX 24.1.0

## Before Running the ORDS container
First, create a secret in the target namespace containing the connect information, username and password to the target database service.
If You intend to use ORDS with SSL/HTTPS, also create a secret containg the private key and certificate. See the values.yaml for better instructions and sample vallues.

Installation of APEX/ORDS may fail due to a strong password verification policy in the database.
If that happens (by looking into the container'S /tmp/ords_logs/install_logs_DB/* files),
temporarily switch off strong password protection in the Oracle Database by running the following SQL command as SYS or SYSTEM:
alter profile default limit password_verify_function null;
Then kill the pod, it will restart and re-try.

# Custom scripts.
If you need to run a custom script on the container you can change the created configMap to add Your custom commands, e.g. to add or remove ORDS features, download APEX images on-the-fly and more.

# Login to APEX
Open browser with the mapped port and host (e.g. http://localhost:8080/ords) , klick on APEX and use below credentials:

- Workspace: internal
- User:      ADMIN
- Password:  Welcome_1
It is strongly recommend that this password is changed.

# Using SQL Developer Web

There must be a database user which is ORDS enabled prior to using SQL Developer Web. Use APEX to create a user and enable it for ORDS. Then, You will be able to log in to SQL Developer Web through e.g. http://localhost:8181/ords/sql-developer or through the user's ORDS URL like http://localhost:8181/ords/testuser/_sdw.

# Important Notes
The database credentials specified must have SYSDBA access because this is the database account that will be used to install/upgrade APEX and ORDS database components.
If the database already has an earlier version of APEX installed the container will upgrade it to the version packaged in the container. That is if the major versions of the release are the same. For compatibility in the upgrade process, should the major versions of the APEX release not be the same then the container will stop.

