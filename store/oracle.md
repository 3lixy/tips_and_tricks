# Oracle

##### Find column name in tables (dba priviledge)
```
select table_name from dba_tab_columns where column_name='THE_COLUMN_YOU_LOOK_FOR';
```

##### Find column name in tables (non dba priviledge)
```
select table_name from all_tab_columns where column_name='THE_COLUMN_YOU_LOOK_FOR';
```

##### Get Reference Constraint creation sql
```
select DBMS_METADATA.GET_DDL('REF_CONSTRAINT', 'THE_REFERENCE_CONSTRAINT') from dual;
```


##### Get Constraint creation sql
```
select DBMS_METADATA.GET_DDL('CONSTRAINT', 'THE_CONSTRAINT') from dual;
```

##### Get Constraint info
```
select * from all_constraints
where constraint_name = 'CONSTRAINT'
;
```

##### Find invalid objects
```
SELECT owner, object_type, object_name
FROM all_objects
WHERE status = 'INVALID'
;
```
##### Make HTTP request
```
select utl_http.request('http://example.com:80/') from dual;
```

##### Drop acl
```
BEGIN
   DBMS_NETWORK_ACL_ADMIN.DROP_ACL (acl    => 'txti.xml' );
END;
/
COMMIT;
```

##### Drop acl oracle 11
```
dbms_network_acl_admin.drop_acl('www.xml');
COMMIT;
```

##### Create acl oracle 11
```
dbms_network_acl_admin.create_acl(
     acl => 'www.xml',
     description => 'WWW ACL',
     principal => 'SCOTT',
     is_grant => true,
     privilege => 'connect'
 );
```

##### Assign hosts and ports to the ACL oracle 11
```
dbms_network_acl_admin.assign_acl(
     acl => 'www.xml',
     host => '*',
     lower_port => 80
 );
```

##### Add users to the ACL oracle 11
```
dbms_network_acl_admin.add_privilege(
     acl => 'www.xml',
     principal => 'OE',
     is_grant => true,
     privilege => 'connect'
 );
```

