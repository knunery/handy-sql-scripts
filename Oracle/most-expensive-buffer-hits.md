
	-- http://www.rampant-books.com/art_oracle_v_sqlstats.htm
	SELECT buffer_gets, executions, buffer_gets/executions, address, sql_text 
	FROM v$sqlstats WHERE buffer_gets > 10000 ORDER BY buffer_gets;