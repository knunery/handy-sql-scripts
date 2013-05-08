/*

SQL Script that gets the fragmentation of every index in your database.

reference: http://blog.sqlauthority.com/2008/03/27/sql-server-2005-find-index-fragmentation-details-slow-index-performance/

What is fragmentation?

> Before you decide to defragment an index you should determine how badly affected it is. 
This aids you in selecting the most appropriate action. Fragmentation is measured as a 
percentage that indicates the number of pages that are not in the ideal order. A value 
below 5% indicates a very lightly fragmented index that requires no maintenance. A value 
of between 5% and 30% can be improved by reorganising the index. Greater than 30% 
fragmentation warrants an index rebuild.
reference: http://www.blackwasp.co.uk/SQLIndexFragmentation.aspx

*/

	SELECT ps.database_id, ps.OBJECT_ID,
	ps.index_id, b.name,
	ps.avg_fragmentation_in_percent
	FROM sys.dm_db_index_physical_stats (DB_ID(), NULL, NULL, NULL, NULL) AS ps
	INNER JOIN sys.indexes AS b ON ps.OBJECT_ID = b.OBJECT_ID
	AND ps.index_id = b.index_id
	WHERE ps.database_id = DB_ID()
	ORDER BY ps.avg_fragmentation_in_percent desc, ps.OBJECT_ID
