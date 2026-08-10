writeCode

Write code to execute below expressions.

1. Create a database named `blog`.

```sh
>  use blog
switched to db blog
```

2. Create a collection called 'articles'.

```sh
> db.createCollection("articles")
{ ok: 1 }
```

3. Insert multiple documents(at least 3) into articles. It should have fields

- title as string
- createdAt as date
- details as String
- author as nested object
  - author should have
    - name
    - email
    - age
    - example author: {name: 'abc', email: 'abc@gmail', age: 25}
- tags : Array of strings like ['html', 'css']

```js
// An article should look like in the database
{
  _id: 'some_random_id',
  title: '',
  details: '',
  author: {
    name: '',
    email: '',
    age: ''
  },
  tags: ['js', 'mongo']
}
```

```sh
> db.articles.insertMany([
    {
      title: 'Post 1',
      details: 'this is post details of post 1',
      author: {
        name: 'admin',
        email: 'admin@email.com',
        age: '24'
      },
      tags: ['html', 'css', 'js']
    },{
      title: 'Post 2',
      details: 'this is post details of post 2',
      author: {
        name: 'author',
        email: 'author@email.com',
        age: '21'
      },
      tags: ['js', 'mongo', 'node']
    },{
      title: 'Post 3',
      details: 'this is post details of post 3',
      author: {
        name: 'editor',
        email: 'editor@email.com',
        age: '20'
      },
      tags: ['react', 'node', 'js']
    },{
      title: 'Post 4',
      details: 'this is post details of post 4',
      author: {
        name: 'user',
        email: 'user@email.com',
        age: '18'
      },
      tags: ['js', 'mongo', 'node']
    },
])

{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("62ea0360c50478bb95e66c7e"),
    '1': ObjectId("62ea0360c50478bb95e66c7f"),
    '2': ObjectId("62ea0360c50478bb95e66c80"),
    '3': ObjectId("62ea0360c50478bb95e66c81")
  }
}
```

4. Find all the articles using `db.COLLECTION_NAME.find()`

```sh
> db.articles.find()
[
  {
    _id: ObjectId("62ea0360c50478bb95e66c7e"),
    title: 'Post 1',
    details: 'this is post details of post 1',
    author: { name: 'admin', email: 'admin@email.com', age: '24' },
    tags: [ 'html', 'css', 'js' ]
  },
  {
    _id: ObjectId("62ea0360c50478bb95e66c7f"),
    title: 'Post 2',
    details: 'this is post details of post 2',
    author: { name: 'author', email: 'author@email.com', age: '21' },
    tags: [ 'js', 'mongo', 'node' ]
  },
  {
    _id: ObjectId("62ea0360c50478bb95e66c80"),
    title: 'Post 3',
    details: 'this is post details of post 3',
    author: { name: 'editor', email: 'editor@email.com', age: '20' },
    tags: [ 'react', 'node', 'js' ]
  },
  {
    _id: ObjectId("62ea0360c50478bb95e66c81"),
    title: 'Post 4',
    details: 'this is post details of post 4',
    author: { name: 'user', email: 'user@email.com', age: '18' },
    tags: [ 'js', 'mongo', 'node' ]
  }
]
```

5. Find a document using \_id field.

```sh
> db.articles.findOne({_id: ObjectId("62ea0360c50478bb95e66c81")})
[
  {
    _id: ObjectId("62ea0360c50478bb95e66c81"),
    title: 'Post 4',
    details: 'this is post details of post 4',
    author: { name: 'user', email: 'user@email.com', age: '18' },
    tags: [ 'js', 'mongo', 'node' ]
  }
]
```

6. 1. Find documents using title

```sh
> db.articles.findOne({title: "Post 3"})
[
  {
    _id: ObjectId("62ea0360c50478bb95e66c80"),
    title: 'Post 3',
    details: 'this is post details of post 3',
    author: { name: 'editor', email: 'editor@email.com', age: '20' },
    tags: [ 'react', 'node', 'js' ]
  }
]
```

7. 2. Find documents using author's name field.

```sh
> db.articles.find({"author.name" : "user"})
[
  {
    _id: ObjectId("62ea0360c50478bb95e66c81"),
    title: 'Post 4',
    details: 'this is post details of post 4',
    author: { name: 'user', email: 'user@email.com', age: '18' },
    tags: [ 'js', 'mongo', 'node' ]
  }
]
```

8. Find document using a specific tag.

