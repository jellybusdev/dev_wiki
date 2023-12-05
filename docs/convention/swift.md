# JellyBus 코드 컨벤션

# **대원칙**

- JellyBus 코딩 컨벤션의 기준은 각 언어의 공식 홈페이지의 컨벤션 규칙을 따름.

       (ex. Swift → Swift.org, Kotlin → kotlinlang, Objective-C → Apple Documents)

- 코드 컨벤션은 작업자 사이의 문법의 다름을 최소화하여 코드 퀄리티를 유지하고, 작업자가 핵심알고리즘 파악에 집중해서 작업함으로써 효율적으로 작업할 수 있는것을 목적으로함.

# **Swift**

## ****Code Formatting****

### ****1. 임포트****

- 모듈 임포트는 알파벳 순으로 정렬합니다. 내장 프레임워크를 먼저 임포트하고, 빈 줄로 구분해 3rd-party프레임워크를 임포트 합니다.

```swift
import UIKit

import SwiftyColor
import SwiftyImage
import URLNavigator
```

### 2. **띄어쓰기**

- 콜론(`:`)을 사용할때는 콜론의 오른쪽에만 공백을 둡니다.

**[상수]**

✅ Preferred 

```swift
let names: [String: String]?
```

⛔️Not Preferred  

```swift
let names:[String: String]?
let names: [String:String]?
```

**[클래스]**

✅ Preferred 

```swift
class MyClass: SuperClass {
  // ...
}
```

⛔️Not Preferred  

```swift
class MyClass : SuperClass {
  // ...
}
```

**[함수 리턴 타입]**

✅ Preferred 

```swift
func doSomething() -> String {
  // ...
}
```

⛔️Not Preferred  

```swift
func doSomething()->String {
  // ...
}
```

**[클로저 리턴 타입]**

✅ Preferred 

```swift
func doSomething(completion: () -> Void) {
  // ...
}
```

⛔️Not Preferred  

```swift
func doSomething(completion: ()->Void) {
  // ...
}
```

**[ If ]**

- if 문의 기본 형태는 Swift 공식문서의 형태를 따른다.

✅ Preferred 

```swift
let contentView: UIView 

func showContentView(animated: Bool) {
		if animated {
				// Do animate view.
		}
		else {
				// Do Something.
		}
} 
```

⛔️Not Preferred  

```swift
let contentView: UIView 

func showContentView(animated: Bool) {
		if (animated) {
				// Do animate view.
		}
		else {
				// Do Something.
		}
} 
```

⛔️Not Preferred  

```swift
let contentView: UIView 

func showContentView(animated: Bool) {
		if (animated){
				// Do animate view.
		}
		else {
				// Do Something.
		}
} 
```

**[if let, Guard let]**

✅ Preferred 

```swift
if let value = aValueReturnedByAVeryLongOptionalThing(),
   let value2 = aDifferentValueReturnedByAVeryLongOptionalThing() {
  doSomething()
}

guard let value = aValueReturnedByAVeryLongOptionalThing(),
      let value2 = aDifferentValueReturnedByAVeryLongOptionalThing() else {
  doSomething()
}
```

**[삼항연산자]**

✅ Preferred 

```swift
func application(_ application: UIApplication, supportedInterfaceOrientationsFor window: UIWindow?) -> UIInterfaceOrientationMask {
	return shouldRotate ? .allButUpsideDown : .portrait
}
```

⛔️Not Preferred  

```swift
func application(_ application: UIApplication, supportedInterfaceOrientationsFor window: UIWindow?) -> UIInterfaceOrientationMask {
	return shouldRotate ? .allButUpsideDown: .portrait
}
```

**[기타]**

- 일반적으로 콤마(`,`) 뒤에는 공백을 추가합니다.

✅ Preferred 

```swift
let numbers = [1, 2, 3, 4, 5]                                                   
```

⛔️Not Preferred  

```swift
let myArray = [1,2,3,4,5]
```

- 연산자 앞뒤로 공백을 추가합니다.

✅ Preferred 

```swift
let myValue = 20 + (30 / 2) * 3
```

⛔️Not Preferred  

```swift
let myValue = 20+(30/2)*3
```

### 3. 개행

**[함수]**

함수가 너무 길 경우, 아래와 같이 함수의 첫 인자의 시작점에 맞추어 개행을 함 

✅ Preferred 

