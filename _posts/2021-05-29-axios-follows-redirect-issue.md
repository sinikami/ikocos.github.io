---
title: Axios follows redirect issue
tags:
- XMLHttpRequest
- Axios
- Javascript
layout: post
categories:
- js
---

I was deal with follows redirect issue when using Axios package.

First of all, As you know redirect response involves  redirect status and location header.
and The develop environment is react + spring boot backend.

There are two issues.
- when redirect response from backend, it is always automatically doing redirection and I can not handle it like fetch library.
- when I set http status as 200 and send it with location, it does not show the location header.

I tried to override xhr library in Axios package. but I found out that it is also used  `XMLHTTPRequest` library, nothing special with it. and there is no away could handle redirection with `XMLHTTPRequest`.

After some research, I figured out that  `XMLHttpRequest` is  built-in browsers.  when it gets 302 status, browser will take it and redirect to location which is coming from headers.

Now, I was clear  with redirection issue, but what kind of reasons cause that the location header not shows up.
I tried to use different headers like `x-response-url`, `url` , but it does not work at all.
 
I was thinking, it is regarding to expose headers because of cross-origin request. so, I just add location header at backend server. surprisingly it works.

In conclusion, if you are going to handle redirection with `Axios` package. There is a solution, Just response `200` status with `location` header, then use window.location.href to redirect it and do not forget set expose headers if your front end is working at cross-origin environment.
