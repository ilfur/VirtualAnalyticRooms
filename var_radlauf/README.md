<!--- app-name: Virtual analytic Room "Radlaufstellen" -->

## Virtual Analytic Room "Radlaufstellen"
# Description
This script will install an Oracle Database 21c in a container und prepare it for Oracle Machine Learning for Python.
It will also load masked demo data for analysis into that database.
A Jupyter Notebook in a separate container can connect to this database for analysis.
Notebooks can be created and saved/persisted. A sample Notebook for analysing the masked data "Radlaufstellen" is also installed.

# Intention
This demonstrates how to create a full analysis environment dynamically with custom (masked) data, linking an analysis tool to that pre-populated database and offering a sample analysis in one full stack.
All components can be monitored iand maintained with kubernetes or Oracle Verrazzano.

# Additional Notes
To connect to the notebook, check for the IP address of the notebook's kubernetes service and port 8889.
When connecting to that IP address with a browser, a login token is being asked for the first login.
The notebook log in kubernetes shows the login token required for the first access.
