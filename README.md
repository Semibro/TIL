# TIL (_Today I Learn_)

<br>

## 2023. 09. 11

```
현재 React Native 기반의 AR 애플리케이션을 개발 중이다.

하지만, 개발 과정에서 AR Core의 마지막 업데이트가 2년 전임을 알게 됐다.

그래서 다른 방법을 모색하던 중..! react-native-vision-camera에 대해서 알게 되었고, 해당 라이브러리를 사용해 AR과 비스무리한(?) 기능을 구현하고자 한다.

근데 이것조차 쉽지 않은게 react-native와 호환성 문제가 많이 발생한다.

(에러 내용은 2023_09_11.md에 첨부)

프로젝트를 위해 빠른 시일 내 해결해야 하는데, 추후 해결하면 해결 방법을 적어 볼 예정.
```

<br>

## 2023. 09. 12

```
React Native 기반으로 AR은 구현이 어렵다고 판단했다. 그래서 다른 방법을 모색하던 중 Kotlin으로 Android Studio에서 개발을 진행하자는 의견이 나와서 약간 진행해봤다.

정말 운이 좋게도 Kotlin/Java 기반의 AR은 일단 구현했다.

(해당 코드는 2023_09_12 폴더 안에 첨부)

추가적으로 AR위에 인공지능이 가능한 파일을 찾아서 해당 파일을 적용해보려고 했다.

하지만 에러가 발생했다. 해결하려고 노력.. 했지만 실패했다. 내일 추가적으로 진행해 볼 예정이다.

(에러 코드와 에러 내용은 2023_09_12 폴더 안에 첨부)
```

<br>

## 2023. 09. 13

```
React Native에서 소셜로그인을 구현할 때는 OAUTH가 아닌 라이브러리로 구현할 수 있다는 사실을 알았다.

웹과는 다른 점인데, kakao-login 라이브러리를 통해서 OAUTH없이 소셜 로그인 구현이 가능하다.

완성하면 코드 첨부 예정
```

<br>

## 2023. 09. 14

```
React Native에서 Pytorch 기반의 딥러닝 모델을 돌리기 위해 Pytorch Core라는 라이브러리에 대해서 공부 중.

PlayTorch 사이트의 코드를 보면서 진행하고 있는데, 모바일에서 카메라는 나오는데 모델을 불러오는 과정에서 에러가 발생한다.

해결방법은 찾는 중..
```

<br>

## 2023. 09. 15

```
PlayTorch 사이트 코드를 Pytorch Core를 이용해 구동하는데 성공!

이제는 사전에 구현해둔 YOLOv8x-seg 모델을 적용해 볼 예정.

그래도 하루마다 성과가 나와서 다행이다.
```

<br>

## 2023. 09. 16

```
어제 탑재하지 못한 YOLOv8x-seg 모델을 적용해 볼 예정.

분명 파일 경로를 맞췄음에도 불구하고 모델을 인식하지 못한다. React Native의 Android build에서 뭔가 문제가 있는 것 같은데..

해결 방법을 좀 더 찾아봐야겠다.

깃허브에서 해결방법을 찾던 중 react-native-realtime-object-detection이라는 라이브러리를 찾았다.

적용을 시도해봤는데.. 아무래도 오류가 많이 발생한다. 다른 해결 방법이 필요해 보인다.
```

<br>

## 2023. 09. 17

```
자소서 작성으로 패스
```

<br>

## 2023. 09. 18

```
기존에 사용하던 Pytorch Core를 분해해보기로 결정함. YOLOv8x-seg.ptl 파일을 임베딩해서 어떤 값을 출력하는지 확인.

Python에서는 masks 값을 출력했는데, JavaScript에서는 masks값이 나오지 않음. 다른 출력값으로 인해 진행이 어려운 상황.

출력값을 바꿀 수 있는 방법을 찾아볼 예정.
```

<br>

## 2023. 09. 19

```

```
