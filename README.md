# Git과 Github로 협업하기
## 1. 설명
이 페이지에서는 깃과 깃허브를 사용해서 협업을 하는 연습을 익혀봅니다. 이렇게 같이 협업을 하여 좋은 방향으로 프로젝트를 변경해 가는 것을 `기여`한다는 표현을 합니다. 

일반적으로 여러명이서 동시에 작업을 할 경우 하나의 브랜치(주로 Master브랜치)에서만 작업을 하면 여러가지 문제가 발생할 가능성이 높습니다. 같은 파일을 수정함은 물론 개발 중에 있는 코드를 커밋해서 프로그램이 실행이 안될 수도 있습니다.(이러한 상태를 빌드가 깨졌다고 표현을 합니다.) 

이러한 문제를 피하기 위해 일반적으로 저장소를 복제, 자신만의 브랜치를 생성하여 코드 작업을 한 후 총 변경 사항을 정리하여 메인 브랜치(일반적으로 Master)로 반영을 요청하게 됩니다. 이러한 요청을 풀 리퀘스트(Pull Request), 줄여서 PR이라고 합니다. 
이번 실습에서는 다음 과정을 경험해보게 될 것입니다.

 1. 저장소 포크(Fork)하기
 1. 지역 저장소로 복제하기
 1. 브랜치 생성하기
 1. 변경사항을 작성하고 스테이징, 커밋하기
 1. 변경사항을 자신의 깃허브 원격저장소로 푸시하기
 1. 메인 브랜치로 반영을 위해 변경 사항을 제출하기(Pull Request)
 1. 변경사항이 적용된 것을 확인 또는 수정해서 다시 PR날리기 

### 1.1 저장소 포크(Fork)하기
이 저장소의 우측 위에 있는 포크(Fork) 버튼을 클릭하여 저장소를 자신 계정의 저장소로 복제본을 생성합니다. 즉 원격저장소의 복사본 저장소가 자신의 계정에 하나 생성이 됩니다.

### 1.2 지역 저장소로 복제하기
자신의 계정에 원격저장소 복제본이 생성되었습니다. 이제 작업을 하기 위하여 내 컴퓨터의 지역저장소로 방금 복사해온 원격 저장소를 복제합니다. `c:\android\workspace` 같은 작업공간으로 이동하여 `git clone git저장소주소` 명령을 사용하여 저장소를 복제합니다. `git저장소주소`는 방금 복사한 원격저장소의 git저장소 주소를 사용합니다. Clone or download 버튼을 눌러서 나오는 주소를 복사해서 사용하세요.

> git clone  `git저장소주소`

예시:
> git clone  https://github.com/자신의Github아이디/student20182.git

위 명령이 올바르게 실행되었다면 여려분의 작업공간 안에는 student20182 지역저장소가 생성, 이 프로젝트의 파일들이 생겼을 것입니다. 이렇게 원격저장소에서 지역저장소로 저장소를 복제하는 것을 클론(clone)한다고 표현합니다.

### 1.3 브랜치 생성하기
이제 가져온 프로젝트 디렉토리로 이동합니다.

> cd student20182

이제 브랜치를 생성합니다. 브랜치를 변경(checkout) 하는 명령을 실행할 때 해당 브랜치가 존재하지 않으면 새 브랜치를 자동 생성하므로 브랜치를 변경하는 명령으로 브랜치를 생성, 변경을 같이 하도록 하겠습니다. 브랜치 이름은 add-자신의 학번-영문이름으로 지정하도록 합니다. 외국인들을 위해 브랜치명은 영어, 숫자, -(빼기기호)를 사용하도록 합니다. 

> git checkout -b <add-studentnumber-yorname>

예시: 2학년 7반 99번 Gihun Ham인 경우
> git checkout -b add-2799-gihunham


