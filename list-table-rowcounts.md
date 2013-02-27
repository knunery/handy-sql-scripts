/*

SQL Script that list all tables and their row counts.

reference: http://blog.sqlauthority.com/2010/09/08/sql-server-find-row-count-in-table-find-largest-table-in-database-part-2/

*/

	SELECT sc.name +'.'+ ta.name TableName
	,SUM(pa.rows) RowCnt
	FROM sys.tables ta
	INNER JOIN sys.partitions pa
	ON pa.OBJECT_ID = ta.OBJECT_ID
	INNER JOIN sys.schemas sc
	ON ta.schema_id = sc.schema_id
	WHERE ta.is_ms_shipped = 0 AND pa.index_id IN (1,0)
	GROUP BY sc.name,ta.name
	ORDER BY SUM(pa.rows) DESC
