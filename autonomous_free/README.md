<!--- app-name: Virtual analytic Room "Radlaufstellen" -->

## Autonomous Database FREE
# Description
Oracle Autonomous Database Free Container image supports 2 types of database workload types; ADW and ATP. These are similar to Transaction Processing and Data Warehouse workload type databases in Autonomous Database Serverless Cloud service.

Following key features are supported:

Oracle Rest Data Services (ORDS)
APEX
Database Actions
Mongo API
Oracle Estate Explorer (OEE)
The storage size is limited to 20 GB for each Database

Using this image
Database versions
From the released images, choose the database version and corresponding image to work with.

We use the following naming convention:

Database version	Latest image tag	Specific release image tag
23ai	latest-23ai	24.11.4.2-23ai
19c	latest	24.9.3.2
Container CPU/memory requirements
Oracle Autonomous Database Free container needs 4 CPUs and 8 GiB memory

On first startup of the container:
User mandatorily has to change the admin passwords. Please specify the password using the environment variable
ADMIN_PASSWORD

Wallet is generated using the wallet password WALLET_PASSWORD

Following table explains the environment variables passed to the container

Environment variable	Description
WORKLOAD_TYPE	Can be either ATP or ADW. Default value is ATP
DATABASE_NAME	Database name should contain only alphanumeric characters. if not provided, the Database will be called either MYATP or MYADW depending on the passed workload type
ADMIN_PASSWORD	Admin user password must be between 12 and 30 characters long and must include at least one uppercase letter, one lowercase letter, and one numeric. The password cannot contain username
WALLET_PASSWORD	Wallet password must have a minimum length of eight characters and contain alphabetic characters combined with numbers or special characters.
ENABLE_ARCHIVE_LOG	To enable archive logging in the database. Default value is True. To turn off archive logging set the value to False
> Note: For OFS mount, container should start with SYS_ADMIN capability. Also, virtual device /dev/fuse should be accessible

Ports
Note the following ports which are forwarded to the container process

Port	Description
1521	TLS
1522	mTLS
8443	HTTPS port for ORDS / APEX and Database Actions
27017	Mongo API
HTTP proxy
If you are behind a corporate proxy, there are 2 ways to configure the database
to use the proxy settings

Set the HTTP_PROXY database property. This is used by packages like DBMS_CLOUD
exec DBMS_CLOUD_CONTAINER_ADMIN.set_database_property('HTTP_PROXY', 'www-my-corp-proxy.com:80/');
Use UTL_HTTP.set_proxy to set proxy for HTTP requests sent using UTL_HTTP
exec UTL_HTTP.SET_PROXY('www-my-corp-proxy.com');
adb-cli
adb-cli can be used to perform database operations after container is up and running

To use adb-cli, you can define the following alias for convenience

alias adb-cli="podman exec <container_name> adb-cli"
Available commands
&gt;&gt; adb-cli --help

Usage: adb-cli [OPTIONS] COMMAND [ARGS]...

  ADB-S Command Line Interface (CLI) to perform container-runtime database
  operations

Options:
  -v, --version  Show the version and exit.
  --help         Show this message and exit.

Commands:
  add-database
  change-password
Add Database
You can add a database using the add-database command

adb-cli add-database --workload-type "ADW" --admin-password "Welcome_1234"
Change Password
To change password for Admin user, use the following command

adb-cli change-password --database-name "MYADW" --old-password "Welcome_1234" --new-password "Welc

##Oracle Estate Explorer (OEE)
Oracle Estate Explorer is a tool that enables customers to
programmatically evaluate groups of Oracle databases for migration readiness to Oracle’s Autonomous Database (ADB). The output from OEE
provides a high-level estate overview of the tested group of databases, ranks them according to their alignment with ADB pre-requisites and
delivers a graded relative effort of any remediation required.

The OEE APEX app is installed in the adb-free images and is available to use out-of-the-box

Following steps are required to launch the OEE app:

Login as Database admin and set a password for the MPACK_OEE user
ALTER USER MPACK_OEE IDENTIFIED BY <password>
Visit the APEX URL using https://localhost:8443/ords/apex

Login to the MPACK_OEE APEX workspace using the password set in Step 1

Change the MPACK_OEE’s APEX account password. A warning page will be displayed after changing the MPACK_OEE’s APEX account password, please ignore it and click on Application Builder to launch the OEE application.

On the application home page, click “Run Application” to open the OEE app in a new browser tab.
