### 11. Who has registered the most recently? 

```js
[
    {
        $sort: {
            registered: -1,
        },
    },
    {
        $limit: 2,
    },
    {
        $project: {
            name: 1,
            registered: 1,
        },
    },
]
```

output:
```js
[
    {
        "_id": {
            "$oid": "65c131d401ae602555150082"
        },
        "name": "Stephenson Griffith",
        "registered": {
            "$date": "2018-04-14T03:16:20.000Z"
        }
    },
    {
        "_id": {
            "$oid": "65c131d401ae60255514ff73"
        },
        "name": "Sonja Galloway",
        "registered": {
            "$date": "2018-04-11T12:52:12.000Z"
        }
    }
]
```
