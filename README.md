English | [Vietnamese](./README_vi_VN.md)

# C-in-Depth
C# in Depth

# Self-Host ASP.NET Web API 1 (C#)

This tutorial shows how to host a web API inside a console application. ASP.NET Web API does not require IIS. You can self-host a web API in your own host process.

New applications should use OWIN to self-host Web API.

HTTP is not just for serving up web pages. HTTP is also a powerful platform for building APIs that expose services and data. HTTP is simple, flexible, and ubiquitous. Almost any platform that you can think of has an HTTP library, so HTTP services can reach a broad range of clients, including browsers, mobile devices, and traditional desktop applications.

App defines three GET actions:
| URI | Description |
| -- | -- | -- |
| /api/products | Get a list of all products. |
| /api/products/id | Get a product by ID. |
| /api/products/?category=category | Get a list of products by category. |

### (Optional) Add an HTTP URL Namespace Reservation

This application listens to http://localhost:8080/. By default, listening at a particular HTTP address requires administrator privileges. When you run the tutorial, therefore, you may get this error: "HTTP could not register URL http://+:8080/" There are two ways to avoid this error:

- Run Visual Studio with elevated administrator permissions, or
- Use Netsh.exe to give your account permissions to reserve the URL.

To use Netsh.exe, open a command prompt with administrator privileges and enter the following command:following command:

```bat
netsh http add urlacl url=http://+:8080/ user=machine\username
```

where machine\username is your user account.

When you are finished self-hosting, be sure to delete the reservation:

```bat
netsh http delete urlacl url=http://+:8080/
```

### Reference
https://learn.microsoft.com/en-us/aspnet/web-api/overview/older-versions/self-host-a-web-api

### Package & Dependencies

#### ClientApp
`Microsoft.AspNet.WebApi.Client` 5.2.9
`Newtonsoft.Json` 6.0.4

https://www.nuget.org/packages/Microsoft.AspNet.WebApi.Client

#### SelfHost
`Microsoft.AspNet.WebApi.Client` 5.2.9
`Microsoft.AspNet.WebApi.Core` 5.2.9
`Microsoft.AspNet.WebApi.SelfHost` 5.2.9
`Newtonsoft.Json` 6.0.4

This is a legacy package for hosting ASP.NET Web API within your own process (outside of IIS). Please use the Microsoft.AspNet.WebApi.OwinSelfHost package for new projects.
https://www.nuget.org/packages/Microsoft.AspNet.WebApi.SelfHost/


# Use OWIN to Self-Host ASP.NET Web API

Host ASP.NET Web API using OWIN to self-host the Web API framework.

Open Web Interface for .NET (OWIN) defines an abstraction between .NET web servers and web applications. OWIN decouples the web application from the server, which makes OWIN ideal for self-hosting a web application in your own process, outside of IIS.

### Package & Dependencies
`Microsoft.AspNet.WebApi.Client` 5.2.9
`Microsoft.AspNet.WebApi.Core` 5.2.9
`Microsoft.AspNet.WebApi.Owin` 5.2.9
`Microsoft.AspNet.WebApi.OwinSelfHost` 5.2.9
`Microsoft.Owin` 2.0.2
`Microsoft.Owin.Host.HttpListener` 2.0.2
`Microsoft.Owin.Hosting` 2.0.2
`Newtonsoft.Json` 6.0.4
`Owin` 1.0

https://www.nuget.org/packages/Microsoft.AspNet.WebApi.OwinSelfHost