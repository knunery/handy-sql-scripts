/*

    If you don't mind potentially stale row counts use this method, otherwise, use the traditional select count(*) from table_name;

*/

	SELECT schemaname,relname,n_live_tup 
    FROM pg_stat_user_tables 
    ORDER BY schemaname, relname;