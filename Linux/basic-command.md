# Linux basic command
>리눅스 기본 명령어 정리

- `pwd` (print working directory)
    - 현재 작업중인 폴더 경로를 출력

- `ls` (list)
    - 현재 작업중인 폴더 내에 있는 파일/폴더를 출력
    - `ls -a` (optional) : 숨김처리 되어있는 파일/폴더까지 출력) 
        - . : 현재폴더
        - .. :  상위폴더

- `cd` (change directory)
    - 이동하고 싶은 폴더로 위치 변경
    - `cd <폴더이름>` 폴더이름으로 이동
    - ~ : 홈화면 (User 폴더 - Dohyeon)
    - 이니셜 문자작성 후 tap키 누르면 자동완성 됨
    
- `mkdir` (make directory)
    - 폴더를 생성
    - `mkdir <폴더이름>` 폴더이름으로 새로운 폴더를 생성

- `touch <파일이름>` 파일이름으로 새로운 파일을 생성

- `rm <파일이름.확장자>` 파일이름.확장자 의 **파일**을 삭제
    - `rm -r <폴더이름>` 폴더d이름에 해당하는 폴더 삭제, -r : recursive (재귀)