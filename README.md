# MongoDB-Project

## Installation Steps of Mongo DB
 1. Download Mongo DB from MOngo official site.
 2. Navigate to Mongo Installation folder and in Bin type command mongod to start mongo 
 3. after the server start, we can use mongo command to open up mongo DB shell and use commands
 
 ## List of commands
 1. "show dbs" -show the list of databases in the system

 2. "use" - to open the already created db instance.

 3. "show collections" - to see what collections are created in the database

 4. The schema  is a representation of the collection and it will constitute key value pairs command that we can use to look into one of these collections is the find the method is 
 ```
 db.--name of collection to look at".find()
 ```.
 We can see that there is document in this collection. This document has an underscore ID key whose value is set to an object ID. This field gets automatically generated every time a new document is created.
 we use JSON to define it the objects in our database which then it gets converted into something called Pisan seen here And the only difference between these two in code is that piece on has quotation marks surrounding both the key and value pairs of our objects.

 5. The above command prints out a string of everything that we have in there.But it is pretty hard to read especially if you have a lot of documents.One way to fix this is that we can change it a command called Pretty which will then display all of our documents in a much easier to read format.
 "db.--name of collection to look at".find().pretty()"

 6. To create collections- "db.createCollection("Cars")"

 7. To add a new document in the collection car by 
 db.car.insert({
     name: "Honda",
     model: "2019",
     price: 1000000
 }) 
 8. If we want to update something
db.car.update({
    name: 'honda'
    },
    { $set: {
     name: 'xyz'
    }
})

9. To update and add some property in document.

db.car.update({
    name: "xyz"
},
{
    $set:{
        transmittion:"automatic"
    }
},
{$upsert: true})

10. To remove all the document - db.car.remove({}) and fro perticular - db.car.remove({name:"xyz}) 