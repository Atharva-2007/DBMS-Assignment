# DBMS-Assignment
MongoDB
ubuntu@ubuntu-OptiPlex-5000:~$ mongosh
Current Mongosh Log ID:	63468a1e4d98c8547a0f45ee
Connecting to:		mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+1.6.0
Using MongoDB:		6.0.2
Using Mongosh:		1.6.0

For mongosh info see: https://docs.mongodb.com/mongodb-shell/

------
   The server generated these startup warnings when booting
   2022-10-12T15:02:39.129+05:30: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
   2022-10-12T15:02:39.450+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
   2022-10-12T15:02:39.450+05:30: vm.max_map_count is too low
------

------
   Enable MongoDB's free cloud-based monitoring service, which will then receive and display
   metrics about your deployment (disk utilization, CPU, operation statistics, etc).
   
   The monitoring data will be available on a MongoDB website with a unique URL accessible to you
   and anyone you share the URL with. MongoDB may use this information to make product
   improvements and to suggest MongoDB products and deployment options to you.
   
   To enable free monitoring, run the following command: db.enableFreeMonitoring()
   To permanently disable this reminder, run the following command: db.disableFreeMonitoring()
------

test> show dbs
admin   40.00 KiB
config  72.00 KiB
db1     80.00 KiB
local   72.00 KiB
test    80.00 KiB
test> use shreyash
switched to db shreyash
shreyash> db.test.insert(name:)
Uncaught:
SyntaxError: Unexpected token, expected "," (1:19)

> 1 | db.test.insert(name:)
    |                    ^
  2 |

shreyash> db.test.insert(name:"shreyash",age:21)
Uncaught:
SyntaxError: Unexpected token, expected "," (1:19)

> 1 | db.test.insert(name:"shreyash",age:21)
    |                    ^
  2 |

shreyash> db.test.insert({name:"shreyash",age:21})
DeprecationWarning: Collection.insert() is deprecated. Use insertOne, insertMany, or bulkWrite.
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("63468cdd40ccb511ac8abaf5") }
}
shreyash> db.test.insertOne({name:"shreyash",age:21})
{
  acknowledged: true,
  insertedId: ObjectId("63468cff40ccb511ac8abaf6")
}
shreyash> db.test.find()
[
  {
    _id: ObjectId("63468cdd40ccb511ac8abaf5"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468cff40ccb511ac8abaf6"),
    name: 'shreyash',
    age: 21
  }
]
shreyash> db.test.insertOne({name:"vaibhav",age:22})
{
  acknowledged: true,
  insertedId: ObjectId("63468e3840ccb511ac8abaf7")
}
shreyash> db.test.insertOne({name:"pratik",age:20})
{
  acknowledged: true,
  insertedId: ObjectId("63468e5440ccb511ac8abaf8")
}
shreyash> db.test.find()
[
  {
    _id: ObjectId("63468cdd40ccb511ac8abaf5"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468cff40ccb511ac8abaf6"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468e3840ccb511ac8abaf7"),
    name: 'vaibhav',
    age: 22
  },
  {
    _id: ObjectId("63468e5440ccb511ac8abaf8"),
    name: 'pratik',
    age: 20
  }
]
shreyash> db.test.updateOne({age : {$lt : 18}}, {$set : {name: "pratik patil"}}) 
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 0
}
shreyash> db.test.find()
[
  {
    _id: ObjectId("63468cdd40ccb511ac8abaf5"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468cff40ccb511ac8abaf6"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468e3840ccb511ac8abaf7"),
    name: 'vaibhav',
    age: 22
  },
  {
    _id: ObjectId("63468e5440ccb511ac8abaf8"),
    name: 'pratik',
    age: 20
  }
]
shreyash> db.test.updateOne({age : {$lt : 20}}, {$set : {name: "pratik patil"}}) 
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 0
}
shreyash> db.test.updateOne({age : {$lt : 21}}, {$set : {name: "pratik patil"}}) 
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
shreyash> db.test.find()
[
  {
    _id: ObjectId("63468cdd40ccb511ac8abaf5"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468cff40ccb511ac8abaf6"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468e3840ccb511ac8abaf7"),
    name: 'vaibhav',
    age: 22
  },
  {
    _id: ObjectId("63468e5440ccb511ac8abaf8"),
    name: 'pratik patil',
    age: 20
  }
]
shreyash> db.test.deleteOne({age : 20})
{ acknowledged: true, deletedCount: 1 }
shreyash> db.test.find()
[
  {
    _id: ObjectId("63468cdd40ccb511ac8abaf5"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468cff40ccb511ac8abaf6"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468e3840ccb511ac8abaf7"),
    name: 'vaibhav',
    age: 22
  }
]
shreyash> db.test.insertMany({name :"tarak" , age: 19},{name : "vishakha", age : 18},{name : "sonal", age: 18})
MongoInvalidArgumentError: Argument "docs" must be an array of documents
shreyash> db.test.insertMany({{name :"tarak" , age: 19},{name : "vishakha", age : 18},{name : "sonal", age: 18})
Uncaught:
SyntaxError: Unexpected token (1:20)

> 1 | db.test.insertMany({{name :"tarak" , age: 19},{name : "vishakha", age : 18},{name : "sonal", age: 18})
    |                     ^
  2 |

shreyash> db.test.insertMany([{name :"tarak" , age: 19},{name : "vishakha", age : 18},{name : "sonal", age: 18}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("634691f740ccb511ac8abaf9"),
    '1': ObjectId("634691f740ccb511ac8abafa"),
    '2': ObjectId("634691f740ccb511ac8abafb")
  }
}
shreyash> db.test.find()
[
  {
    _id: ObjectId("63468cdd40ccb511ac8abaf5"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468cff40ccb511ac8abaf6"),
    name: 'shreyash',
    age: 21
  },
  {
    _id: ObjectId("63468e3840ccb511ac8abaf7"),
    name: 'vaibhav',
    age: 22
  },
  { _id: ObjectId("634691f740ccb511ac8abaf9"), name: 'tarak', age: 19 },
  {
    _id: ObjectId("634691f740ccb511ac8abafa"),
    name: 'vishakha',
    age: 18
  },
  { _id: ObjectId("634691f740ccb511ac8abafb"), name: 'sonal', age: 18 }
]
shreyash> 
(To exit, press Ctrl+C again or Ctrl+D or type .exit)
shreyash> 

