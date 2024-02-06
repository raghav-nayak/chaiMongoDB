### 3. List the top 2 most common favorite fruits.

```js
[
	{
		$group: {
			_id: "$favoriteFruit",
			// note that it is not $count; count is a new field; it is not in the original db
			count: {
				//  add 1 if you find the matching category; sum = sum + 1
				$sum: 1, 
			},
		},
	},
	{
		$sort: {
			count: -1, // desc order
		},
	},
	{
		$limit: 2, // limit result to 2 
	},
]
```

output:
```js
{
  "_id": "banana",
  "count": 339
},
{
  "_id": "apple",
  "count": 338
}
```
