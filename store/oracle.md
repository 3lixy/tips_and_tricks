# Oracle

##### Find column name in tables (dba priviledge)
```
select table_name from dba_tab_columns where column_name='THE_COLUMN_YOU_LOOK_FOR';
```

##### Find column name in tables (non dba priviledge)
```
select table_name from all_tab_columns where column_name='THE_COLUMN_YOU_LOOK_FOR';
```