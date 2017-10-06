# MongoDB queries

### Runing
#
```sh
$ mongod
cmd + t
$ mongo
```

### Create db or switch to db
#
```sh
$ use test
```

### Show Databases and Collections
#
```sh
$ show dbs
$ show collections
```

### Print 
#
```sh
$ print("test");
```

### Insert 
#
```sh
$ db.test.insert({â€œtestâ€ : â€œtestâ€ });
```

### Find 
#
```sh
$ db.test.find({"id":1}).explain("executionStats");
$ db.test.find({"id":1}).explain();
```
##### Multiple condition 
##### ( lte : less than or equal , gte : greater than or equal )
#

```sh
$ db.test.find( {"tourPrice":{$lte :500}, "tourLength" : {$lte:3}});
```
##### Show custom fields
#
```sh
$ db.test.find({}, {first_name:1,_id:0});
```
##### Sorting
#
```sh
$ db.test.find({}, {tourName:1 , tourPrice:1 , tourLength: 1 , _id:0}).sort({tourPrice:-1});
```

##### Limit query
#
```sh
$ db.test.find({}, {tourName:1 , tourPrice:1 , tourLength: 1 , _id:0}).pretty().sort({tourPrice:-1}).limit(1);
```
##### Pagination
#
```sh
$ db.test.find({}, {tourName:1 , tourPrice:1 , tourlength: 1 , _id:0}).sort({tourPrice:-1}).limit(1).skip(5);
```
### Count
#
```sh
$ db.test.count(); 
```

### Functional query
#
```sh 
$ for (i =0 ; i<1000 ; i++) { db.numbers.insert( {"number" : i} )}; 
```

### Import File
# 
```sh
$ mongoimport â€”db learning_mongo â€”collection tours â€”jsonArray â€”file test.json
```

### Update 
#
```sh
$ db.test.update({"id":"1"},{$set : {"first_name" : "reza"}});
```

### Update and add to set
#
```sh
$ db.test.update({"id":"1"},{$addToSet : {"last_name":"Nehzati"}});
```
### Remove set
#
```sh
$ db.test.remove({"id":"1"});
```

### Drop Object
#
```sh
$ db.test.drop();
```

### Create Index 
#
```sh 
$ db.test.createIndex({tourPackage:1});
$ db.test.createIndex({"tourName":1},{unique: true});
```
###### Create text Index 
#
```sh 
$ db.test.createIndex({tourName:"text"});
```
###### Find Indexd text 
#
```sh 
$ db.test.find({$text:"text"});
```
###### Regex query
#
```sh
$ db.tours.find({tourDescription:/backpack/i},{tourName:1,_id:0})
```
###### aggregate
#
```sh
$ db.test.aggregate([{$group: {_id: '$tourPackage', count: {$sum : 1}}}])
```
