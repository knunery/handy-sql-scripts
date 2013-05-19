/*

    List the databases.
    \list or \l will do the same thing.
    PROTIP: To see the query behind commands like '\list' run psql witht the flag -E.
*/    
    
    SELECT * FROM pg_database;

    SELECT table_schema,table_name
    FROM information_schema.tables
    ORDER BY table_schema,table_name;