```sh
> db.articles.find({tags : "js"})
[
  {
    _id: ObjectId("62ea0360c50478bb95e66c7e"),
    title: 'Post 1',
    details: 'this is post details of post 1',
    author: { name: 'admin', email: 'admin@email.com', age: '24' },
    tags: [ 'html', 'css', 'js' ]
  },
  {
    _id: ObjectId("62ea0360c50478bb95e66c7f"),
    title: 'Post 2',
    details: 'this is post details of post 2',
    author: { name: 'author', email: 'author@email.com', age: '21' },
    tags: [ 'js', 'mongo', 'node' ]
  },
  {
    _id: ObjectId("62ea0360c50478bb95e66c80"),
    title: 'Post 3',
    details: 'this is post details of post 3',
    author: { name: 'editor', email: 'editor@email.com', age: '20' },
    tags: [ 'react', 'node', 'js' ]
  },
  {
    _id: ObjectId("62ea0360c50478bb95e66c81"),
    title: 'Post 4',
    details: 'this is post details of post 4',
    author: { name: 'user', email: 'user@email.com', age: '18' },
    tags: [ 'js', 'mongo', 'node' ]
  }
]
```

9. Update title of a document using its \_id field.

```sh
> db.articles.update({_id: ObjectId("62ea0360c50478bb95e66c80")}, {$set: {title: 'Full Stack Development'}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

> db.articles.find({title: "Full Stack Development"})
[
  {
    _id: ObjectId("62ea0360c50478bb95e66c80"),
    title: 'Full Stack Development',
    details: 'this is post details of post 3',
    author: { name: 'editor', email: 'editor@email.com', age: '20' },
    tags: [ 'react', 'node', 'js' ]
  }
]
```

10. Update a author's name using article's title.

```sh
> db.articles.update({title: "Post 4"}, {$set: {"author.name" : "sumanta"}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
blog> db.articles.find({title: "Post 4"})
[
  {
    _id: ObjectId("62ea0360c50478bb95e66c81"),
    title: 'Post 4',
    details: 'this is post details of post 4',
    author: { name: 'sumanta', email: 'user@email.com', age: '18' },
    tags: [ 'js', 'mongo', 'node' ]
  }
]
```

11. rename details field to description from all articles in articles collection.

```sh
> db.articles.updateMany({}, {$rename: {"details": "description"}}, {multi: true})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 4,
  modifiedCount: 0,
  upsertedCount: 0
}
```

12. Add additional tag in a specific document.

```sh
> db.articles.update({title: "Post 1"}, {$push: {"tags": "nodejs"}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

> db.articles.find({title: "Post 1"})
[
  {
    _id: ObjectId("62ea0360c50478bb95e66c7e"),
    title: 'Post 1',
    author: { name: 'admin', email: 'admin@email.com', age: '24' },
    tags: [ 'html', 'css', 'js', 'nodejs' ],
    description: 'this is post details of post 1'
  }
]
```

13. Update an article's title using $set and without $set.

- Write the differences here ?

> If $set is not used it updates the complete set of array with the element

13. find an article using title and increment it's auhtor's age by 5.

```sh
> db.articles.update({title: "Post 4"}, {$inc: {"author.age": 5}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```

14. Delete a document using \_id field with `db.COLLECTION_NAME.remove()`.

```sh
>db.articles.remove({_id: ObjectId("62ea0360c50478bb95e66c7f")})
{ acknowledged: true, deletedCount: 1 }
```

// Sample data

