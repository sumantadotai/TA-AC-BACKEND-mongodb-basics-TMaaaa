writeCode

Write code to:-

- create a database named `sports`.

```sh
> use sports
switched to db sports
```

- list all databases present in local mongod server.

```sh
> show dbs
admin    40.00 KiB
config  108.00 KiB
local    40.00 KiB
```

- create 3 collections named `cricket`, `football`, `TT` in sports databse.

```sh
> db.createCollection("cricket")
{ ok: 1 }
> db.createCollection("football")
{ ok: 1 }
> db.createCollection("TT")
{ ok: 1 }
```

- add multiple players in those collections which should have fields like `name`, `age` and `email` and `bid_price`.

```sh
//For Cricket
> db.cricket.insert({"name": "Player 1","age": 20,"email": "player1@email.com","bid_price": "1cr"})
> db.cricket.insert({"name": "Player 2","age": 22,"email": "player2@email.com","bid_price": "1.5cr"})
> db.cricket.insert({"name": "Player 3","age": 24,"email": "player3@email.com","bid_price": "3cr"})
> db.cricket.insert({"name": "Player 4","age": 27,"email": "player4@email.com","bid_price": "2cr"})

//For Football
> db.football.insert({"name": "Player 5","age": 20,"email": "player5@email.com","bid_price": "50L"})
> db.football.insert({"name": "Player 6","age": 19,"email": "player6@email.com","bid_price": "5cr"})
> db.football.insert({"name": "Player 7","age": 15,"email": "player7@email.com","bid_price": "3cr"})
> db.football.insert({"name": "Player 8","age": 18,"email": "player8@email.com","bid_price": "2.2cr"})

//For TT
> db.TT.insert({"name": "Player 9","age": 32,"email": "player9@email.com","bid_price": "1.3cr"})
> db.TT.insert({"name": "Player 10","age": 22,"email": "player11@email.com","bid_price": "1.7cr"})
> dbT.insert({"name": "Player 11","age": 28, "email" : "player11@email.com","bid_price": "2cr"})
> db.TT.insert({"name": "Player 12","age": 22,"email": "player12@email.com","bid_price": "4cr"})
> db.TT.insert({"name": "Player 13","age": 27,"email": "player13@email.com","bid_price": "3.5cr"})
```

- list all collections in sports database.

```sh
>show collections
cricket
football
TT
```

- rename `TT` collection to `tennis`.

```sh
>db.TT.renameCollection("tennis")
{ ok: 1 }
```

- create a capped collection called `khokho` which should have max 3 documents.

```sh
>db.createCollection("khokho", {capped: true, size: 3})
{ ok: 1 }
```

Try inserting more than 3 and see what happens?

```sh
>db.khokho.insert({"name": "Player 14","age": 15,"email": "player14@email.com","bid_price": "1.3cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("62e686c74411f58825fd4b29") }
}
sports> db.khokho.insert({"name": "Player 15","age": 22,"email": "player15@email.com","bid_price": "2.3cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("62e686d44411f58825fd4b2a") }
}
sports> db.khokho.insert({"name": "Player 26","age": 26,"email": "player16@email.com","bid_price": "1.5cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("62e686e54411f58825fd4b2b") }
}
sports> db.khokho.insert({"name": "Player 17","age": 20,"email": "player17@email.com","bid_price": "1.7cr"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("62e686fa4411f58825fd4b2c") }
}
sports> db.khokho.find()
[
  {
    _id: ObjectId("62e686e54411f58825fd4b2b"),
    name: 'Player 26',
    age: 26,
    email: 'player16@email.com',
    bid_price: '1.5cr'
  },
  {
    _id: ObjectId("62e686fa4411f58825fd4b2c"),
    name: 'Player 17',
    age: 20,
    email: 'player17@email.com',
    bid_price: '1.7cr'
  }
]

//older data getting removed
```

- check whether a collection is capped or not?

```sh
> db.football.stats()
{
  ns: 'sports.football',
  size: 394,
  count: 4,
  avgObjSize: 98,
  numOrphanDocs: 0,
  storageSize: 36864,
  freeStorageSize: 16384,
  capped: false,  //not capped
  wiredTiger: {
    metadata: { formatVersion: 1 },

> db.khokho.stats()
{
  ns: 'sports.khokho',
  size: 204,
  count: 2,
  avgObjSize: 102,
  numOrphanDocs: 0,
  storageSize: 36864,
  freeStorageSize: 16384,
  capped: true,   //  its capped
  max: 0,
  maxSize: 256,
  wiredTiger: {
    metadata: { formatVersion: 1 },
```

- drop all documents from `football` collection.

```sh
>db.football.remove({})
{ acknowledged: true, deletedCount: 4 }
```

- delete cricket collection completely.

```sh
>db.cricket.drop()
true
```

- delete sports database.

```sh
>db.dropDatabase()
{ ok: 1, dropped: 'sports' }
```

- check which database you are connected to ?

```sh
> db
sports
```

- connect to test database

```sh
>use test
switched to db test
```
