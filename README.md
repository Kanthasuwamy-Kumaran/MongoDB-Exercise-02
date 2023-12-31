# MongoDB-Exercise-02
MongoDB-Exercise-02

**1. Create a Database called customers.**
``movie> use customers
switched to db customers``

**2. Create a collection called customerdetails.**
``customers> db.createCollection("customerdetails")
{ ok: 1 }``

**3. Insert all documents into the collection named   customerdetails.**
``customers> db.customerdetails.insertMany([{name: "John", age:"25",gender:"Male",city:"New york"},{name: "Emily", age:"22",gender:"Female",city:"London"},{name: "Daniel", age:"28",gender:"Male",city:"Sydney"},{name: "Sophia", age:"24",gender:"Female",city:"Paris"},{name: "William", age:"26",gender:"Male",city:"Chicago"},{name: "Olivia", age:"23",gender:"Female",city:"Los Angeles"},{name: "Benjamin", age:"27",gender:"Male",city:"Toronto"},{name: "Mila", age:"29",gender:"Female",city:"Berlin"},{name: "James", age:"30",gender:"Male",city:"Tokyo"}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("654cafc683231ea19eb525eb"),
    '1': ObjectId("654cafc683231ea19eb525ec"),
    '2': ObjectId("654cafc683231ea19eb525ed"),
    '3': ObjectId("654cafc683231ea19eb525ee"),
    '4': ObjectId("654cafc683231ea19eb525ef"),
    '5': ObjectId("654cafc683231ea19eb525f0"),
    '6': ObjectId("654cafc683231ea19eb525f1"),
    '7': ObjectId("654cafc683231ea19eb525f2"),
    '8': ObjectId("654cafc683231ea19eb525f3")
  }
}
``

**4. Retrieve all documents from the collection and sort the results by the “age” field    in ascending order.**
``customers> db.customerdetails.find().sort({ age: 1 }).pretty()
[
  {
    _id: ObjectId("654cafc683231ea19eb525ec"),
    name: 'Emily',
    age: '22',
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525f0"),
    name: 'Olivia',
    age: '23',
    gender: 'Female',
    city: 'Los Angeles'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525ee"),
    name: 'Sophia',
    age: '24',
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525eb"),
    name: 'John',
    age: '25',
    gender: 'Male',
    city: 'New york'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525ef"),
    name: 'William',
    age: '26',
    gender: 'Male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525f1"),
    name: 'Benjamin',
    age: '27',
    gender: 'Male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525ed"),
    name: 'Daniel',
    age: '28',
    gender: 'Male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525f2"),
    name: 'Mila',
    age: '29',
    gender: 'Female',
    city: 'Berlin'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525f3"),
    name: 'James',
    age: '30',
    gender: 'Male',
    city: 'Tokyo'
  }
]
``

**5. Count the number of females.**
``customers> db.customerdetails.countDocuments({gender: "Female"})
4
``

**6.Insert one document into the customerdetails collection.**
``customers> db.customerdetails.insertOne({name: "Raja", age:"23",gender:"Male",city:"Jaffna"})
{
  acknowledged: true,
  insertedId: ObjectId("654cb3a583231ea19eb525f4")
}
``

**7. Update city=SriLanka to John.**
``
customers> db.customerdetails.update({name:"John"},{$set:{city:"Srilanka"}})
DeprecationWarning: Collection.update() is deprecated. Use updateOne, updateMany, or bulkWrite.
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
customers> db.customerdetails.find()
[
  {
    _id: ObjectId("654cafc683231ea19eb525eb"),
    name: 'John',
    age: '25',
    gender: 'Male',
    city: 'Srilanka'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525ec"),
    name: 'Emily',
    age: '22',
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525ed"),
    name: 'Daniel',
    age: '28',
    gender: 'Male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525ee"),
    name: 'Sophia',
    age: '24',
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525ef"),
    name: 'William',
    age: '26',
    gender: 'Male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525f0"),
    name: 'Olivia',
    age: '23',
    gender: 'Female',
    city: 'Los Angeles'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525f1"),
    name: 'Benjamin',
    age: '27',
    gender: 'Male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525f2"),
    name: 'Mila',
    age: '29',
    gender: 'Female',
    city: 'Berlin'
  },
  {
    _id: ObjectId("654cafc683231ea19eb525f3"),
    name: 'James',
    age: '30',
    gender: 'Male',
    city: 'Tokyo'
  },
  {
    _id: ObjectId("654cb3a583231ea19eb525f4"),
    name: 'Raja',
    age: '23',
    gender: 'Male',
    city: 'Jaffna'
  }
]
``

