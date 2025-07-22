## git 명령어 실습

git에 명령어들은 아래 그림과 같이 많이 있다.

<img width="2048" height="1448" alt="image" src="https://github.com/user-attachments/assets/fdaf7e47-23dc-431c-957d-301c5390ce47" />


### 기본 명령어(add, status, push log)

- 파일 변경 상태 추적
    - 추적되지 않는 파일에 대해서는 U로 표시
        
       <img width="253" height="52" alt="image" src="https://github.com/user-attachments/assets/bd226ba5-eb38-4d3e-a46b-eb272dbc928b" />

        
        <img width="1202" height="219" alt="image" src="https://github.com/user-attachments/assets/2e4b7476-3eaf-4059-a6cd-e7de532c15e9" />

        
- 파일 상태 추적하기 or 파일 변경 올리기
    - git add 명령어를 통해서 파일 상태 추적하기로 변경
        
        <img width="1212" height="402" alt="image" src="https://github.com/user-attachments/assets/b888aeae-953a-4075-b7a1-906fb672c66a" />

        
- 파일 커밋하기
    - git commit 입력 시
        
        <img width="1220" height="212" alt="image" src="https://github.com/user-attachments/assets/e134de53-03db-4d33-a0ff-7336910ff1dd" />

        
    - 아래와 같은 페이지로 가서 커밋 메시지 작성 가능
        
        <img width="1071" height="240" alt="image" src="https://github.com/user-attachments/assets/449dfb2c-ca97-4600-979c-a76a67756d5a" />

        
    - 번외로 커밋과 메시지 까지 한꺼번에 하고 싶다면 -m 옵션 사용하기
        - git commit -m “add test.py”
- tree 통해서 파악
    - 보면 성공적으로 커밋이 기록된것을 확인 가능
        
        <img width="2048" height="447" alt="image" src="https://github.com/user-attachments/assets/3e5d5b25-be8f-4a4d-92d3-9e88b745bff4" />

        
- git hub에 올리기
    - git push 명령어를 통해서 파일 올리기
        
        <img width="1211" height="361" alt="image" src="https://github.com/user-attachments/assets/31a670d0-7a5d-4099-bf2e-650dab0e11b2" />

        
- 성공적으로 올라간 모습
    
    <img width="1797" height="364" alt="image" src="https://github.com/user-attachments/assets/690aa089-9082-4ce7-a311-2d25edc3e4da" />

    
- 깃 로그 확인하기
    - git log 이용하서 커밋 로그 확인 가능
    - Sourcetree에서 보이는 것과 동일함
        
        <img width="1353" height="614" alt="image" src="https://github.com/user-attachments/assets/7cd64eaf-0e38-4eb8-a024-30e051006cda" />

        
    - git 홈페이지 가면 아래와 같이 git log를 확인할 수 있음
    
    <img width="1370" height="553" alt="image" src="https://github.com/user-attachments/assets/174d62f0-8a70-4f88-a943-c3bed2d74a64" />

    
- 수정이 발생한 경우
    - git status 했을 때 수정된 내용이 아래와 같이 표현됨
        
        <img width="1199" height="367" alt="image" src="https://github.com/user-attachments/assets/33682186-d61a-43a3-8b4c-4a767ea4b836" />

        

### 시간 타임 캡슐

- reset
    - 과거로 돌아 갔을때 이전 타임캡슐을 삭제함
        
        <img width="1186" height="144" alt="image" src="https://github.com/user-attachments/assets/597e5c3c-742d-420a-8b8d-6d713a552aed" />

        
