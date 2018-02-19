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
