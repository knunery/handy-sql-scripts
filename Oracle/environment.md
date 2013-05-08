	select SYS_CONTEXT('USERENV', 'IP_ADDRESS', 15) ipaddr from dual;

	select SYS_CONTEXT('USERENV', 'HOST', 15) host_name from dual;