```js
db.users.insertMany([
  {
    age: 49,
    name: "Maurice Brock",
    email: "wuk@hibpiz.ch",
    gender: "Female",
    sports: ["cricket", "football"],
    scores: [24, 35, 18, 16],
    weight: 45,
  },
  {
    age: 37,
    birthday: "7/15/1986",
    name: "Virgie Cunningham",
    email: "ezogafa@de.gm",
    gender: "Male",
    sports: ["football"],
    scores: [17, 35, 43],
    weight: 52,
  },
  {
    age: 48,
    birthday: "5/14/1961",
    name: "Alexander Holt",
    email: "han@mu.pe",
    gender: "Male",
    sports: ["cricket", "football", "TT"],
    scores: [24, 30, 16],
    weight: 55,
  },
  {
    age: 53,
    birthday: "11/15/1963",
    name: "Derek Dawson",
    email: "polril@now.de",
    gender: "Male",
    sports: ["cricket", "hockey"],
    scores: [20, 15, 38, 23],
    weight: 49,
  },
  {
    age: 34,
    birthday: "7/24/1964",
    name: "Cynthia Cobb",
    email: "wujjarpob@jecimpar.gu",
    gender: "Female",
    sports: ["cricket"],
    scores: [41, 17, 28],
    weight: 51,
  },
  {
    age: 33,
    birthday: "10/26/1982",
    name: "Isabella Atkins",
    email: "ononuzas@givhoz.ca",
    gender: "Female",
    sports: ["cricket", "football", "hockey", "TT"],
    scores: [14, 38, 29, 45, 20],
    weight: 49,
  },
  {
    age: 47,
    birthday: "10/12/1978",
    name: "Katharine Bryan",
    email: "zo@pebi.sa",
    gender: "Male",
    sports: ["TT", "hockey", "khokho"],
    scores: [27, 20, 34],
    weight: 58,
  },
  {
    age: 41,
    birthday: "1/28/1991",
    name: "Beatrice Fleming",
    email: "ufufsa@pujizren.tk",
    gender: "Female",
    sports: ["football", "khokho"],
    scores: [30, 20, 15, 29, 43],
    weight: 47,
  },
  {
    age: 26,
    birthday: "3/23/1998",
    name: "Tom Fields",
    email: "wasodjow@ofaba.gf",
    gender: "Female",
    sports: ["khokho"],
    scores: [37, 29, 18, 43, 49],
    weight: 50,
  },
  {
    age: 33,
    birthday: "11/14/1960",
    name: "Steve Ortega",
    email: "dupus@ca.ls",
    gender: "Female",
    sports: ["cricket", "football", "hockey"],
    scores: [12, 15, 20],
    weight: 51,
  },
  {
    age: 24,
    birthday: "1/5/1994",
    name: "Suraj Kumar",
    weight: 50,
    gender: "Male",
    sports: ["football", "cricket", "TT"],
  },
]);
```

Insert above data into database to perform below queries:-

```sh
>{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("62ea0840c50478bb95e66c82"),
    '1': ObjectId("62ea0840c50478bb95e66c83"),
    '2': ObjectId("62ea0840c50478bb95e66c84"),
    '3': ObjectId("62ea0840c50478bb95e66c85"),
    '4': ObjectId("62ea0840c50478bb95e66c86"),
    '5': ObjectId("62ea0840c50478bb95e66c87"),
    '6': ObjectId("62ea0840c50478bb95e66c88"),
    '7': ObjectId("62ea0840c50478bb95e66c89"),
    '8': ObjectId("62ea0840c50478bb95e66c8a"),
    '9': ObjectId("62ea0840c50478bb95e66c8b"),
    '10': ObjectId("62ea0840c50478bb95e66c8c")
  }
}
```

- Find all males who play cricket.

```sh
> db.users.find({gender: "Male"})
[
  {
    _id: ObjectId("62ea0840c50478bb95e66c83"),
    age: 37,
    birthday: '7/15/1986',
    name: 'Virgie Cunningham',
    email: 'ezogafa@de.gm',
    gender: 'Male',
    sports: [ 'football' ],
    scores: [ 17, 35, 43 ],
    weight: 52
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c84"),
    age: 48,
    birthday: '5/14/1961',
    name: 'Alexander Holt',
    email: 'han@mu.pe',
    gender: 'Male',
    sports: [ 'cricket', 'football', 'TT' ],
    scores: [ 24, 30, 16 ],
    weight: 55
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c85"),
    age: 53,
    birthday: '11/15/1963',
    name: 'Derek Dawson',
    email: 'polril@now.de',
    gender: 'Male',
    sports: [ 'cricket', 'hockey' ],
    scores: [ 20, 15, 38, 23 ],
    weight: 49
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c88"),
    age: 47,
    birthday: '10/12/1978',
    name: 'Katharine Bryan',
    email: 'zo@pebi.sa',
    gender: 'Male',
    sports: [ 'TT', 'hockey', 'khokho' ],
    scores: [ 27, 20, 34 ],
    weight: 58
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c8c"),
    age: 24,
    birthday: '1/5/1994',
    name: 'Suraj Kumar',
    weight: 50,
    gender: 'Male',
    sports: [ 'football', 'cricket', 'TT' ]
  }
]
```

- Update user with extra golf field in sports array whose name is "Steve Ortega".

