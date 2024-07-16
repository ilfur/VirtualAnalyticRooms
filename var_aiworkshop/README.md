<!--- app-name: Virtual analytic Room "Radlaufstellen" -->

## Virtual Analytic Room "AI Workshop"
# Description
This script will create an Oracle Database 23AI PDB and prepare it for Oracle AI testing features.
It will also load demo data for analysis and vector index creation into that database.
A sqlplus command line in a separate container can connect to this database for analysis.
In the command line client, access to the sample SQL scripts is given (path "/projects").

# Intention
This demonstrates how to create a full analysis environment dynamically with custom (masked) data, linking an analysis tool to that pre-populated database and offering a sample analysis in one full stack.
All components can be monitored and maintained with kubernetes / Oracle OCNE.

# Additional Notes
To connect to sqlplus, check for the IP name of the generated container / network service.
Just typing "sql" on the command line should then connect You to Your AI pluggable database.
