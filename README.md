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
 ```
 We can see that there is document in this collection. This document has an underscore ID key whose value is set to an object ID. This field gets automatically generated every time a new document is created.
 we use JSON to define it the objects in our database which then it gets converted into something called Pisan seen here And the only difference between these two in code is that piece on has quotation marks surrounding both the key and value pairs of our objects.

 5. The above command prints out a string of everything that we have in there.But it is pretty hard to read especially if you have a lot of documents.One way to fix this is that we can change it a command called Pretty which will then display all of our documents in a much easier to read format.

 ```
 db.--name of collection to look at".find().pretty()"
 ```

 6. To create collections- 
 
 ```
 db.createCollection("Cars")
 ```

 7. To add a new document in the collection car by 
 ```
 db.car.insert({
     name: "Honda",
     model: "2019",
     price: 1000000
 }) 
 ```
 8. If we want to update something
 ```
db.car.update({
    name: 'honda'
    },
    { $set: {
     name: 'xyz'
    }
})
```
9. To update and add some property in document.
```
db.car.update({
    name: "xyz"
},
{
    $set:{
        transmittion:"automatic"
    }
},
{$upsert: true})
```
10. To remove all the document 
```
 db.car.remove({})
 ```
  and fro perticular -
  
```
db.car.remove({name:"xyz"}) 
```

## Data Type

We've already introduced the concepts of what a schema and a collection are.

You can think of them as essentially being equal in so much as the schema forms a representation or a model encoding of the data that gets stored into our collection.

Let's now take a look at the different types of data that can get stored.

There are six main data types.
1. String
2. number
3. date 
4. array 
5. boolean
6. object ID.

![alt text](https://github.com/IshantL/MongoDB-Project/blob/master/images/datatype.png)


There is also two other data types 

They are a buffer and mixed data buffer is used to store things like images video and audio mixed type allows you to sort different types based on what you pass into it.

So you might want to store in certain instances strings and in other instances arrays.

## Query Data

create collection by using db.createCollection("students");
```
db.student.insert({
    name: 'Joe',
    undergrad: true,
    units: 9,
    classes: ['geography', 'math', 'journalism']
})

db.student.insert({
    name: 'Jane',
    undergrad: false,
    units: 12,
    classes: ['geography', 'science', 'journalism', 'history']
})

db.student.insert({
    name: 'Kevin',
    undergrad: true,
    units: 3,
    classes: ['geography']
})

db.student.insert({
    name: 'Rachel',
    undergrad: false,
    units: 6,
    classes: ['geography', 'history']
})

db.student.find({})
db.student.find({'name': 'Rachel'})
db.student.find({units: {$gt: 6}})  //greater than 6
db.student.find({units: {$lt: 7}})  // less than 7
```
So in this example we're looking within the classes field and we want to pull out all those students that are enrolled in history.
```
db.student.find({classes: {$in: ['history']}}) //
```

So using that and we always have to specify an array so we could say history and geography for example and this would be an array.
```
db.student.find({classes: {$in: ['history','geography']}}).pretty()
```

Now we'll take a look at how we can sort and limit the results of our queries.

So when we're sorting we typically assign either a 1 or a negative one to whatever it is that we're trying to sort.

So in this example we're looking for students enrolled in history and then we're sorting by ascending and we're filtering by the number of units.
```
db.student.find({classes: {$in: ['history']}}).sort({units: 1})    // ascending
```
So whichever student is enrolled in fewer units should appear at the top of the data that we get back. when we submit this query we get back first Rachel who's enrolled in six units and then Jane who was enrolled in 12 units.

So it was able to pull out those students again enrolled in history and then sort based on the number of units that they're taking in we can clean this up a little bit so you can see it better by using the doc pretty command.


when we're using sort it will either sort numerically or alphabetically so in this case we're sorting numerically.

If instead we wanted to sort alphabetically we would be sorting a string.
We'd be sorting in a descending manner so those with a name closer to A will appear first and those with the names closer to Z will appear towards the bottom.

```
db.student.find({}).sort({name: -1})    // descending
```
And finally we always have the option to limit the number of results that we get back and we can easily pass in just a number so that after retrieving all those documents according to whatever specificity that we've indicated we can then say now only give me the first two that you get back. So again you can see how we've limited this to the first two results sorted by name.
```
db.student.find({}).sort({name: 1}).limit(2)
```
