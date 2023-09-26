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
결국 방향을 잡기로 정했다. 실시간으로 객체를 탐지해서 유사도를 비교 후, 사용자에게 정보를 띄워주는 작업이 React Native에서 어렵다는 사실을 알았다.

방향을 다른 방향으로 잡기로 정했고, 객체 사진을 찍어서 GPU서버에서 유사도 비교 후, 사용자에게 메모를 띄워주는 방향으로 설정.

기간 내에 원하는 기능을 구현할 수 있어야 할텐데 걱정이다.
```

<br>

## 2023. 09. 20

```
소셜 로그인 기능 구현 시작. React Native의 경우 BackEnd에서 Oauth구현을 할 필요가 없다.

"@react-native-seoul/kakao-login"로 구현이 가능하다.

카카오 개발자 페이지에서 프로젝트 생성하고, 카카오 비즈 신청을 통해서 사용자의 원하는 정보를 얻을 수 있다.

React Native에서는 간단하게 import와 login(), getProfile() 만으로도 사용자 로그인과 정보를 얻는 과정을 할 수 있다.
```

<br>

## 2023. 09. 21

```
소셜 로그인 기능 구현 완료. 회원가입 로직 작성 완료.

React Native는 아니지만 JavaScript와 Python간의 WebRTC 작동 성공.

실시간 객체 탐지 기능 구현의 가능성 보임.
```

<br>

## 2023. 09. 22

```
React Native 메모 기능 구현 중..
```

<br>

## 2023. 09. 23

```
메모 기능

  - 4줄이상의 길이는 문장 요약

  - 북마크 체크 여부 상태관리

  - 메모에 사진 추가할 수 있게 변경
```

**하위 컴포넌트에서 상위 컴포넌트로 props 하는 방법**

```JavaScript

// 하위 컴포넌트
const MemoItem: React.FC<MemoItemProp> = ({onMemoWritePress }) => {
  return (
    ...
  );
}

// 상위 컴포넌트
{memoItemVisible && <MemoItem onMemoWritePress={checkMemoHandler} />}

// 상위 컴포넌트 함수
const checkMemoHandler = () => {
    setMemoItemVisible((prev) => !prev);
    setMemoCreateModalVisible((prev) => !prev);
  };
```

<br>

## 2023. 09. 24

```
메모 상세 조회의 이미지를 클릭 시 이미지의 원본을 보여주는 로직 구현.

원본은 이미지 비율에 따라 조정.
```

<br>

## 2023. 09. 25

```
개발을 진행하던 중, 백엔드의 정보를 받아와서 바로 보여줘야하는 상황이 발생함.

이를 위해 코드를 작성하던 중 문제가 발생함.
```

**문제의 코드**

```JavaScript
// 메모 상세 조회 상태관리
  const [memoDetailData, setMemoDetailData] = useState<MemoDetailProps[]>([]);

  // 메모 상세 조회를 위한 AXIOS
  axios
    .get(BACKEND_URL + `/memos/${memoSeq}/23`)
    .then((response) => {
      setMemoDetailData([response.data]);
    })
    .catch((error) => {
      console.log(error);
    });
```

```
위의 코드에서 setMemoDetailData가 비동기적으로 작동하다보니 원하는 정보가 바로 반영이 안되는 문제가 발생함.
```

**해결방법**

```Java Script
// 메모 상세 조회를 위한 AXIOS
  useEffect(() => {
    const fetchData = async () => {
      try {
        const res = await axios.get(BACKEND_URL + `/memos/${memoSeq}/23`);
        setMemoDetailData([res.data]);
        setMemoPic(res.data.file);
      } catch (err) {
        console.log(err);
      }
    };
    fetchData();
  }, []);

///////////////////////////////////

{memoDetailData[0] && (
  <Text style={detailStyle.calendar}>
    {memoDetailData[0].updatedAt}
  </Text>
)}

// 해결방법은 해당 값이 있을 때, 동작하도록 만들면 해결이 된다..

// 거의 2-3시간을 사용한 것 같은데.. 다시는 까먹지말고 이런 문제가 발생했을 때, 잘 대처하자!!
```

<br>

## 2023. 09. 26

```
React Native에서 모달을 띄웠을 때, 모달 외의 부분을 터치했을 때 모달이 종료되도록 하는 로직 구현.

```

```JavaScript
// 모달
{memoListVisible && (
  <>
    <Pressable style={styles.memoClose} onPress={closeMemoList} />
    <MemoList
      onMemoWritePress={checkMemoHandler}
      onMemoDetailPress={setMemoDetailModal}
    />
  </>
)}

// 함수
const closeMemoList = () => {
  setMemoListVisible(false);
};

// 스타일
memoClose: {
    flex: 1,
    backgroundColor: "transparent",
    marginTop: -screenHeight,
  },
```

**어지러운 4중 삼항연산자**

```TypeScript
{memoDetailData[0] && (
  <View>
    <Text style={detailStyle.open}>
      {memoDetailData[0].accessType === "OPEN" ? (
        "전체공개"
      ) : memoDetailData[0].accessType === "CLOSED" ? (
        "비공개"
      ) : memoDetailData[0].taggedTeamList.length > 0 ? (
        <Pressable
          onPress={() =>
            changeShowAllTagged(
              memoDetailData[0].taggedTeamList.length - 1
            )
          }
        >
          <Text>
            {memoDetailData[0].taggedTeamList[0].nickname}
            {memoDetailData[0].taggedTeamList.length - 1 !==
              0 && (
              <Text style={detailStyle.plusText}>
                {` +${
                  memoDetailData[0].taggedTeamList.length - 1
                }`}
              </Text>
            )}
          </Text>
        </Pressable>
      ) : (
        <Pressable
          onPress={() =>
            changeShowAllTagged(
              memoDetailData[0].taggedUserList.length - 1
            )
          }
        >
          <Text style={detailStyle.open}>
            {memoDetailData[0].taggedUserList[0].nickname}
            {memoDetailData[0].taggedUserList.length - 1 !==
              0 && (
              <Text style={detailStyle.plusText}>
                {` +${
                  memoDetailData[0].taggedUserList.length - 1
                }`}
              </Text>
            )}
          </Text>
        </Pressable>
      )}
    </Text>
    {showAllTagged && (
      <Pressable
        onPress={() => changeShowAllTagged(1)}
        style={detailStyle.tagged}
      >
        {memoDetailData[0].taggedTeamList.length > 0 &&
          memoDetailData[0].taggedTeamList.map(
            (team, index) => (
              <Text
                key={`team-${index}`}
                style={{
                  color: "#FFFFFF",
                  marginLeft: calculateDynamicWidth(8),
                }}
              >
                {team.nickname}
              </Text>
            )
          )}
        {memoDetailData[0].taggedUserList.length > 0 &&
          memoDetailData[0].taggedUserList.map(
            (user, index) => (
              <Text
                key={`user-${index}`}
                style={{
                  color: "#FFFFFF",
                  marginLeft: calculateDynamicWidth(8),
                }}
              >
                {user.nickname}
              </Text>
            )
          )}
      </Pressable>
    )}
  </View>
)}

/////////////

const changeShowAllTagged = (num: number) => {
  if (num !== 0) {
    setShowAllTagged(!showAllTagged);
  }
};
```