```sh
>  db.users.update({name: "Steve Ortega"}, {$push:{sports: "golf"} })
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
> db.users.find({name: "Steve Ortega"})
[
  {
    _id: ObjectId("62ea0840c50478bb95e66c8b"),
    age: 33,
    birthday: '11/14/1960',
    name: 'Steve Ortega',
    email: 'dupus@ca.ls',
    gender: 'Female',
    sports: [ 'cricket', 'football', 'hockey', 'golf' ],
    scores: [ 12, 15, 20 ],
    weight: 51
  }
]
```

- Find all users who play either 'football' or 'cricket'.

```sh
> db.users.find({sports: {$in : ['cricket', 'football']}})
[
  {
    _id: ObjectId("62ea0840c50478bb95e66c82"),
    age: 49,
    name: 'Maurice Brock',
    email: 'wuk@hibpiz.ch',
    gender: 'Female',
    sports: [ 'cricket', 'football' ],
    scores: [ 24, 35, 18, 16 ],
    weight: 45
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c83"),
    age: 37,
    birthday: '7/15/1986',
    name: 'Virgie Cunningham',
    email: 'ezogafa@de.gm',
    gender: 'Male',
    sports: [ 'football' ],
    scores: [ 17, 35, 43 ],
    weight: 52
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c84"),
    age: 48,
    birthday: '5/14/1961',
    name: 'Alexander Holt',
    email: 'han@mu.pe',
    gender: 'Male',
    sports: [ 'cricket', 'football', 'TT' ],
    scores: [ 24, 30, 16 ],
    weight: 55
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c85"),
    age: 53,
    birthday: '11/15/1963',
    name: 'Derek Dawson',
    email: 'polril@now.de',
    gender: 'Male',
    sports: [ 'cricket', 'hockey' ],
    scores: [ 20, 15, 38, 23 ],
    weight: 49
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c86"),
    age: 34,
    birthday: '7/24/1964',
    name: 'Cynthia Cobb',
    email: 'wujjarpob@jecimpar.gu',
    gender: 'Female',
    sports: [ 'cricket' ],
    scores: [ 41, 17, 28 ],
    weight: 51
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c87"),
    age: 33,
    birthday: '10/26/1982',
    name: 'Isabella Atkins',
    email: 'ononuzas@givhoz.ca',
    gender: 'Female',
    sports: [ 'cricket', 'football', 'hockey', 'TT' ],
    scores: [ 14, 38, 29, 45, 20 ],
    weight: 49
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c89"),
    age: 41,
    birthday: '1/28/1991',
    name: 'Beatrice Fleming',
    email: 'ufufsa@pujizren.tk',
    gender: 'Female',
    sports: [ 'football', 'khokho' ],
    scores: [ 30, 20, 15, 29, 43 ],
    weight: 47
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c8b"),
    age: 33,
    birthday: '11/14/1960',
    name: 'Steve Ortega',
    email: 'dupus@ca.ls',
    gender: 'Female',
    sports: [ 'cricket', 'football', 'hockey', 'golf' ],
    scores: [ 12, 15, 20 ],
    weight: 51
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c8c"),
    age: 24,
    birthday: '1/5/1994',
    name: 'Suraj Kumar',
    weight: 50,
    gender: 'Male',
    sports: [ 'football', 'cricket', 'TT' ]
  }
]
```

- Find all users whose name includes 'ri' in their name.

```sh
>  db.users.find({ name: /ri/i })
[
  {
    _id: ObjectId("62ea0840c50478bb95e66c82"),
    age: 49,
    name: 'Maurice Brock',
    email: 'wuk@hibpiz.ch',
    gender: 'Female',
    sports: [ 'cricket', 'football' ],
    scores: [ 24, 35, 18, 16 ],
    weight: 45
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c88"),
    age: 47,
    birthday: '10/12/1978',
    name: 'Katharine Bryan',
    email: 'zo@pebi.sa',
    gender: 'Male',
    sports: [ 'TT', 'hockey', 'khokho' ],
    scores: [ 27, 20, 34 ],
    weight: 58
  },
  {
    _id: ObjectId("62ea0840c50478bb95e66c89"),
    age: 41,
    birthday: '1/28/1991',
    name: 'Beatrice Fleming',
    email: 'ufufsa@pujizren.tk',
    gender: 'Female',
    sports: [ 'football', 'khokho' ],
    scores: [ 30, 20, 15, 29, 43 ],
    weight: 47
  }
]
```
