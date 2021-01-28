
# LaserCatEyes DotNet SDK - currently in BETA program

**HttpClientListener.DotNetStandard** allows you to listen **outgoing** requests from you application *(Also .Net core version is avaliable).*

## Installation & Implementation of HttpClient Listener
1. LaserCatEyes is available through [Nuget](https://www.nuget.org/packages/LaserCatEyes.HttpClientListener/). Install [LaserCatEyes.HttpClientListener](https://www.nuget.org/packages/LaserCatEyes.HttpClientListener/) from the package manager console:
```
PM> Install-Package LaserCatEyes.HttpClientListener.DotNetStandard
```

2. In ``Startup`` class ``ConfigureServices`` method inject Endpoint Listener

### To listen all HttpClients
```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        if (CurrentEnvironment.IsDevelopment()) //This is a debugging tool, you don't want to run it in prodcution, right!?
        {
            //Seriously do NOT run it in production environment 
            services.AddLaserCatEyesHttpClientListener(MY_APP_KEY_FROM_LASER_CAT_EYES_PORTAL);
            //OR 
            //(more option will be available soon)
            services.AddLaserCatEyesHttpClientListener(option =>
            {
                option.AppKey = MY_APP_KEY_FROM_LASER_CAT_EYES_PORTAL;
                option.AspCoreEnvironment = "STAGE";
                option.Version = "1.2.3.4";
                option.BuildNumber = "1";
            });
        }
    }
```
or
### Listen only selected HttpClients
```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        if (CurrentEnvironment.IsDevelopment()) //This is a debugging tool, you don't want to run it in prodcution, right!?
        {
            //Seriously do NOT run it in production environment 
            services.AddLaserCatEyesHttpClientListener(MY_APP_KEY_FROM_LASER_CAT_EYES_PORTAL, listenAllHttpClients: false);
            services.AddHttpClient("myClient", c =>
            {
                //your settings
            }).AddHttpMessageHandler<LaserCatEyesHttpMessageHandler>();
        }
    }
```
## Author

<img src="https://www.betalgo.com/img/logo-dark.png" width="10px"> Betalgo, mail@betalgo.com
