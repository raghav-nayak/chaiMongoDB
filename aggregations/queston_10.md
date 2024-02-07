### 10. How many users have a phone number starting with "+1 (940)"?

```js
[
    {
        $match: {
            "company.phone": /^\+1 \(940\)/,
        },
    },
    {
        $count: "usersWithMatchingPhonePattern",
    },
]
```

output:
```js
{
	"usersWithMatchingPhonePattern": 5
}
```