- revert
    - 이전 내역을 없애는게 아니라 했던걸 거꾸로 하는 작업
    - 겹치는 부분이 있어서 삭제할지 아니면 더할지 물어봄
        
        <img width="2048" height="453" alt="image" src="https://github.com/user-attachments/assets/b38b16db-aee8-4348-8b25-08c0aa384fbb" />

        
    - 이 부분에서 문제가 발생했다는 점을 보여줌
        
        <img width="2048" height="158" alt="image" src="https://github.com/user-attachments/assets/aeace737-99ba-44f8-b2ab-8e1d71872af7" />

        
    - rm을 통해서 나는 지우고 계속 진행하도록 함
        
        <img width="1523" height="490" alt="image" src="https://github.com/user-attachments/assets/e50c1a49-fbd3-4219-9d97-8a41d92b4f67" />
        
    - 그러면 결과 적으로 test.py는 없어짐
        
        <img width="297" height="220" alt="image" src="https://github.com/user-attachments/assets/3f63904e-563c-4da1-b581-ec4c38ed6940" />

        
    - Tree로 살펴보면 아래와 같음
        
        <img width="2048" height="812" alt="image" src="https://github.com/user-attachments/assets/406697b7-1f57-49da-bca7-338fc1780b7d" />


        

### Branch

- 사용하는 이유
    - 프로젝트를 하나 이상의 모습으로 관리할때
    - 여러가지 작업들이 각각 독립되어 진행될때
- git 브랜치 생성 및 변경하기
    - git branch <이름> : 이름의 브랜치 생성
    - git branch: 리스트 보여줌
    - git switch <이름> : 이름의 브랜치로 이동됨<

<img width="1307" height="525" alt="image" src="https://github.com/user-attachments/assets/bca8c220-a803-4965-abc9-7898246f38cf" />


- git 브랜치 생성 및 변경하기 합쳐서 진행
    - git switch -c 이름

<img width="1300" height="256" alt="image" src="https://github.com/user-attachments/assets/26bf6ee0-3645-497f-8116-17a477e03327" />


- git 브랜치 이름 변경
    - git branch -m 이전이름 변경이름

<img width="1237" height="324" alt="image" src="https://github.com/user-attachments/assets/f4fc6b27-8685-4207-a255-617a201d5965" />


- 그림과 같이 Branch 별로 따로 관리

<img width="791" height="282" alt="image" src="https://github.com/user-attachments/assets/d236352c-b9d6-4bda-9a93-85e4605506e9" />


### Branch 합치기

- merge
    - 두개의 가지를 이어 붙히는 과정(새로운 커밋이 생겨남)
    - 합치고자 하는 merge로 이동한 후 합치고자 하는 브랜치 적기
        
        <img width="1263" height="277" alt="image" src="https://github.com/user-attachments/assets/fd61a92b-2da5-440c-9385-ee254ea87f15" />

        
    - 결과를 보면 합치는 걸 볼 수 있음
        
        <img width="439" height="206" alt="image" src="https://github.com/user-attachments/assets/bb87ead4-2355-46a4-8527-b9a70918f1f4" />

        

### PR

- 의미
    - 남의 저장소의 내용을 내가 가져와서 업데이트한 뒤에 ‘이 부분 제가 이렇게 바뀌었는데 제가 작업한 부분도 적용해주세요!’라는 요청을 보내는 것이다.
- Rebase
    - 새로운 커밋을 같다 붙히는 경우임
    - 합쳐지는 애한테서 합치고자 하는 애로 rebase 진행함
        
        <img width="1219" height="152" alt="image" src="https://github.com/user-attachments/assets/4f4c6ef5-5e0b-4ac3-b455-8b67eec87813" />

        
    - 결과를 보면 아래와 같음
        
        <img width="930" height="341" alt="image" src="https://github.com/user-attachments/assets/89e681ac-886d-46aa-ad60-0ad958d5d9a3" />

        
- 자기소개 PR 보내보기
    - 아래 그림과 같이 PR 전송해봄
    
    <img width="966" height="503" alt="image" src="https://github.com/user-attachments/assets/3c37bbd9-89dc-49f5-abb7-a3de3b563ee6" />

### .gitignore

- 의미
    - 깃에서 관리하지 않고자 하는 파일을 정의
    - 여기에 등록해두면 git에 올라갈 때 아래 파일들은 관리되지 않음
    <img width="352" height="594" alt="image" src="https://github.com/user-attachments/assets/26ae5b9c-385a-4b50-9353-cf3525b8d554" />
