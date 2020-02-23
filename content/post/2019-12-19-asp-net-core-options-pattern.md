---
title: "2019-12-19-Asp-Net-Core-Options-Pattern"
description: ""
date: "2019-12-18T21:54:37-06:00"
thumbnail: ""
categories:
  - "asp"
tags:
  - "asp.net"
  - ".net core"
draft: true
---
Dependency injection in ASP.NET Core is a wonderful thing.

Options Pattern:

https://weblog.west-wind.com/posts/2017/dec/12/easy-configuration-binding-in-aspnet-core-revisited

```
services.AddTransient(sp => sp.GetService<IOptions<AppSettings>>().Value);
```