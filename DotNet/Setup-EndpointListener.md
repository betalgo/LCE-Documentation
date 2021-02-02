Currently in BETA program - [Github](https://github.com/betalgo/LCE-DotNet-SDK)

We have two different DotNet sdk. 
1. **Endpoint Listener** allows you to listen **incoming** requests to your application.
2. **HttpClientListener** allows you to listen **outgoing** requests from you application *(Also .Net standard version is avaliable).*

You can use both of them to get full visibility on your application. 

## Installation & Implementation of EnpointListener
LaserCatEyes is available through [Nuget](https://www.nuget.org/packages/LaserCatEyes.EndpointListener/). Install [LaserCatEyes.EndpointListener](https://www.nuget.org/packages/LaserCatEyes.EndpointListener/) from the package manager console:
```
PM> Install-Package LaserCatEyes.EndpointListener
```

2. In ``Startup`` class ``Configure`` method inject middleware
```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        ...
        if (env.IsDevelopment())//This is a debugging tool, you don't want to run it in prodcution, right!?
        {
           ... 
           //Seriously do NOT run it in production environment 
           app.UseLaserCatEyesEndpointListenerMiddleware();           
        }
       ...
    }
```
3. In ``Startup`` class ``ConfigureServices`` method inject Endpoint Listener

```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        ...
        if (env.IsDevelopment())//This is a debugging tool, you don't want to run it in prodcution, right!?
        {
           ... 
           //Seriously do NOT run it in production environment 
           services.AddLaserCatEyesEndpointListener(MY_APP_KEY_FROM_LASER_CAT_EYES_PORTAL);
           //OR 
           //(more option will be available soon)
           services.AddLaserCatEyesEndpointListener(option =>
           {
               option.AppKey = MY_APP_KEY_FROM_LASER_CAT_EYES_PORTAL;
               option.AspCoreEnvironment = "STAGE";
               option.Version = "1.2.3.4";
               option.BuildNumber = "1";
           });               
        }
       ...
    }
```


[Laser-Cat-Eyes web portal]: <https://portal.lasercateyes.com>
## Author

<img src="https://www.betalgo.com/img/logo-dark.png" width="10px"> Betalgo, mail@betalgo.com
