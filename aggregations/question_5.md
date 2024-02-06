### 5. Which country has highest number of registered users?

```js
[
    {
        $group: {
            _id: "$company.location.country",
            userCount: {
                $sum: 1,
            },
        },
    },
    {
        $sort: {
            userCount: -1,
        },
    },
    {
        $limit: 1
    }
]
```

output:
```js
{
  "_id": "Germany",
  "userCount": 261
}
```
