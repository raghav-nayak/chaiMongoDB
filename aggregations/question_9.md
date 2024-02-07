### 9. What are the names and age of users who are inactive and have "velit" as tag?

```js
[
    {
        $match: {
            $and: [{
                    isActive: false,
                },
                {
                    tags: "velit",
                },
            ],
        },
    },
    {
        $project: {
            name: 1,
            age: 1,
        },
    },
]
```


output:
```js
[
    {
        "_id": {
            "$oid": "65c131d401ae60255514fdc0"
        },
        "name": "Aurelia Gonzales",
        "age": 20
    },
    {
        "_id": {
            "$oid": "65c131d401ae60255514fdde"
        }
        "name": "Hahn Pope",
        "age": 21,

    }
]
```


you can write it without `$and` clause too.
```js
[
    {
        $match: {
            isActive: false,
            tags: "velit",
        },
    },
    {
        $project: {
            name: 1,
            age: 1,
        },
    },
]
```
