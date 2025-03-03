
👏 Git 배우기
===
- 이모티콘 = window키 + '.'

GitHub
---
### Github 가입
[github](https://github.com/)에서 회원 가입
- 새로운 Repository(원격 저장소) 만들기
    - Owener : 사용자이름
    - Repository name : 중복되지 않는 저장소 이름
    - Description : 저장소를 설명하는 요약 한 줄
    - Public / Private : 공개 / 비공개 설정
    - Add a README : 리드미 파일을 자동으로 추가 (체크 비권장)
    - Add .gitignore : 깃 저장소에 올리면 안 되는 목록이 담긴 파일(해당 파일은 무시)추가하기 (프로그래밍 언어별 기본값)
    -Choose a license : 오픈소스에 대한 지적 재산권을 부여하기 위한 파일 추가(이후 추가 가능)
    - 3가지 파일을 선택하지 않으면, Quick Setup(CLI 명령어)를 볼 수 있다.


Git
---

1. 깃 저장소 **만들기** 명령어 :
git init

2. 깃 추적되지 않은 파일 모두 현재 폴더 기준으로 **스테이징** :
git add .

3. **커밋**하기 :
git commit -m " 커밋 메시지"

4. **원격저장소 추가**하기 :
git remote add origin [깃헙저장소주소]
git remote add[원격저장소 이름][원격저장소 주소]

5. 메인 **브랜치**로 변경하기 :
(2020년도 부터 브랜치 master -> main으로 변경됨)

    git branch - M main

6. 원격 저장소에 업로드하기(push)

    git push -u origin main
    git push [원격저장소 이름][원격저장소 브랜치]

- 기본 원격저장소의 이름은 origin 기본 브랜치의 이름은 main이다.

### 용어 정리
- Git(깃) : VCS (Version Control System)버전 관리 시스템
- GitHub : Git으로 관리하는 프로젝트를 원격으로 공유하는 사이트
- GUI : Graphic User Interface, 마우스로 화면을 클릭해서 사용하는 방식
- CLI : Command Line Interface, 명령어를 하나씩 입력해서 사용하는 방식
- commit : 버전 관리를 통해 생성된 파일, 또는 행위
- log : 지금까지 만든 커밋을 모두 확인
- 로컬 저장소 : 내 컴퓨터 안의 Git 프로젝트
- 원격 저장소 : GitHub에 업로드 된 Git 프로젝트
- push : 로컬 저장소 -> 원격 저장소로 올리는 것
- pull : 원격 저장소 -> 로컬 저장소로 내려받는 것

### 토큰 만들기
- 우측 상단 프로필 아이콘 -> 제일 하단 Settings -> Developer Settings > 왼쪽 메뉴 최하단 스크롤> personal access token > Genereate new token(classic)
- 기한, 권한 선택
- 생성된 토큰은 더이상 보여지지 않기 때문으로 적용

### 소스트리에서 토큰 적용하기
- 최상단 메뉴 [도구] => [옵션] => [인증]
- 계정선택 => 편집 => 인증 : personal Access Token 선택 후 복사한 토큰 붙여넣기

### Git 저장박식 알아보기
- Git의 저장방식 SNAPSHOT
    - 변경된 파일을 통쨰로 저장
- 차이점만 저장하는 방식 : delta
- 순서
    1. 변경된 파일을 저장한다.(save)
    2. 스테이지로 올라간다. (git add)
    3. 스테이지의 스냅샷을 찍는다.(git commit)
    4.원격 저장소 업데이트 (git push)

- 깃으로 관리하는 파일의 4가지 상태
    - 추적이 안된 상태 (untracked) : add를 하지 않은 경우
    - 추적이 된 상태 (tracked) : 이미 add가 된 경우
        1. 수정 없음 (unmodified) : 변경사항 없으면
        2. 수정 함 (modified) : 변경사항 있으면
        3. 스테이지 됨 (staged) : 스테이징 하면

    - 예시
        - 새로운 파일을 만들었을 때
            - untracked(추적이 안된 상태)
        -add를 통해 스테이징
            -untracked -> staged
        - commit을 통해 snapshot
            -staged -> unmodified
            - 스테이징 -> 수정없음
        - 한번 add가 된 상태에서 파일 내용이 변경된 경우
            - unmodified -> modified


## 브랜치

- 여러 명의 개발자가 동시에 개발을 할 때 (협업)
- 새로운 Branch 를 추가
- 브랜치는 커밋을 가리킨다 (브랜치 -> 커밋) : 포인터 역할
- 저장소의 병렬된 버전
- 메인 분기, 기본 분기에 영향을 주지 않고 자유롭게 작업 가능
-원하는 작업일 때 다시 갈라진 브랜치(분기)를 브랜치에 병합 가능

## 병합 (Merge)

-두 버전의 합집합을 구하는 것

    1. merge commit : 병합 커밋
        - 각각 다른 내용이 충돌없이 합쳐지는 것
    2. fast-foward : 빨리 감기
        - 상태를 새로 만들 필요 없이 포인터만 변경하는 것
    3. conflict : 병합 충돌
        - 같은 파일, 같은 줄을 각각 다른 커밋이 수정하였을 때
        - 충돌의 경우 수동으로 병합 conflict를 해결해야 함.

- base 부랜치를 기준으로 compare 브랜치를 병합한다.
- 충돌 병합 해결하기
    - 충돌이 일어난 파일을 열어보면
```
<<<<<< HEAD
충돌 내용 1
======
충돌 내용 2
>>>>>> compare
```
    - 필요없는 내용들을 삭제하고, 수동으로 파일을 편집한 후 저장
    - 충돌이 해결된 파일을 스테이징(add)하고 커밋
    - 커밋 메시지가 자동으로 채워짐. (Merge ...)
-VS Code 충돌해결 기능
    - Accept Current Change (베이스 브랜치의 내용만 남김)
    - Accept Incoming Change (compare 브랜치의 내용만 남김)
    - Accept Both Change (둘 다 남김)

# Pull Request
- 공동 작업자에게 브랜치 병합을 요청하는 메시지를 보내는 것
- 원격 저장소에서 최근 베이스 브랜치보다 앞선 브랜치의 원격 커밋이 있을 경우
    - Compare & Pull Request 버튼 확인 가능
- 협업자에게 정중하게 병합을 요청한다.
    - base : 병합된 커밋이 들어갈 브랜치
    - compare : 병합이 될 브랜치
    - Able to Merge : 충돌 없이 병합될 수 있음.
    - 제목과 내용 부분에 협업자에게 도움이 되는 설명을 남긴다.
- 원격저장소에서 변경이 된 내용을 로컬에서 확인하기
    - git fetch : 원격저장소의 내용을 업데이트
    - git pull : 로컬로 가져와서 합치기


# Tag
- 개발이 완료되고 출시하게 될 때 => Release
- 버전 정보를 Tag를 통해 표시할 수 있다.
- Tag ==> 특정 커밋을 가리킨다.
- 특정 커밋을 기준으로 [태그 추가]
- 버전 관리
    - major 업그레이드 : 사용자들이 느끼는 큰 변화가 있는 경우
    - minor 업그레이드 : 작은 변화가 있는 경우
    - 유지보수 업그레이드 : 버그 수정, 유지보수 등의 변화
    - v1(major).0(minor).0(maintenece)
- Tag를 원격저장소에 Push 하면
- 깃허브 저장소에서 Realsease 버전 정보를 확인 가능하다.

# fork : 원격 저장소 복사해서 새로운 원격 저장소 만들기

- 원본 저장소에 직접 푸시를 할 수 있는 사람은 소유자
- 외 협력자(Collaborator)로 등록 되어야 함.
- 깃허브 저장소 'Setting' - 'Collaborator' => 'Add People'
- 에서 깃허브 계정(email 또는 username으로 검색하여 추가)

- 원본 저장소 소유자 입장에서 협락자가 많아질 수록
- 저장소 관리가 힘들어진다.
- 오픈 소스에 참여(기여)하고 싶은 개발자에게
- 원본 저장소를 fork 하게 해서
- fork한 저장소를 commit 을 하여 원본 소유자에게
- contribute -> pull request를 통해
- 원본 저장소에 파일을 추가할 수 있다.

- branch : 하나의 원격 저장소에서 분기점을 나눔
- fork : 여러 원격 저장소에서 분기점을 나눔