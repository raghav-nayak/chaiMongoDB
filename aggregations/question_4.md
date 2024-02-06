##### 4. Find the total number of males and females

```js
[{
    $group: {
        _id: "$gender",
        count: {
            $sum: 1
        }
    }
}]
```

output:
```js
{
  "_id": "female",
  "count": 507
}
{
  "_id": "male",
  "count": 493
}
```
