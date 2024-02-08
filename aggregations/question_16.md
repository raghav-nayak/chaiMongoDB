## lookup

syntax:
```js
{
    $lookup: {
        from: collection,
        localField: field,
        foreignField: field,
        as: result
    }
}
```


### Join Books and Authors collections and get the author details.

```js
[
    {
        $lookup: {
            from: "authors",
            localField: "author_id",
            foreignField: "_id",
            as: "author_details"
        }
    }
]
```

output:
note that the author_details is an array
```js
{
    "_id": 1,
    "title": "The Great Gatsby",
    "author_id": 100,
    "genre": "Classic",
    "author_details": [
        {
            "_id": 100,
            "name": "F. Scott Fitzgerald",
            "birth_year": 1896
        }
    ]
}
```

### Get the name of the author from books in an object instead of array
```js
[
    {
        $lookup: {
            from: "authors",
            localField: "author_id",
            foreignField: "_id",
            as: "author_details"
        }
    },
    {
        $addFields: { // to add new field
            author_info: { // new field is added
                $first: "$author_details" // $first -> gives first element from author_details from previous stage
            }
        }
    }
]
```

output:
```js
{
    "_id": 1,
    "title": "The Great Gatsby",
    "author_id": 100,
    "genre": "Classic",
    "author_details": [
        {
            "_id": 100,
            "name": "F. Scott Fitzgerald",
            "birth_year": 1896
        }
    ],
    "author_info": {
        "_id": 100,
        "name": "F. Scott Fitzgerald",
        "birth_year": 1896
    }
}
```

### same thing can be written as 
```js
[
    {
        $lookup: {
            from: "authors",
            localField: "author_id",
            foreignField: "_id",
            as: "author_details"
        }
    },
    {
        $addFields: {
            author_info: {
                $arrayElemAt: ["$author_details", 0]
            }
        }
    }
]
```

output:
```js
{
    "_id": 1,
    "title": "The Great Gatsby",
    "author_id": 100,
    "genre": "Classic",
    "author_details": [
        {
            "_id": 100,
            "name": "F. Scott Fitzgerald",
            "birth_year": 1896
        }
    ],
    "author_info": {
        "_id": 100,
        "name": "F. Scott Fitzgerald",
        "birth_year": 1896
    }
}
```