### 1.4 자신의 반번호에 해당하는 곳을 찾아내서 정보 수정하고 스테이징, 커밋하기
이제 README.md 파일을 [VisualStudio Code](https://code.visualstudio.com/])나 [EditPlus](https://www.editplus.com/kr/) 같은 자신이 좋아하는 IDE로 열어서 자신에 해당하는 행의 정보를 수정합니다. 더 좋아하는 IDE가 있다면 그것을 사용해도 됩니다. 여기서는 [마크다운(Markdown)](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)으로 작성된 알아보기 쉬운 md텍스트 파일을 수정합니다만 원래는 소스코드를 개발 IDE로 수정하는 작업이 대부분일 것입니다. 

| 번호  | 이름  | Github ID | MyCatCode 저장소 | 
| :---: |:-------------:| :-----:| :-----:|
| 99 |  | @ | [mycatcode저장소]() |  

위와 같이 되어있는 코드를 다음가 같이 자신의 정보로 수정해줍니다.

| 번호  | 이름  | Github ID | MyCatCode 저장소 | 
| :---: |:-------------:| :-----:| :-----:|
| 99  | 함기훈 | @progh2 | [mycatcode저장소](https://github.com/progh2/mycatcode) |  

수정을 다 했으면 변경 사항을 다음 명령어로 확인해봅니다.

> git status

수정된 파일이 보이면 변경된 파일을 스테이징 해줍니다.

> git add README.md

다시 `git status` 명령으로 잘 스테이징 되었는지 확인합니다. 

> git status

스테이징이 잘 되었다면 커밋합니다.

> git commit -m "`학번` `이름` 추가"

예시:
> git commit -m "2799 함기훈 추가"

커밋 메시지는 여러분의 학번과 이름으로 합니다.

### 1.5 변경사항을 깃허브에 푸시하기
`git push` 명령으로 변경내역을 푸시합니다. 이미 원격저장소가 있는 프로젝트를 클론해왔기 때문에 원격저장소 주소는 이미 origin으로 등록되어 있습니다. `<브랜치이름>`은 앞에서 checkout 명령으로 생성한 이름을 적어줍니다.

> git push origin `브랜치이름`

예시:
> git push origin add-2799-gihunham


### 1.6 검토를 하기 위해 변경사항을 제출하기
푸시가 완료되었다면 원격 저장소의 `Pull requests`탭에서 초록색의 `Compare & pull request` 버튼을 볼 수 있습니다. 이 버튼을 클릭해서 변경하고자 하는 내용 설명을 잘 적고 `Create pull request` 버튼을 클릭하면 메인 브랜치에 반영할 변경 사항 요청이 메인 브랜치 관리자에게 가게 됩니다. 이 단계를 `Pull Request`, `풀 리퀘스트`, `PR`이라고 합니다. 

### 1.7 변경사항이 적용된 것을 확인하기
풀 메인 브랜치 관리자가 해당 내용을 보고 받아들일지, 수정할 사항이 있어서 수정을 요청할지가 결정됩니다. 잘 준비해서 (또 약간의 운이 함께해서) 한번에 요청이 받아들여지면 메인 브랜치에 여러분이 변경한 내용들이 반영되는 것을 볼 수 있을 것입니다. 

하지만 대부분의 오픈소스의 경우는 코드 스타일부터 시작해서 코드 내용 등을 코드리뷰를 통해서 점검을 한 후 받아들이기 때문에 대개 처음 보낼 때는 몇 개의 수정사항을 요청받게 될 것입니다. 그 경우 해당 내용을 수정한 후 다시 `PR`을 날리면 받아들여지게 될 것입니다. (가끔 프로젝트의 방향성과 맞지 않다고 받아들이지 않는 경우도 있습니다. 너무 마음상하지 마세요. 사람 사는 세상이 다 그러니까요.)

자, 이제 위 내용을 바탕으로 아래 표를 수정해보도록 합시다.

## 2. 작업해보기
아래 자신의 반, 번호에 해당하는 곳에 이름과 깃허브 아이디(@으로 시작), MyCatCode 프로젝터 홈페이지 주소를 넣으세요. 
(branch, Pull Request를 사용하는 법을 배웁니다.)

| 번호  | 이름  | Github ID | MyCatCode 저장소 | 
| :---: |:-------------:| :-----:| :-----:|
| 01  | 함기훈 | @progh2 | [mycatcode저장소](https://github.com/progh2/mycatcode) |  
| 99  | 함기훈 | @progh2 | [mycatcode저장소](https://github.com/progh2/mycatcode2) |  
| 99  | 함기훈 | @progh2 | [mycatcode저장소](https://github.com/progh2/mycatcode2) |  

### 2.1 2학년 1반
| 번호  | 이름  | Github ID | MyCatCode 저장소 | 
| :---: |:-------------:| :-----:| :-----:|
| 01  |  | @ | [mycatcode저장소]() |  
| 02  | 김나연 | @kimnayeon574 | [mycatcode저장소](https://github.com/kimnayeon574/mycatcode) |  
| 03  |  | @ | [mycatcode저장소]() |  
| 04  |  | @ | [mycatcode저장소]() |  
| 05  |  | @ | [mycatcode저장소]() |  
| 06  |  | @ | [mycatcode저장소]() |  
| 07  | 박혜정 | @Hyjpark | [mycatcode저장소](https://github.com/Hyjpark/mycatcode) |  
| 08  |  | @ | [mycatcode저장소]() |  
| 09  |  | @ | [mycatcode저장소]() |  
| 10  | 유란주 | @ranjuyou | [https://github.com/ranjuyou/mycatcode]() |  
| 11  |  | @ | [mycatcode저장소]() |  
| 12  |  | @ | [mycatcode저장소]() |  
| 13  |  | @ | [mycatcode저장소]() |  
| 14  |  | @ | [mycatcode저장소]() |  
| 15  |  | @ | [mycatcode저장소]() |  
| 16  |  | @ | [mycatcode저장소]() |  
| 17  |  | @ | [mycatcode저장소]() |  
| 18  |  | @ | [mycatcode저장소]() |  
| 19  |  | @ | [mycatcode저장소]() |  
| 20  |  | @ | [mycatcode저장소]() |  

### 2.2 2학년 2반
| 번호  | 이름  | Github ID | MyCatCode 저장소 | 
| :---: |:-------------:| :-----:| :-----:|
| 01  |  | @ | [mycatcode저장소]() |  
| 02  |  | @ | [mycatcode저장소]() |  
| 03  |  | @ | [mycatcode저장소]() |  
| 04  | 김예빈 | @girincute | [mycatcode저장소](https://github.com/girincute/android-mycatcode) |  
| 05  |  | @ | [mycatcode저장소]() |  
| 06  |  | @ | [mycatcode저장소]() |  
| 07  |  | @ | [mycatcode저장소]() |  
| 08  |방채연| @BangChaeYeon | [mycatcode저장소](https://github.com/BangChaeYeon/mycatcode) |  
| 09  |  | @ | [mycatcode저장소]() |  
| 10  |  | @ | [mycatcode저장소]() |  
| 11  | 신영선 | @YoungSunShin  | [mycatcode저장소](https://github.com/YoungSunShin/mycatcode) |  
| 12  | 이유정 | @You-J | [mycatcode저장소](https://github.com/You-J/mycatcode) |  
| 13  |  | @ | [mycatcode저장소]() |  
| 14  |  | @ | [mycatcode저장소]() |  
| 15  |  | @ | [mycatcode저장소]() |  
| 16  |  | @ | [mycatcode저장소]() |  
| 17  |  | @ | [mycatcode저장소]() |  
| 18  |  | @ | [mycatcode저장소]() |  
| 19  | 허주희 | @juhee6379 | [mycatcode저장소](https://github.com/heojuhee/mycatcode) |  
| 20  |  | @ | [mycatcode저장소]() |  

## 3. 레퍼런스
* [Github first-contributions 한글리드미](https://github.com/firstcontributions/first-contributions/blob/master/translations/README.ko.md) - 이 저장소로도 한번 작업을 해봅시다!