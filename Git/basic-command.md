# basic command
>git 기본 문법 정리

## 초기 설정
- git을 설치 후 최초 한번만 실행
```bash
git config --global user.email <이메일>
git config --global user.name <이름>

```

## git 저장소 만들기

- `git init`
    - `git directory` 및 하위 directory를 생성해주는 명령어
    - 관리하고 싶은 최상위 위치에서 실행

## git 상태 체크

- `status`
    -현재 git으로 관리되고 있는 파일/폴더의 상태를 출력

## 코드 수정하고 저장소에 저장하기

- `add`
    - `git add <파일/폴더이름>`
    - `working directory`에서 `staging area`로 추가
    - 일반적으로 모든 파일, 폴더를 추가하기 위해 아래의 코드를 사용
        - `git add .` 현재 디렉토리의 모든 파일, 폴더를 add

- `commit`
    - `git commit -m "메세지"`
    - `staging area`에 올라간 파일들의 스냅샷을 찍어서 `.git directory`에 저장
    - 일반적으로 `-m` 옵션을 넣어서 메세지를 추가하여 등록

## 원격저장소에 업로드하기

- `remote add`
    - `git remote add origin <URL>`
    - 원격저장소 주소를 origin 이라는 이름으로 저장

- `push`
    - `git push <원격저장소이름-origin> <브랜치이름-master>`
    - 원격저장소에 브랜치를 업로드, 원격저장소이름과 브랜치이름은 바뀔 수 있음

## Git 사용 요약
![Git_LifeCycle](./asset/Git_lifecycle.png)

1. 수정한 code file을 저장한다 (Local working directory, **Untracked 상태**)
2. `git add <파일/폴더` (Add the file, **Staged 상태**) 
    - 작업한 파일/폴더를 **Staging area**에 업로드한다.
    - `git add .` 입력시 작업한 디렉토리의 모든 내용을 업로드 한다.
3. `git commit -m "<메세지>"` (.git에 저장, **unmodified 상태**)    
    - **Staging area**에 업로드된 파일들의 스냅샷을 찍어 `.git` 디렉토리에 저장한다.
    - `git -m "메세지"` 로 변경사항에 대한 내용을 기록할 수 있다.

4. `git push origin master` 
    - **원격저장소** (여기서는 설정한 github)에 **branch(master)**을 업로드한다.

> 코드 및 파일 변동사항이 있을 시 저장 후 add, commit을 진행한다.
