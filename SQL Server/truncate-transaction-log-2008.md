/*

The "Simple" recovery model does what it implies, it gives you a simple backup that can be used to
replace your entire database in the event of a failure or if you have the need to restore your 
database to another server.  With this recovery model you have the ability to do complete backups 
(an entire copy) or differential backups (any changes since the last complete backup).  
With this recovery model you are exposed to any failures since the last backup completed. 

*/


    SELECT name,recovery_model_desc from sys.databases
    GO 
    Alter database <YourDatabaseName> SET Recovery simple
    GO
    Declare @LogFileLogicalName sysname
    SELECT @LogFileLogicalName=Name from sys.database_files where Type=1
    print @LogFileLogicalName

    DBCC Shrinkfile(@LogFileLogicalName,100)