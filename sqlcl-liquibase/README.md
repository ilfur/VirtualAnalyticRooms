##Working with Oracle SQLcl
Oracle SQLcl (SQL Developer Command Line) is a Java-based command-line interface for Oracle Database. Using SQLcl, you can interactively or batch execute SQL and PL/SQL statements. SQLcl provides inline editing, statement completion, command recall, and also supports existing SQL*Plus scripts.

##About Liquibase
Liquibase is an open-source database-independent library for tracking, managing and applying database schema changes. For an understanding of the major concepts in Liquibase, see Major Concepts.

In SQLcl, you can now execute commands to generate a changelog for a single object or for a full schema (changeset and changelogs). You can process these objects manually using SQLcl or through any of the traditional Liquibase interfaces.

With the Liquibase feature in SQLcl, you can:

Generate and execute single object changelogs
Generate and execute schema changesets with object dependencies
Automatically sort a changeset during creation based on object dependencies
Record all SQL statements for changeset or changelog execution, as it is generated
Provide full rollback support for changesets and changelogs automatically

