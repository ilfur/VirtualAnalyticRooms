
# Oracle GoldenGate 21.3 Microservices Edition Container Images

Sample container image build files to provide an installation of Oracle GoldenGate for DevOps users.
These instructions apply to building container images for Oracle GoldenGate version 21c.

## Before You Start

This project was tested with:

* Oracle GoldenGate 23.4.0.0.0 Microservices for Oracle on Linux x86-64
* Oracle GoldenGate FREE 23.5.6.0.0 Microservices for Oracle on Linux x86-64
* Oracle GoldenGate 23.4.0.0.0 Microservices for MySQL on Linux x86-64
* Oracle GoldenGate 23.4.0.0.0 Microservices for PostgreSQL on Linux x86-64

Support for Oracle GoldenGate Classic Architecture is not provided.

Parameters:

* `<container name>`   - A name for the new container (default: auto generated)
* `-p <host-port>`     - The host port to map to the Oracle GoldenGate HTTPS server (default: no mapping)
* `-e OGG_ADMIN`       - The name of the administrative account to create (default: `oggadmin`)
* `-e OGG_ADMIN_PWD`   - The password for the administrative account (default: auto generated)
* `-e OGG_DEPLOYMENT`  - The name of the deployment (default: `Local`)
* `-v /u01/ogg/scripts`- The volume used for executing setup (${OGG_HOME}/scripts/setup) and startup (${OGG_HOME}/scripts/startup) user scripts (default: none)
* `-v /u02`            - The volume used for persistent GoldenGate data (default: use container storage)
* `-v /u03`            - The volume used for temporary GoldenGate data (default: use container storage)
* `-v /etc/nginx/cert` - The volume used for storing the SSL certificate for the HTTPS server (default: create a self-signed certificate)


### Administrative Account Password

On the first startup of the container, a random password will be generated for the Oracle GoldenGate administrative user if not provided by the `OGG_ADMIN_PWD` environment variable. You can find this password at the start of the container log:

```sh
$ docker logs <container name> | head -3
----------------------------------------------------------------------------------
--  Password for OGG administrative user 'oggadmin' is 'ujX7sqQ430G9-xSlr'
----------------------------------------------------------------------------------
```

### SSL Certificate

When bringing your own SSL certificate to an Oracle GoldenGate container, two files are needed:

1. `ogg.key` - The private key for the SSL certificate.
1. `ogg.pem` - The SSL leaf certificate, and a full certificate trust chain

If these files are located in a directory called `cert`, they can be used in the GoldenGate container with a volume mount as shown here:


### Running scripts before setup and on startup
The container images can be configured to run scripts before setup and on startup. Currently, `.sh` extensions are supported. For setup scripts just mount the volume `/u01/ogg/scripts/setup` or extend the image to include scripts in this directory. For startup scripts just mount the volume `/u01/ogg/scripts/startup` or extend the image to include scripts in this directory. Both of those locations are static and the content is controlled by the volume mount.


## Known Issues

None

## License

All scripts and files hosted in this project and GitHub [docker-images/OracleGoldenGate](../) repository required to build the container images are, unless otherwise noted, released under the Universal Permissive License (UPL), Version 1.0.  See [LICENSE](/LICENSE) for details.

To download and run Oracle GoldenGate, regardless whether inside or outside a container, you must download the binaries from the [Oracle Technology Network](http://www.oracle.com/technetwork/middleware/goldengate/downloads/index.html) and accept the license indicated at that page.

## Copyright

Copyright &copy; 2022 Oracle and/or its affiliates.
