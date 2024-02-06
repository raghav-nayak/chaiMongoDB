##### 6. List all unique eye colors present in the collection.

```js
[
    {
        $group: {
            _id: "$eyeColor"
        }
    }
]
```

output:
```js
{
  "_id": "blue"
},
{
  "_id": "brown"
},
{
  "_id": "green"
}
```
