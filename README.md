X-XSS-Protection middleware
===========================
[![Build Status](https://travis-ci.org/helmetjs/x-xss-protection.svg?branch=master)](https://travis-ci.org/helmetjs/x-xss-protection)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com/)

[_Looking for a changelog?_](https://github.com/helmetjs/helmet/blob/master/HISTORY.md)

The `X-XSS-Protection` HTTP header is a basic protection against XSS. It was originally [by Microsoft](http://blogs.msdn.com/b/ieinternals/archive/2011/01/31/controlling-the-internet-explorer-xss-filter-with-the-x-xss-protection-http-header.aspx) but Chrome has since adopted it as well.

This middleware sets the `X-XSS-Protection` header. On modern browsers, it will set the value to `1; mode=block`. On old versions of Internet Explorer, this creates a vulnerability (see [here](http://hackademix.net/2009/11/21/ies-xss-filter-creates-xss-vulnerabilities/) and [here](http://technet.microsoft.com/en-us/security/bulletin/MS10-002)), and so the header is set to `0` to disable it.

# Installation

    npm install x-xss-protection --save
    
# Usage

```javascript
var xssFilter = require('x-xss-protection')
app.use(xssFilter())
```
# setOnOldIE

To force the header to be set to `1; mode=block` on all versions of IE, add the option:

```javascript
app.use(xssFilter({ setOnOldIE: true }))
// This has some security problems for old IE!
```
