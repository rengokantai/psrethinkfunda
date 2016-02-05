#### psrethinkfunda
- cp1
create db
```
r.dbCreate("dbname")
r.dbCreate("dbname").tableCreate("tablename")
```
r.db("dbname").tableList()
r.db("dbname").table("tablename")
r.dbDrop("dbname")
```
