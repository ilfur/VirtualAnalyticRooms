
# Oracle GoldenGate Microservices Edition Container Images

This chart installs GoldenGate Free, Database23ai Free, instant client, jupyter and sets up a sync between the installed 23ai database and a previously installed autonomous database (ADB). A provided jupyter notebook can run the CPAT assessment tool for database migrations.

To have this chart fully working, please install ingress-nginx and OraOperator first.
This chart uses an Ingress and a SingleInstanceDatabase resource, which must be known to kubernetes beforehand.

Before installing this chart, please also create two kubernetes secrets which contain the following required fields:




