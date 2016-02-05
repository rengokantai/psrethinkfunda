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
