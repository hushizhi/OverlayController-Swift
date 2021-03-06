# OverlayController-Swift
[![Swift 3.0](https://img.shields.io/badge/Swift-3.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
![enter image description here](https://img.shields.io/badge/pod-v0.0.1-brightgreen.svg)
![enter image description here](https://img.shields.io/badge/platform-iOS%208.0%2B-ff69b5152950834.svg) 
<a href="https://github.com/snail-z/OverlayController-Swift/blob/master/LICENSE"><img src="https://img.shields.io/badge/license-MIT-green.svg?style=flat"></a>
  
OverlayController is an implementation of a overlay effect for any view. It can be used to easily add dynamics to user interactions and popups views.

#### [Objective-C version is here.](https://github.com/snail-z/SnailQuickMaskPopups.git)

## Installation
To install OverlayController using [CocoaPods](https://cocoapods.org "CocoaPods" ), please integrate it in your existing Podfile, or create a new Podfile:

```ruby
    platform :ios, '8.0'
    use_frameworks!

    target 'You Project' do
      pod 'OverlayController', '~> 0.0.2'
    end
```
Then run pod install.

## Example
![image](https://github.com/snail-z/OverlayController-Swift/blob/master/Sample/alert%20style.gif)
![image](https://github.com/snail-z/OverlayController-Swift/blob/master/Sample/slogan%20style.gif?raw=true)
![image](https://github.com/snail-z/OverlayController-Swift/blob/master/Sample/shared%20style.gif?raw=true)

![image](https://github.com/snail-z/OverlayController-Swift/blob/master/Sample/qzone%20style.gif)
![image](https://github.com/snail-z/OverlayController-Swift/blob/master/Sample/sidebar%20style.gif)
![image](https://github.com/snail-z/OverlayController-Swift/blob/master/Sample/sina%20style.gif)


## Requirements

*  Swift 3.0
*  iOS 8 or higher

## Update
* Add elastic animation, set by `isUsingElastic`
```swift
  open var isUsingElastic = false // Using elastic animation
```
* Add transition effects, set by `TransitionStyle -> FromCenter`
```swift
  public enum TransitionStyle {
    case CrossDissolve, Zoom, FromTop, FromBottom, FromLeft, FromRight, FromCenter
}
```
* Add the corresponding delegate method.
```swift
/**
 - Protocol -
 ! OverlayControllerDelegate
 */
@objc protocol OverlayControllerDelegate: class {
    // WillPresent delegate to be executed before the view is presented.
    @objc optional func overlayControllerWillPresent(overlayController: OverlayController)
    @objc optional func overlayControllerDidPresent (overlayController: OverlayController)
    @objc optional func overlayControllerWillDismiss(overlayController: OverlayController)
    @objc optional func overlayControllerDidDismiss (overlayController: OverlayController)
}
```
More details, please see the demo.
  
## Usage

``` swift

    var overlayController : OverlayController!
    
    overlayController = OverlayController(aView: customView, overlayStyle: .BlackTranslucent)
    overlayController.present(animated: true)
    
 ``` 
*  Properties
``` swift

    open var presentationStyle: PresentationStyle = .Centered
    open var transitionStyle: TransitionStyle = .CrossDissolve
    open var overlayAlpha: CGFloat = 0.5
    open var animateDuration: TimeInterval = 0.25
    open var isAllowOverlayTouch = true
    open var isAllowDrag   = false
    
    /**
     The view disappear in the opposite direction.
     - set default value is false!
     */
    open var isDismissedOppositeDirection = false
    
    // Using elastic animation
    open var isUsingElastic = false 
    
 ```
*  Delegate
``` swift

    // MARK: - OverlayControllerDelegate
    
    func overlayControllerWillPresent(overlayController: OverlayController) {
        print("overlayControllerWillPresent~")
    }
    
    func overlayControllerDidPresent(overlayController: OverlayController) {
        print("overlayControllerDidPresent~")
    }
    
    func overlayControllerWillDismiss(overlayController: OverlayController) {
        print("overlayControllerWillDismiss~")
    }
    
    func overlayControllerDidDismiss(overlayController: OverlayController) {
        print("overlayControllerDidDismiss~")
    }
    
 ```
 
## License

OverlayController is distributed under the MIT license.
