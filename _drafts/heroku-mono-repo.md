---
layout: post
title: Fullstack mono repo deployment on Heroku node.js runtime
teaser: |
---

When building a full stack app (nodeJS), it is common to use the mono repo layout:

```
/full-stack-app
  client
  server
```

and upon deployment, the client side code is sent to the browser via server
code, which also handles the miscellaneous API requests. This offers the
advantages of not having to version control two separate repository and
having to sync their versions, especially for a small team.

The heroku node.js runtime however, assumes the presence of `package.json` file
in the root directory. When the repository is pushed to its server, it runs
`yarn/npm install` against that file, then run the optional `build` scripts,
and eventually run `start` script to serve HTTP requests.

Obviously, the mono repo layout wouldn't work directly with the heroku set up.
There are many ways to get around with it, but I find most of them hacky and
inconvenient. Ideally, we want to maximize the workflow Heroku suggests and
handle everything via a `build` and `start` step.

The most elegant solution I found is yarn workspaces with Yarn 1. (There's an official heroku blog
[post](https://blog.heroku.com/building-a-monorepo-with-yarn-2) demonstrating
how to accomplish it with Yarn 2, but it turns out yarn 1 works just as fine,
minus the quirks that came with the version update.)

To get started with yarn workspaces, follow this
[guide](https://classic.yarnpkg.com/en/docs/workspaces/). We would have the
following folder structure:

```
/full-stack-app
  package.json
  client/
    package.json
  server/
    package.json
```

In the top level `package.json`, we define the workspaces as follows:

```
  {
    ...,
    "private":true,
    "workspaces":[
      "client",
      "server"
    ]
  }
```

> note: the name of the workspaces (inside the array) must match
> the `name` field defined in their respective `package.json`, rather than
> the folder name. Also, "private" key must be set to true

When this is set up, commands in the sub folder can be invoked directly from
the top levels. The following two is equivalent:

Inside `full-stack-app/client`:

```
$ yarn add some-module
$ yarn run start
```

Inside `full-stack-app/`:

```
$ yarn workspace client add some-module
$ yarn workspace client run start
```

Running `yarn install` in the top folder will also install the dependencies
from both subfolders. Additionally, it will group the overlapping dependency
into one top level `node_modules`, and save the distinct ones in their respective
`node_modules`.

The same works for custom command as well. If we have specified the following
in the `server` subfolder's `package.json`:

```
{
  "scripts":{
    "customCommand":"echo hi"
  }
}
```

We can invoke it from the top level folder by calling
`yarn workspace server run customCommand`.

This way we fulfill the heroku's requirement to have a `package.json` in the
root. And we can set up the build and start script to follow its recommended
workflow:

```
{
  "scripts":{
    "build": "yarn workspace client run build",
    "start": "yarn workspace server run start"
  }
}
```