**8. Remove the customer from Tokyo.**
``db.customerdetails.remove({city:"Tokyo"})

DeprecationWarning: Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.
{ acknowledged: true, deletedCount: 1 }``

**9.  Find customers not from Los Angeles.**
``db.customerdetails.find({city:{$ne:"Los Angels"}})
[
  {
    _id: ObjectId("65547511831f5bd5c913d723"),
    name: 'John',
    age: 25,
    gender: 'Male',
    city: 'SriLanka'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d724"),
    name: 'Emily',
    age: 22,
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d725"),
    name: 'Daniel',
    age: 28,
    gender: 'Male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d726"),
    name: 'Sophia',
    age: 24,
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d727"),
    name: 'William',
    age: 26,
    gender: 'Male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d728"),
    name: 'Olivia',
    age: 23,
    gender: 'Female',
    city: 'Los Angeles'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d729"),
    name: 'Benjamin',
    age: 27,
    gender: 'Male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d72a"),
    name: 'Mila',
    age: 29,
    gender: 'Female',
    city: 'Berlin'
  },
  {
    _id: ObjectId("65547c21831f5bd5c913d72c"),
    name: 'Raja',
    age: 23,
    gender: 'Male',
    city: 'Jaffna'
  }
]``

**10.Find the customers who are older than age 25.**
``db.customerdetails.find({age:{$lt:25}})
[
  {
    _id: ObjectId("65547511831f5bd5c913d724"),
    name: 'Emily',
    age: 22,
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d726"),
    name: 'Sophia',
    age: 24,
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d728"),
    name: 'Olivia',
    age: 23,
    gender: 'Female',
    city: 'Los Angeles'
  },
  {
    _id: ObjectId("65547c21831f5bd5c913d72c"),
    name: 'Raja',
    age: 23,
    gender: 'Male',
    city: 'Jaffna'
  }
]``

**11.Retrieve the males who are less than 25.**
``db.customerdetails.find({gender:"Male",age:{$lt:25}})
[
  {
    _id: ObjectId("65547c21831f5bd5c913d72c"),
    name: 'Raja',
    age: 23,
    gender: 'Male',
    city: 'Jaffna'
  }
]``

**12.Update Francis age to 35, if Francis is not available upsert.**
``db.customerdetails.update({name:"Francis"},{$set:{age:35}},{upsert:true})
{
  acknowledged: true,
  insertedId: ObjectId("65547e40e5eb27e9526949e3"),
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 1
}``

**13.Retrieve males who are younger than 30 and older than25.**
``db.customerdetails.find({gender:"Male",age:{$gt:25,$lt:30}})
[
  {
    _id: ObjectId("65547511831f5bd5c913d725"),
    name: 'Daniel',
    age: 28,
    gender: 'Male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d727"),
    name: 'William',
    age: 26,
    gender: 'Male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d729"),
    name: 'Benjamin',
    age: 27,
    gender: 'Male',
    city: 'Toronto'
  }
]``

**14.Find a customer who is lesser than or equal to 23.**
``db.customerdetails.find({age:{$lte:23}})

  {
    _id: ObjectId("65547511831f5bd5c913d724"),
    name: 'Emily',
    age: 22,
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("65547511831f5bd5c913d728"),
    name: 'Olivia',
    age: 23,
    gender: 'Female',
    city: 'Los Angeles'
  },
  {
    _id: ObjectId("65547c21831f5bd5c913d72c"),
    name: 'Raja',
    age: 23,
    gender: 'Male',
    city: 'Jaffna'
  }
]``



