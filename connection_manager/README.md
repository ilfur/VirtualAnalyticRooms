<!--- app-name: Oracle Connection Manager CMAN -->

# Oracle Connection Manager (CMAN) 
## Description
Oracle Connection Manager is a proxy server that forwards connection requests to databases or other proxy servers. It operates at the session level, and usually resides on a computer separate from the database server and client computers.

Oracle Connection Manager is available for installation with Oracle Database Enterprise Edition. It is a custom installation option on the client system. Starting with Oracle Database Client 23ai, Oracle Connection Manager is available as an image file for installation and configuration. Refer to your platform-specific Oracle Database installation guide for additional information.

## Notes for this Release
* This install can be configured to write logs and traces to a persistent volume like NFS for further analysis. Those logs are in addition to the standard container log.
* This install can be configured to write the cman.ora configuration file to an external persistent volume to change it from outside of kubernetes. By default, though, a ConfigMap holds a cman.ora which is inserted into the container on startup. 
* This install opens a standard TCP service on port 1521 which can be configured as LoadBalancer for external access, ClusterIP for internal access that can be proxied through a Gateway or a non-recommended NodePort. Using an Ingress to forward to the CMAN container is strongly discouraged, since the network protocol used by CMAN is non-http, just plain Oracle NET8 sockets.
* At the moment, health checks and external reload of cman configuration is non-functional since the REST service support of CMAN is switched off in the standard container in use.
* To activate a new CMAN configuration, either change the cman.ora file on the persistent volume or change the ConfigMap holding the cman.ora, then restart the CMAN container. Optionally, open a shell to the CMAN container ```"kubectl exec -ti <container-name> -n <namespace> -- /bin/bash"``` and issue a ```"cmctl" + "administer <cman-name>" + "reload"```.