```swift
class JBEditTransitionCommand {
		class func addTransitionPreset(_ preset: JBTransitionPreset, 
                                   targetClip: inout JBMultiTrackClip,
                                   trackSize: CGSize,
                                   options: [AnyHashable: Any]) {
				// DO SOMETHING..
		}

		class func defaultDuration(preset: JBTransitionPreset, 
															 track: JBMultiTrack, 
															 clipIdentifier: UInt) -> Double {
				// DO SOMETHING..
		}
}
```

### 4. 네이밍

- 묘사를 잘하고 일관된 네이밍은 코드를 읽고 이해하기 쉽게 해줍니다. 네이밍은 Apple의 [API Design Guidelines](https://swift.org/documentation/api-design-guidelines/)을 따릅니다.
- 클래스(타입, 프로토콜 이름 포함) 이름에는 UpperCamelCase(첫 문자를 대문자로 시작하는 camel표기법), 함수 이름에는 camelCase를 사용합니다.

**[클래스 프로퍼티]**

✅ Preferred 

```swift
public class UIColor {
  public class var red: UIColor {                // GOOD.
    // ...
  }
}

public class URLSession {
  public class var shared: URLSession {          // GOOD.
    // ...
  }
}
```

⛔️Not Preferred  

```swift
public class UIColor {
  public class var redColor: UIColor {           // AVOID.
    // ...
  }
}

public class URLSession {
  public class var sharedSession: URLSession {   // AVOID.
    // ...
  }
}
```

[**Global Constants]**

✅ Preferred 

```swift
let staticSecondsPerMinute = 60
let defaultSecondsPerMinute = 10
```

⛔️Not Preferred  

```swift
let SecondsPerMinute = 60
let kSecondsPerMinute = 60
let gSecondsPerMinute = 60
let SECONDS_PER_MINUTE = 60
```

**[스위프트의 getter]**

- 스위프트에서 어떤 인스턴스를 리턴하는 함수나 메서드에 `get`을 쓰지 않는다. `get` 없이 바로 타입 이름(명사)으로 시작하면 된다.

✅ Preferred 

```swift
func date(from string: String) -> Date?
func anchor(for node: SCNNode) -> ARAnchor?                          
func distance(from location: CLLocation) -> CLLocationDistance        
func track(withTrackID trackID: CMPersistentTrackID) -> AVAssetTrack?
```

**[약어]**

- 약어로 시작하는 경우 소문자로 표기하고, 그 외 경우에는 항상 대문자로 표기합니다.

✅ Preferred 

```swift
class URLValidator {
  func isValidURL(_ url: URL) -> Bool {
    // ...
  }

  func isProfileURL(_ url: URL, for userID: String) -> Bool {
    // ...
  }
}

let urlValidator = URLValidator()
let isProfile = urlValidator.isProfileUrl(urlToTest, userID: idOfUser)
```

⛔️Not Preferred  

```swift
class UrlValidator {
  func isValidUrl(_ URL: URL) -> Bool {
    // ...
  }

  func isProfileUrl(_ URL: URL, for userId: String) -> Bool {
    // ...
  }
}

let URLValidator = UrlValidator()
let isProfile = URLValidator.isProfileUrl(URLToTest, userId: IDOfUser)
```

**[Bool변수]**

문법적으로만 보면 `isSelected`과 `selected` 둘 다 맞다고 할 수 있으나 스위프트에서는 `is`를 써주는 것이 컨벤션이다보니 맞춰주는것을 원칙으로함. 

✅ Preferred 

```swift
if isEnabled { ... }
if !isEnabled { ... }

tableView.isVisible = !items.isEmpty  //"tableView가 보일 때는 items가 비어있지 않을 때"
tableView.isHidden = items.isEmpty    //"tableView가 숨어있을 때는 items가 비어있을 때"
```

### 5. ****클래스와 구조체****

- 구조체를 생성할 때는 Swift 구조체 생성자를 사용합니다.

✅ Preferred 

```swift
let frame = CGRect(x: 0.0, y: 0.0, width: 100.0, height: 100.0)
```

⛔️Not Preferred  

```swift
let frame = CGRectMake(0, 0, 100, 100)
```

### 6. ****타입****

- `Array<T>`와, `Dictionary<T: U>` 보다는 `[T]`, `[T: U]`를 사용합니다.

✅ Preferred 

```swift
var messages: [String]?
var names: [Int: String]?
```

⛔️Not Preferred  

```swift
var messages: Array<String>?
var names: Dictionary<Int, String>?
```

### 7. Code Structure

✅ Preferred

```swift
/**
 * 퀵 에디터에 연결되어있는 Commander 기본 클래스
 */
class JBQuickEditCommander: JBQuickEditCoordinate,
                            JBQuickEditTopViewDelegate,
                            JBQuickEditControlBarDelegate,
                            JBCommandTaskDelegate,
                            JBMTLMultiTrackPlayViewFullScreenDelegate {

		// static 변수 
		public static var defaultClassName: String

		// 0. 클래스 변수  
		public class var className: String

		// 1.5. Class Method (클래스 메서드에 UI 관련 밸류들이 많을경우에, Extension으로 분류) 
		class func defaultClass() -> Class {
				return JBQuickEditCommander.self
		}

		// 1. 일반 변수 
		weak var controlView: UIView?
    weak var controlBar: JBQuickEditControlBar?
    weak var bottomView: UIView?
    
    var originTrack: JBMultiTrack? = nil
    var editingTrack: JBMultiTrack? = nil {
        didSet {
						// WARNING: 5줄 이내로 작성하고, 더 길어질 경우에 메소드로 빼야함.
            if let nowTrack = editingTrack {
                nowTrack.refreshAnimations()
            }
        }
    }
    
    var task: JBCommandTask?
    var commandMode: JBEditCommandMode = JBEditCommandTrack
		
		// 2. Value Method 중에 클래스에 전체적으로 영향이 있는 메소드들 상단에 정리 
		open func commandClass() -> JBEditCommand.Type {
        return JBEditCommand.self
    }
    
    open func commandOptions() -> [AnyHashable: Any]? {
        return nil
    }
    
    open func editCommand() -> JBEditCommand? {
        return self.editCommand(options: commandOptions())
    }
    
    open func editCommand(options: [AnyHashable: Any]?) -> JBEditCommand? {
        if useEditCommand() {
            let commanderClass = self.commandClass()
            if let command = commanderClass.command(with: commandMode) as? JBEditCommand {
                command.setOptions(options)
                return command
            }
        }
        
        return nil
    }
    
    open func defaultCommandMode() -> JBEditCommandMode {
        return JBEditCommandTrack
    }
    
    open func useEditCommand() -> Bool {
        return true
    }

		// 3. Initialize 
		public required init(viewController: UIViewController, options: [String: Any]) {
        self.viewController = viewController
        
        super.init()
        
				// 메서드들 사용할땐 필요한경우가 아니면 self. 제거 
        initValues(options: options)
        
				initDetails()

        performInitializeAppear()
    }

		func initDetails() {
        initViews()
        
        initLayouts()
        
        initialFinalized()
		}

		func initViews() {
				
		}

		func initLayout() {
	
		}

		// 4. Deinit
		deinit {
        delegate = nil
    }

		// 5. Methods 

		// Something.. 

		// 6. Value - UI 관련된 Value들은 Extension으로 무조건 분리할것 
		open func inAppBannerHeight() -> CGFloat {
        return 62.0
    }
    
    open func defaultMargin() -> CGFloat {
        return 15.0
    }
}
```

### 8. 주석

코드 분류할때 블럭별로 // MARK: 주석으로 분류해서 코드의 전체구성을 파악하기 쉽도록 한다.

```swift
class JBQuickEditCommander {
		// MARK: - COMMAND
	  open func commandToTrack(_ track: JBMultiTrack, clip: JBMultiTrackClip, options: [AnyHashable: Any]) {
        if commandMode == JBEditCommandTrack {
            commandToTrack(track, options: options)
        }
        else {
            commandToClip(clip, options: options)
        }
    }
    
    open func commandToTrack(_ track: JBMultiTrack, options: [AnyHashable: Any]) {
        commandClass().command(to: track, options: options)
    }
    
    open func commandToClip(_ clip: JBMultiTrackClip, options: [AnyHashable: Any]) {
        commandClass().command(to: clip, options: options)
    }

		// MARK: - SHOW/HIDE COMMANDER
    open func showCommander(animated: Bool, completion: (() -> Void)?) {
        if animated {
            self.willAppear()
            
            UIView.animate(withDuration: appearAnimationDuration(), delay: 0.005, animations: {
                self.doAppear()
            }) { finished in
                self.didAppear()
            }
            
            UIView.animate(withDuration: appearAfterAnimationDuration(), delay: 0.21, animations: {
                self.doAfterAppear()
            }) { finished in
                self.didAfterAppear()
                completion?()
            }
        }
        else {
            self.willAppear()
            self.doAppear()
            self.didAppear()
            self.doAfterAppear()
            self.didAfterAppear()
        }
    }

		// MARK: - VALUES
    open func inAppBannerType() -> Int {
        return 0
    }
    
    open func inAppBannerHeight() -> CGFloat {
        return 62.0
    }
    
    open func defaultMargin() -> CGFloat {
        return 15.0
    }
}
```

코드에서 설명이 필요한경우 주석은 아래와 같이 코드 블럭별로 정리한다.

```swift
class JBTimelineRuler {
    /**
     * 메인타임라인, 서브타임라인이 포함된 타입 초기화 함수
     *
     * - note:
     * 1. 트림,컷,스플릿을 제외한 나머지 타임라인은 Scale 이 유지되어야 함
     * 2. 트림,컷,스플릿 타암라인은 Sclae 이 각각 초기화되어야 함
     */
    func initScaleMainRulerSubType() {
        let totalClipDurationSecond: Double = totalClipDurationSecond()
        let totalClipWidth: Double = Double(totalClipWidth())
        
        // 1단계 기준 미만의 영상은 아래 기본 길이로 적용
        let firstStandardThumbViewCount: Int = 20
        let firstStandardWidth = Double(self.defaultThumbViewLength) * Double(firstStandardThumbViewCount)
        
        if firstStandardWidth > totalClipWidth {
            maxZoomOutScale = 1.0
            scale = 1.0
        }
        else {
            // 기본 기준 미만의 영상의 최소 스케일
            let standardMinimumWidth = defaultMinimumItemViewsWidth
            let defaultMinimumWidthSecond = secondFromPoint(point: standardMinimumWidth)
            self.maxZoomOutScale = defaultMinimumWidthSecond / totalClipDurationSecond
            
            // 기본 기준 시간 (초단위)
            // 기본 기준 영상 시간
            let oneMinuteSecond: Double = 60.0 // 1분 (60초 기준)
            let firstLimitSecond: Double = oneMinuteSecond * 2.0 //(2분)
            let secondLimitSecond: Double = oneMinuteSecond * 5.0 //(5분)
            
            let firstStandardSecond = secondFromPoint(point: firstStandardWidth)
            let secondStandardSecond = secondFromPoint(point: totalClipDurationSecond)
            let thridStandardSecond = secondFromPoint(point: totalClipDurationSecond)
            
            // 스케일 계산
            if(firstLimitSecond > totalClipDurationSecond) {
                // 1단계 스케일 적용 (2분 미만)
                // firstLimitSecond 미만의 영상은 firstStandardWidth 길이로 고정 적용
                scale = firstStandardSecond / totalClipDurationSecond
            }
            else if(secondLimitSecond > totalClipDurationSecond) {
                // 2단계 스케일 적용 (2분 이상 ~ 5분 미만)
                // 1분당 썸네일 6개
                scale = (secondStandardSecond / totalClipDurationSecond) * 5.0
            }
            else {
                // 3단계 스케일 적용 (5분 이상)
                // 1분당 썸네일 1개
                scale = thridStandardSecond / totalClipDurationSecond
            }
        }
    }
}
```

---

### * 참조문서

**1. Swift.org 공홈 예제**

[https://docs.swift.org/swift-book/documentation/the-swift-programming-language/statements/](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/statements/)

**2. 구글 Swift Coding Convention**

[https://google.github.io/swift/#guards-for-early-exits](https://google.github.io/swift/#guards-for-early-exits)

3. 링크드인 Swift Coding Convention (MS)

[https://github.com/linkedin/swift-style-guide](https://github.com/linkedin/swift-style-guide)

4. 일본회사  eure Swift Coding Convention (미국회사만 있는것같아서 일본회사도 찾아봄)

[https://github.com/eure/swift-style-guide](https://github.com/eure/swift-style-guide)

5. Airbnb Swift Coding Convention

[https://github.com/airbnb/swift](https://github.com/airbnb/swift)

**6. 개인 깃헙에 올라와있는 컨벤션 (형식이 읽기 편해서 넣어둠)**

[https://jusung.github.io/Swift-Code-Convention/](https://jusung.github.io/Swift-Code-Convention/)

7. 네이버 Coding Style을 참고 할 수 있는 부분

[https://github.com/naver/aries-framework-swift/blob/main/README.md](https://github.com/naver/aries-framework-swift/blob/main/README.md)

7-1. 네이버 JavaScript Style Guide (Airbnb 자바스크립트 스타일 가이드 기반) 참고용

[https://github.com/naver/eslint-config-naver/blob/master/STYLE_GUIDE.md](https://github.com/naver/eslint-config-naver/blob/master/STYLE_GUIDE.md)

[https://angelplayer.tistory.com/111](https://angelplayer.tistory.com/111)

**8. Swift 네이밍 참고**

[https://soojin.ro/blog/english-for-developers-swift](https://soojin.ro/blog/english-for-developers-swift)