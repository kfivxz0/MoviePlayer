# 비디오 재생 앱 만들기 (14장)
IOS에서 재공하는 AVPlayerViewController를 사용하면 앱 내부에 저장되어 있는 비디오 파일뿐만 아니라 외부에 링크된 비디오 파일도 간단하게 재생할 수 있습니다. 비디오 재생 방법을 잘 활용하면 쉽게 다음과 같은 비디오 재생 앱도 만들 수 있습니다.

--- 
## 완성된 모습

![스크린샷 2022-05-27 오후 2 53 45](https://user-images.githubusercontent.com/106981296/173392334-06d671c3-9440-40c3-8c97-257cb352bcce.png)

---
## 주요 기능

* 앱 내부 비디오 재생  
![스크린샷 2022-05-27 오후 2 54 01](https://user-images.githubusercontent.com/106981296/173392595-7990c6ed-ad7b-44ac-b742-8fd940b2fcdd.png)  

* 외부 링크 비디오 재생  
![스크린샷 2022-05-27 오후 2 54 11](https://user-images.githubusercontent.com/106981296/173392819-e8f0e366-15c6-4ec5-bf4b-dbbb8a0ce1a6.png)

---
## 전체 소스  
![스크린샷 2022-05-27 오후 2 54 36](https://user-images.githubusercontent.com/106981296/173392966-dd8783eb-37d8-4f81-acdb-50df51f0b9f5.png)

---
## 주요 코드 해석

비디오 관련 헤더 파일을 추가합니다.
```SWIFT
import AVKit
```

'앱 내부 비디오 재생' 코드를 작성합니다.
```SWIFT
// 비디오 파일명을 사용해 비디오가 저장된 앱 내부의 파일 경로를 받아옵니다.
let filePath:String? = Bundle.main.path(forResource: "FastTyping", ofType: "mp4")

// 앱 내부의 파일명을 NSURL 형식으로 변경합니다.
let url = NSURL(fileURLWithPath: filePath!)

//앞에서 얻은 비디오 URL로 초기화된 AVPlayer의 인스턴트를 생성합니다.
let player = AVPlayer(url: url as URL)

//AVPlayerViewController의 player 속성에 AVPlayer 인스턴드를 할당합니다.
playerController.player = player
```

'외부 링크 비디오 재생' 코드를 작성합니다.
```SWIFT
// 외부 파일 MP4
let url = NSURL (string: "https:// ~~~~~ ")!

let playerController = AVPlayerViewController()

let player = AVPlayer(url: url as URL)
playerController.player = player

self.present(playerController, animated: true){
    player.play()
  }
}
```

비디오 재생 함수를 만듭니다.
```SWIFT
// 아래 함수를 추가해 두 액션 함수에서 동일한 내용을 복사해 붙여 넣습니다.
private func playVideo(url: NSURL){}
```

마지막으로 두 액션 함수에서 동일하게 입력된 부분을 다음 코드로 대체합니다.
```SWIFT
playVideo(url: url)
```
