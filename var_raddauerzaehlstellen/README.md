<!--- app-name: Virtual analytic Room "Radlaufstellen" -->

## Virtual Analytic Room "Radlaufstellen"
# Description
This script will install an Oracle Database 21c in a container und prepare it for Oracle Machine Learning for Python.
It will also load csv files as well as masked demo data for analysis into that database.
A Jupyter Notebook in a separate container can connect to this database for analysis. Notebooks can be created and saved/persisted. A sample Notebook for analyzing the data "Radlaufstellen" is also installed.
With CloudBeaver, you may browse the database, query tables and views and make changes to the schema.
With the link to an external Oracle Analytics application, you can analyze sustainability data.
# Intention
This demonstrates how to create a full analysis environment dynamically, including data, users and access privileges, linking an analysis tool to the pre-populated database and offering a sample analysis in one full stack. All components can be monitored and maintained with kubernetes or Oracle Verrazzano.

# Additional Comments
To connect to the notebook, check for the IP address of the notebook's kubernetes service and port 8889. When connecting to that IP address with a browser, a login token is being asked for the first login. The notebook log in kubernetes shows the login token required for the first access.

The same applies to CloudBeaver.

# Version Notes
- OAM-Umstellung: Einbindung Jupyter/CloudBeaver in Grafana/Kiali 
- OAS Service YAML integriert
- Korrekturen Jupyter Notebook
- Umzug auf DerRotMilan GitHub
- Korrekturen DPIMP