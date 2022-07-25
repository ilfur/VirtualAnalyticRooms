##What Is Oracle Machine Learning for Python?
Oracle Machine Learning for Python (OML4Py) enables you to run Python commands for data transformations and for statistical, machine learning, and graphical analysis on data stored in or accessible through an Oracle database using a Python API.

OML4Py is a Python module that enables Python users to manipulate data in database tables and views using Python syntax. OML4Py functions and methods transparently translate a select set of Python functions into SQL for in-database execution.

OML4Py is available in the following Oracle database environments:

* The Python interpreter in Oracle Machine Learning Notebooks in your Oracle Autonomous Database. For more information, see Get Started with Notebooks for Data Analysis and Data Visualization in Using Oracle Machine Learning Notebooks.

In this environment, all the required components are included, including Python, required Python libraries, and the Python interpreter in Notebooks.

* An OML4Py client connection to OML4Py in an on-premises Oracle Database instance.

For this environment, you must install Python, the required Python libraries, and the OML4Py server components in the database, and you must install the OML4Py client. See Install OML4Py for On-Premises Databases.

Designed for problems involving both large and small volumes of data, OML4Py integrates Python with the database. With OML4Py, you can do the following:

* Develop, refine, and deploy user-defined Python functions and machine learning models that leverage the parallelism and scalability of the database to automate data preparation and machine learning.

* Run overloaded Python functions and use native Python syntax to manipulate in-database data, without having to learn SQL.

* Use Automated Machine Learning (AutoML) to enhance user productivity and machine learning results through automated algorithm and feature selection, as well as model tuning and selection.

* Use Embedded Python Execution to run user-defined Python functions in Python engines spawned and managed by the database environment. The user-defined functions and data are automatically loaded to the engines as required, and when data-parallel and task-parallel execution is enabled.

##About the Python Components and Libraries in OML4Py
OML4Py requires an installation of Python, a number of Python libraries, as well as the OML4Py components.

* In Oracle Autonomous Database, OML4Py is already installed. The OML4Py installation includes Python, additional required Python libraries, and the OML4Py server components. A Python interpreter is included with Oracle Machine Learning Notebooks in Autonomous Database.

* You can install OML4Py in an on-premises Oracle Database. In this case, you must install Python, the additional required Python libraries, the OML4Py server components, and an OML4Py client. See Install OML4Py for On-Premises Databases.

#Python Version in Current Release of OML4Py

The current release of OML4Py is based on Python 3.9.5.

This version is in the current release of Oracle Autonomous Database. You must install it manually when installing OML4Py on an on-premises Oracle Database.

#Required Python Libraries

The following Python libraries must be included.

cx_Oracle 8.1.0
cycler 0.10.0
joblib 1.1.0
kiwisolver 1.1.0
matplotlib 3.3.3
numpy 1.21.5
pandas 1.3.4
Pillow-8.2.0
pyparsing 2.4.0
python-dateutil 2.8.1
pytz 2019.3
scikit-learn 1.0.1
scipy 1.7.3
six 1.13.0
threadpoolctl 2.1.0
All the above libraries are included with Python in the current release of Oracle Autonomous Database.

For an installation of OML4Py in an on-premises Oracle Database, you must install Python and additionally the libraries listed here. See Install OML4Py for On-Premises Databases.

