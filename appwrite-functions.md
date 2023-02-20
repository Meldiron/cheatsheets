---
title: Appwrite Functions
prism_languages: [JavaScript]
tags: [Featured]
layout: 2017/sheet
---

### Running Locally (Functions G4)

```
1. Clone Appwrite: `git clone https://github.com/appwrite/appwrite.git`
2. Enter downloaded Appwrite folder `cd appwrite`
3. Switch branch to Functions G4: `git checkout feat-appwrite-router`
4. Ensure Appwrite is down, and wipe all data (users, projects..): `docker compose down -v`
5. Build Appwrite: `docker compose build`
6. Start Appwrite: `docker compose up -d`
7. Visit Console at [http://localhost/](http://localhost/)
```

### Function preview URLs

```
To use function preview URLs, visit domain: `[FUNCTION_ID].[PROJECT_ID].functions.localhost`, for example, `portfolio.matejbaco.functions.localhost`

- Make sure to have execute permissions as `any` on your functions. Otherwise preview URLs won't work.
```

### Hello World

```js
module.exports = async (context) => {
    return context.res.send('Hello Generation 4 👋');
}
```

### JSON Response

```js
module.exports = async (context) => {
    return context.res.json({
        message: 'Hello Generation 4 👋',
    });
}
```

### 404 Error Response

```js
module.exports = async (context) => {
    return context.res.send('Not Found', 404);
}
```

### Image Response

```js
const fs = require("fs");

module.exports = async (context) => {
    return context.res.send(fs.readFileSync('cat.png'), 200, {
        'content-type': 'image/png'
    });
}
```

### HTML Response

```js
module.exports = async (context) => {
    return context.res.send('<h1>Hello Appwrite</h1>', 200, {
        'content-type': 'text/html; charset=utf-8'
    });
}
```

### Reading String Body

```js
module.exports = async (context) => {
    const msg = `Your body is: ${context.req.bodyString}`;
    return context.res.send(msg);
}
```

### Reading JSON Body

```js
module.exports = async (context) => {
    // Ensure you send request with JSON body with "name" key. Also ensure you send header "content-type: application/json"
    const msg = `Your name is: ${context.req.body.name}`;
    return context.res.send(msg);
}
```

### URL-specific Response

```js
module.exports = async (context) => {
    const url = context.req.url;

    if(url === "/") {
        return context.res.send("Home page");
    } else if(url === "/contact") {
        return context.res.send("Contact page");
    } else {
        return context.res.send("Page not found!", 404);
    }
}
```

### Method-specific Response

```js
module.exports = async (context) => {
    const method = context.req.method;

    if(method === "GET") {
        return context.res.send("Getting user ...");
    } else if(method === "POST") {
        return context.res.send("Creating user ...");
    } else {
        return context.res.send("Unsupported method.", 500);
    }
}
```

### All Request Details

```js
module.exports = async (context) => {
    return context.res.json({
        url: context.req.url,
        port: context.req.port,
        path: context.req.path,
        query: context.req.query,
        queryString: context.req.queryString,
        scheme: context.req.scheme,
        host: context.req.host
    });
}
```

### Logging

```js
module.exports = async (context) => {
    context.log("Hey");
    context.log(42);
    context.log({ name: "Matej", age: 21 });

    context.error("Error log! No worries, it just logs. Execution is still succeessful");

    return context.res.empty(); // empty() gives no resonse body and status code 204
}
```

### Failing Execution

```js
module.exports = async (context) => {
    return context.res.send("", 500); // Status code 500 and above will be marked as failed
}
```

### Throwing Exception

```js
module.exports = async (context) => {
    throw new Error("Implement me first!");
    // No return needed. Response body is empty and status code is 500
}
```

## References
{: .-one-column}

* <https://github.com/appwrite/appwrite/pull/5096>
* <https://github.com/open-runtimes/open-runtimes/pull/136>