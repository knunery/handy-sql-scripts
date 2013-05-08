
	-- http://www.rampant-books.com/art_oracle_v_sqlstats.htm
	SELECT disk_reads, executions, disk_reads/executions, address, sql_text
	FROM v$sqlstats WHERE disk_reads > 5000 ORDER BY disk_reads;