### 8. How many users have 'enim' as one of the tags?

```js
[
	{
        $match: {
            tags: "enim" // search "enim" in "tags" field
        }
    },
    {
        $count: "userWithEnimTag"
    }
]
```

output:
```js
{
	"userWithEnimTag": 62
}
```
