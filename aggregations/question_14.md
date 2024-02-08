### 14. Find users who have both "enim" and "id" as their tags.

```js
[
    {
        $match: {
            "tags": {
                $all: ["enim", "id"] // $all checks whether all the given values are present in the tags or not
            }
        },
    }
]
```

output:
```js
all the 5 documents
```
