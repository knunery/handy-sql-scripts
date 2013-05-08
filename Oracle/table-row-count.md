	select 
	   table_name, 
	   num_rows counter 
	from 
	   all_tables 
	where 
	   owner = 'YOUR_SCHEMA_NAME'
	order by 
	   table_name;