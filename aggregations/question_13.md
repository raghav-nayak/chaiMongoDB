### 13. How many users have "ad" as the second tag in their list of tags?


```js
[
    {
        $match: {
            "tags.1": "ad", // tags.1 -> 2nd element in the tags array
        },
    },
    {
        $count: "secondTagAd",
    },
]
```

output:
```js
{
	"secondTagAd": 12
}
```

