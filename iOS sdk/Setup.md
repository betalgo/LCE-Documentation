## Installation & Implementation 
1. LaserCatEyes is available through [CocoaPods](https://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
  pod 'LaserCatEyes'
```

2. In ``AppDelegate``'s ``didFinishLaunchingWithOptions`` method add 
```
  LaserCatManager.shared.startLogging(appKeyId: {APP_KEY})
```

3. If you want to stop Logging call 

  ```
  LaserCatManager.shared.stopLogging()
  ```

Note: You can monitor only Alamofire network data with this SDK.

[Laser-Cat-Eyes web portal]: <https://portal.lasercateyes.com/auth/login>


## Author

<img src="https://www.betalgo.com/img/logo-dark.png" width="10px"> Betalgo, mail@betalgo.com
