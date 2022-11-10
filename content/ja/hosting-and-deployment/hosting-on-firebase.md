---
aliases: []
authors:
- Michel Racic
categories:
- hosting and deployment
date: "2017-03-12"
description: You can use Firebase's free tier to host your static website; this also
  gives you access to Firebase's NOSQL API.
draft: true
keywords:
- hosting
- firebase
linktitle: Host on Firebase
menu:
  docs:
    parent: hosting-and-deployment
    weight: 20
publishdate: "2017-03-12"
sections_weight: 20
title: Host on Firebase
toc: true
weight: 20
---

## Assumptions

1. You have an account with [Firebase][signup]. (If you don't, you can sign up for free using your Google account.)
2. You have completed the [Quick Start][] or have a completed Hugo website ready for deployment.

## Initial setup

Go to the [Firebase console][console] and create a new project (unless you already have a project). You will need to globally install `firebase-tools` (node.js):

```txt
npm install -g firebase-tools
```

Log in to Firebase (setup on your local machine) using `firebase login`, which opens a browser where you can select your account. Use `firebase logout` in case you are already logged in but to the wrong account.


```txt
firebase login
```

In the root of your Hugo project, initialize the Firebase project with the `firebase init` command:

```txt
firebase init
```

From here:

1. Choose Hosting in the feature question
2. Choose the project you just set up
3. Accept the default for your database rules file
4. Accept the default for the publish directory, which is `public`
5. Choose "No" in the question if you are deploying a single-page app

## Deploy

To deploy your Hugo site, execute the `firebase deploy` command, and your site will be up in no time:

```txt
hugo && firebase deploy
```

## CI Setup

You can generate a deploy token using

```txt
firebase login:ci
```

You can also set up your CI (e.g., with Wercker) and add the token to a private variable like `$FIREBASE_DEPLOY_TOKEN`.

{{% note %}}
This is a private secret and it should not appear in a public repository. Make sure you understand your chosen CI and that it's not visible to others.
{{% /note %}}

You can then add a step in your build to do the deployment using the token:

```txt
firebase deploy --token $FIREBASE_DEPLOY_TOKEN
```

## Reference links

* [Firebase CLI Reference](https://firebase.google.com/docs/cli/#administrative_commands)

[console]: https://console.firebase.google.com
[Quick Start]: /getting-started/quick-start/
[signup]: https://console.firebase.google.com/
