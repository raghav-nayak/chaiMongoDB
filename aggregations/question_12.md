### 12. Categorize users by their favorite fruit

```js
[
    {
        $group: {
            _id: "$favoriteFruit",
            users: {
                $push: "$name",
            },
        },
    }
]
```

output:
```js
[
    {
        "_id": "banana",
        "users": [
            "Aurelia Gonzales",
            ...
        ]
    },
    {
        "_id": "apple",
        "users": [
            "Kitty Snow",
            ...
        ]
    },
    {
        "_id": "strawberry",
        "users": [
            "Hays Wise",
            ...
        ]
    }
]
```
