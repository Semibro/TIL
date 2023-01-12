# Markdown
![markdown](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQiQMEbm2XbuvKKkZkC8NAWDBWC07zIsFIQpfgDQfHcHr8ill9YMovcn8etShjtwBiuRDk&usqp=CAU)

1. 텍스트 기반의 가벼운 *마크업언어
2. 문서의 구조와 내용을 같이 쉽고 빠르게 적고자 탄생
3. 명령어
   
   \# 헤딩(Heading) : 문서의 제목이나 소제목으로 사용

    \1. 2. 3. / * / - 리스트(List) : 순서가 있는 리스트와 순서가 없는 리스트

    \```code block``` / \`inline code block` 코드 블럭(code block) : 일반 텍스트와 다르게 코드를 이쁘게 출력

    \[string](url) 링크(Link) : string은 보여지는 부분, url은 연결할 곳을 나타냄

    \!\[string](img_url) 이미지(Image) : 링크와 비슷하지만 이미지를 삽입

    \**Bold** \*Italic* \~~strikeout~~ 굵게, 기울임, 삭선 : 굵게, 기울임, 삭선 기능

    \--- 수평선(Horizontal Line) : 가로로 긴 수평선을 작성, 대게 단락을 구분할 때 사용

    \> 참고내용 : 참고한 내용작성할 때 사용

    *\* 마크업(Markup)? 태그(tag)를 이용하여 문서의 구조를 나타내는 것*

---

# Git/Github
![github](https://miro.medium.com/max/1400/0*ZLfPdBuEy3SgJscw.jpg)

1. Repository : 특정 디렉토리를 버전 관리하는 저장소
   - git init 명령어로 로컬 저장소를 생성
   - .git 디렉토리에 버전 관리에 필요한 모든 것이 들어있음
2. 특정 버전으로 남긴다 = “커밋(Commit)한다”
3. Git 흐름
   - Working Directory(작업영역) → Add → Staging Area(변경사항) → Commit → Repository(최종 저장소)
   - 중요한 명령어
   ```bash
    git add # working -> staging
    git commit # staging -> repository
    git status # 현재 상태 확인
    git commit -m "message" # commit 및 변경사항 message 부분에 작성
    # Ex) git commit -m "Add README.md"
    git push origin main # git에 push하는데 origin은 내 github주소 별명이고 main은 사용자 이름
    # main이 master로 적혀있을 수 있음
    ```
4. Github 저장소 == Remote Repository
5. 명령어 순서 정리
   - Ex) git add README.md → git commit -m “Edit README.md” → git push origin main
6. Clone
   - `git clone 주소`
7. Download
   - Clone과 Download의 차이점?
        - Clone은 변경사항까지 가져오지만, Download는 최신 파일만 가져옴