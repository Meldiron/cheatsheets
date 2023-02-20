---
title: Appwrite Functions
prism_languages: [JavaScript]
tags: [Featured]
layout: 2017/sheet
---

### Running Locally (Functions G4)

1. Clone Appwrite: `git clone https://github.com/appwrite/appwrite.git`
2. Enter downloaded Appwrite folder `cd appwrite`
3. Switch branch to Functions G4: `git checkout feat-appwrite-router`
4. Ensure Appwrite is down, and wipe all data (users, projects..): `docker compose down -v`
5. Build Appwrite: `docker compose build`
6. Start Appwrite: `docker compose up -d`
7. Visit Console at [http://localhost/](http://localhost/)

### Function preview URLs

To use function preview URLs, visit domain: `[FUNCTION_ID].[PROJECT_ID].functions.localhost`, for example, `portfolio.matejbaco.functions.localhost`

> Make sure to have execute permissions as `any` on your functions. Otherwise preview URLs won't work.

### Hello World

```js
module.exports = async (context) => {
    return context.res.json({
        message: 'Hello Generation 4 👋',
    });
}
```

## References
{: .-one-column}

* <https://github.com/appwrite/appwrite/pull/5096>
* <https://github.com/open-runtimes/open-runtimes/pull/136>