writeCode

Write code to:-

- create a database named `mountains`

```sh
> use mountains
switched to db mountains
```

- a collection inside that database named `himalayas`

```sh
> db.createCollection("himalayas")
```

- insert 1 document into that collection `{name: 'Dhauldhar range', height: '4000 mtrs'}`

```sh
> db.himalayas.insert({name: 'Dhauldhar range', height: '4000 mtrs'})
```

- insert multiple document using insertMany command

```sh
>var mountain = [
    {
        name:"Everest",
        height:"8849.868"
    },
    {
        name:"Kangchenjunga",
        height:"8585.9112"
    },
     {
        name:"Dhaulagiri",
        height:"8167.116"
    },
    {
        name:"Annapurna",
        height:"8090.916"
    }
]
>db.himalayas.insertMany(mountain)
```

- find all documents from mountains

```sh
> db.himalayas.find().pretty()
[
  {
    _id: ObjectId("62e96a8f705122be04f4a383"),
    name: 'Dhauldhar range',
    height: '4000 mtrs'
  },
  {
    _id: ObjectId("62e96a9a705122be04f4a384"),
    name: 'Everest',
    height: '8849.868'
  },
  {
    _id: ObjectId("62e96a9a705122be04f4a385"),
    name: 'Kangchenjunga',
    height: '8585.9112'
  },
  {
    _id: ObjectId("62e96a9a705122be04f4a386"),
    name: 'Dhaulagiri',
    height: '8167.116'
  },
  {
    _id: ObjectId("62e96a9a705122be04f4a387"),
    name: 'Annapurna',
    height: '8090.916'
  }
]
```

- find a single document using name

```sh
> db.himalayas.find({name: "Everest"})
[
  {
    _id: ObjectId("62e96a9a705122be04f4a384"),
    name: 'Everest',
    height: '8849.868'
  }
]
```
