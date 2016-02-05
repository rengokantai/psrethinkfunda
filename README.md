#### psrethinkfunda
- cp1
create db
```
r.dbCreate("dbname")
r.dbCreate("dbname").tableCreate("tablename")
```

basic
```
r.db("dbname").tableList()
r.db("dbname").table("tablename")
r.dbDrop("dbname")
```

crud
```
r.db("dbname").table("tablename").count().typeOf()
r.db("dbname").table("tablename").insert({name:"x"})
r.db("dbname").table("tablename").filter({name:"x"}).delete();
r.db("dbname").table("tablename").get("11111111-1111-1111-1111-111111111111").replace(....);
```

chains
```
r.db("dbname").table("tablename").filter(function(e){return field("x").match(regExp)})
```

common func
```
r.db("dbname").table("tablename").pluck("f1","f2").orderBy("f1").limit(5);
```
concatMap: multi-level searching
```
r.db("dbname").table("tablename").hasFields("x").concatMap(function(x){
  return x("y").filter(function(y){
    return y("z").match(regexp)
  })
})
```
withFields = hasFields+ return  

logic, date,time
```
r.db("dbname").table("tablename").filter(function(x){
return x("y").gt(...).and(x("y")).lt(...)
}).pluck("y")
```
date->string, use ISO8601(date) function  

build time:
```
r.time(2015,r.january,12,'-10:00')
```

- cp3  
import data  
install python driver first
```
rethinkdb import -f data.json --table db.table
```

secondary indexes
```
r.db("dbname").table("tablaname").indexCreate("indexname",r.row("index1")("index2"));
```
Usingsecondary indexes:
```
r.db("dbname").table("tablaname").filter(function(x){return x("index1")("index2").eq(regexp)})
```
