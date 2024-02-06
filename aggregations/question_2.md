### 2. What is the average age of all users?

answer:
here null means everything. That means it will put everything as a single document.

```js
[{
	$group: {
		_id: null,
		averageAge: { // creates a new field
			$avg: "$age"
		}
	}
}]
```

output:
```js
{
	"_id": null,
	"averageAge": 29.835
}
```


if you want to group by gender and then their avg
```js
[{
	$group: {
		_id: "$gender",
		averageAge: { // creates a new field
			$avg: "$age"
		}
	}
}]
```

output:
```js
{
  "averageAge": 29.81854043392505,
  "_id": "female"
},
{
  "_id": "male",
  "averageAge": 29.851926977687626
}
```
