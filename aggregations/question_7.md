### 7. What is the average number of tags per user?

use `$unwind` operator for arrays.
Syntax is 
```js
$unwind: {
      path: path,
      includeArrayIndex: 'string',
      preserveNullAndEmptyArrays: boolean
    }
```

What it will do is the same array is spread with different values in the tags field.

```js
[
    {
        $unwind: {
            path: "$tags"
        }
    },
    {
        $group: {
            _id: "$_id",
            numberOfTags: {
                $sum: 1
            }
        }
    },
    {
        $group: {
            _id: null,
            averageNumberOfTags: {
                $avg: "$numberOfTags"
            }
        }
    }
]
```

output:
```js
{
	"averageNumberOfTags": 3.556,
	"_id": null
}
```


another way
using addFields

```js
{
    $addFields: {
      newField: expression, ...
    }
}
```

```js
[
    {
        $addFields: {
            numberOfTags: {
                $size: {
                    $ifNull: ["$tags", []]
                }
            }
        }
    },
    {
        $group: {
            _id: null,
            averageNumberOftags: {
                $avg: "$numberOfTags"
            }
        }
    }
]
```
