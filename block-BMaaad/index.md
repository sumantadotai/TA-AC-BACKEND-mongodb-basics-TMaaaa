writeCode

Write command to

- List collections from a database.

```sh
> show dbs
```

- create a new collection in your country database which you created recently.

```sh
> use india
> db.createCollection("states")
```

Write code to:-

- crate a database named `weather`

```sh
> use weather
```

- create a capped collection named `temperature` with maximum of 3 documents and try inserting more than 3 to see the result.

```sh
> weather>  db.createCollection("temperature", { capped: true, size: 3})
{ ok: 1 }
weather> db.temperature.insert({city: "hyderabad"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("62e67fd364af57ae48211daa") }
}
weather> db.temperature.insert({city: "mumbai"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("62e67fd664af57ae48211dab") }
}
weather> db.temperature.insert({city: "delhi"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("62e67fda64af57ae48211dac") }
}
weather> db.temperature.insert({city: "kolkata"})
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("62e67fe064af57ae48211dad") }
}
weather> db.temperature.find()
[
  { _id: ObjectId("62e67fd664af57ae48211dab"), city: 'mumbai' },
  { _id: ObjectId("62e67fda64af57ae48211dac"), city: 'delhi' },
  { _id: ObjectId("62e67fe064af57ae48211dad"), city: 'kolkata' }
]

//Old Data Getting Removed
```

- create a simple collection named `humidity`

```sh
> db.createCollection("humidity");
{ ok: 1 }
```

- check whether `temperature` collection is capped or not ?

```sh
>db.temperature.stats()
{
  ns: 'weather.temperature',
  size: 117,
  count: 3,
  avgObjSize: 39,
  numOrphanDocs: 0,
  storageSize: 20480,
  freeStorageSize: 0,
  capped: true, //Its Capped  Collection
  max: 3,
  maxSize: 256,
  wiredTiger: {
    metadata: { formatVersion: 1 },
```

- Delete `humidity` collection and then the entire database(weather).

```sh
> db.humidity.drop()
true
> db.dropDatabase()
{ ok: 1, dropped: 'weather' }
```
