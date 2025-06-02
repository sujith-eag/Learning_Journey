
```bash
mkdir server
cd server

npm init
npm install express
```

[package.JSON](https://docs.npmjs.com/cli/v11/configuring-npm/package-json)


```js
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})

```