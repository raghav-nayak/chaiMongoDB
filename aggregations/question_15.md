### 15. List all the companies located in the USA with their corresponding user count.

```js
[
    {
        $match: {
            "company.location.country": "USA",
        },
    },
    {
        $group: {
            _id: "$company.title",
            userCount: {
                $sum: 1,
            },
        },
    },
]
```

output:
```js
[
	{
		"userCount": 1,
		"_id": "COMVEYER"
	},
	{
		"_id": "ZAGGLE",
		"userCount": 1
	},
	...
]
```
