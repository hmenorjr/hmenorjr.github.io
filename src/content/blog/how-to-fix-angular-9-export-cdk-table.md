---
title: 'How to Fix Angular 9 Export CDK_Table'
description: 'I was containerizing the front-end of a web application that was built in Angular 9 with Bootstrap and Angular Material. It was working on my local terminal. However, when I containerized it, several warnings and this error occurs.'
pubDate: '2020-05-19'
heroImage: '../../images/blog-export-cdk-table-error.webp'
featured: true
---

## What I Did?

Of course, Googled my way into it. Tried several blogs:

* Cleared the node_modules/
* Add/Save the plugin…
* Deleted the package-lock.json
* Clear the cache, etc…

Any possible solution that worked on some but doesn’t worked on me.

## Wait a minute

After reading some blogs again, one caught my attention and noticed the writer just executed the following:

First: ``$ npm install @angular/core``

And then: ``$ npm install @angular/common``

And lastly: ``npm install @angular/``

However, when I opened the ``package.json``… It’s already installed.

## What now?

I tried to rearrange the lines of dependency.

Before:

```json
"private": true,
  "dependencies": {
    "@angular/animations": "~9.0.5",
    "@angular/cdk": "^9.2.1", <--- attention
    "@angular/compiler": "~9.0.5",
    "@angular/forms": "~9.0.5",
    "@angular/material": "^9.1.1",
    "@angular/platform-browser": "~9.0.5",
    "@angular/platform-browser-dynamic": "~9.0.5",
    "@angular/router": "~9.0.5",
    "@angular/core": "~9.0.5", <--- attention
    "@angular/common": "~9.0.5", <--- attention
    "angular-material": "^1.1.21",
    "angular-ng-autocomplete": "latest",
    "bootstrap": "^4.4.1",
    "lodash": "^4.17.15",
    "rxjs": "~6.5.4",
    "sweetalert2": "^9.7.0",
    "tslib": "^1.11.1",
    "zone.js": "~0.10.2"
```

After:

```json
"private": true,
  "dependencies": {
    "@angular/animations": "~9.0.5",
    "@angular/core": "~9.0.5", <--- attention
    "@angular/common": "~9.0.5", <--- attention
    "@angular/cdk": "^9.2.1", <--- attention
    "@angular/compiler": "~9.0.5",
    "@angular/forms": "~9.0.5",
    "@angular/material": "^9.1.1",
    "@angular/platform-browser": "~9.0.5",
    "@angular/platform-browser-dynamic": "~9.0.5",
    "@angular/router": "~9.0.5",
    "angular-material": "^1.1.21",
    "angular-ng-autocomplete": "latest",
    "bootstrap": "^4.4.1",
    "lodash": "^4.17.15",
    "rxjs": "~6.5.4",
    "sweetalert2": "^9.7.0",
    "tslib": "^1.11.1",
    "zone.js": "~0.10.2"
```

Noticed the highlighted lines? For some reason the when ``@angular/cdk`` was added it was inserted at the top. 

Seems like all new plugins that were saved were at the top. But during npm install that’s not the case.

The Result?

* Most of the warnings were gone
* The `CDK_Table` issue was gone

Thank you for reading, hope this helped you solve this issue:

```sh
export 'CDK_TABLE' was not found in '@angular/cdk/table'
```

### Support me by [buying me a coffee](https://coff.ee/hmenorjr)
