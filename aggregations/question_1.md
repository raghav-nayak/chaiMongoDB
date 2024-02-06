### 1. How many users are active?
answer:
```js
[
  // first stage
  {
    $match: {
      isActive: true
    }
  },
  {
    $count: "activeUsers"
  }
]
```

output:
```js
{
  "activeUsers": 516
}
```

when you run the above pipeline, it will give the result in a new field called `activeUsers` which can be passed on to the next state.