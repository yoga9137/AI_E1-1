# 미션1. 개발자용 작업실 구축 미션
## Git 저장소: AI_E1-1  

## 1. 프로젝트 개요
이 저장소는 로컬 개발 워크스테이션 구축 과정을 기록한 저장소이다.
주요 목표는 다음과 같다.
- 터미널을 이용한 작업 디렉토리 구성
- Docker 설치 및 동작 확인
- Dockerfile 기반 웹 서버 컨테이너 실행
- 포트 매핑을 통한 브라우저 접속 확인
- 바인드 마운트를 통한 변경 반영 확인
- Docker 볼륨을 통한 데이터 영속성 확인
- Git/GitHub/VSCode 연동 확인

## 2. 실행 환경
- OS: Windows / Ubuntu  
- Shell: PowerShell / bash  
- Terminal: VSCode Terminal / Windows Terminal / Terminal  
- Docker: `docker --version` 결과  
- Git: git version 2.56.0.windows.4  
- VSCode: 1.144.1 (261c84cb1eddf11235f9e2c921425e9663fbe556, x64).  

## 3. 수행 항목 체크리스트
- [ ] 터미널로 디렉토리 생성 및 권한 확인
- [ ] Docker 설치 확인
- [ ] Docker 기본 명령 실행
- [ ] Dockerfile 작성
- [ ] Docker 이미지 빌드
- [ ] 컨테이너 실행
- [ ] 포트 매핑 접속 확인
- [ ] 바인드 마운트 변경 반영 확인
- [ ] Docker 볼륨 영속성 확인
- [x] Git 설정
- [ ] GitHub 저장소 생성 및 push
- [ ] VSCode GitHub 연동 확인

## 4. 터미널 조작 로그

## 5. 권한 실습 로그

## 6. Docker 설치 및 기본 점검

## 7. Docker 기본 운영 명령

## 8. 컨테이너 실행 실습

## 9. Dockerfile 기반 커스텀 이미지 제작

## 10. 포트 매핑 및 접속 증거

## 11. 바인드 마운트 검증

## 12. Docker 볼륨 영속성 검증

## 13. Git 설정 및 GitHub 연동

## 14. 보안 및 개인정보 보호 점검

## 15. 트러블슈팅  

문제 1. VS Code 에서 깃허브 저장소와 연동할 때 오류 발생  
  
문제  
PS C:\Workspace\E1_1> git clone https://github.com/yoga9137/AI_E1-1.git .           
fatal: destination path '.' already exists and is not an empty directory.  

원인 가설  
git clone 명령어는 지정한 대상 경로(여기서는 .으로 표현된 현재 디렉터리)가 완전히 빈 디렉터리여야만 실행됨.  
현재 폴더(C:\Workspace\E1_1) 내부에 이미 파일, 폴더 또는 Git 설정 파일(.git 등)이 존재하여 충돌이 발생한 것.  

해결  
C:\Workspace 폴더 내부의 E1_1 폴더를 삭제한 후, 다시 명령을 실행했다.  
PS C:\Workspace> git config --global user.name yoga9137        
PS C:\Workspace> git config --global user.email yoga9137@gmail.com  
PS C:\Workspace> git clone https://github.com/yoga9137/AI_E1-1.git .  
Cloning into '.'...  
remote: Enumerating objects: 70, done.  
remote: Counting objects: 100% (70/70), done.  
remote: Compressing objects: 100% (44/44), done.  
remote: Total 70 (delta 19), reused 0 (delta 0), pack-reused 0 (from 0)  
Receiving objects: 100% (70/70), 22.77 KiB | 5.69 MiB/s, done.  
Resolving deltas: 100% (19/19), done.  
PS C:\Workspace>  
      
    
문제 2. VS Code 에서 깃허브로 Readme.md 파일을 업로드할 때 오류 발생  
문제  
PS C:\Workspace\E1-1> git push origin main  
To https://github.com/yoga9137/AI_E1-1.git  
 ! [rejected]        main -> main (non-fast-forward)  
error: failed to push some refs to 'https://github.com/yoga9137/AI_E1-1.git'  
hint: Updates were rejected because the tip of your current branch is behind  
hint: its remote counterpart. If you want to integrate the remote changes,  
hint: use 'git pull' before pushing again.  
hint: See the 'Note about fast-forwards' in 'git push --help' for details.  

원인 가설  
원격 깃허브 저장소(Remote)와 내 컴퓨터(Local)의 소스코드가 서로 동기화되지 않아서 발생한 push 거부 오류.  

해결  
방법 1. 깃허브 변경 사항을 내 컴퓨터로 가져와 합치기 (권장)  
> git pull origin main --allow-unrelated-histories

방법 2. 깃허브 저장소를 내 코드로 강제 덮어쓰기 (주의)  
> git push origin main --force 또는
> git push origin main --f  
    
    
문제 3. 방법1. 을 사용할 경우, 아래의 오류 메시지 발생  
문제  
PS C:\Workspace\E1-1> git pull origin main --allow-unrelated-histories  
remote: Enumerating objects: 11, done.  
remote: Counting objects: 100% (11/11), done.  
remote: Compressing objects: 100% (6/6), done.  
remote: Total 9 (delta 3), reused 0 (delta 0), pack-reused 0 (from 0)  
Unpacking objects: 100% (9/9), 3.24 KiB | 100.00 KiB/s, done.  
From https://github.com/yoga9137/AI_E1-1  
   branch            main       -> FETCH_HEAD  
   2846597..32c6d48  main       -> origin/main  
Updating 93cfe29..32c6d48  
error: Your local changes to the following files would be overwritten by merge:  
        README.md  
Please commit your changes or stash them before you merge.  
Aborting  

원인 가설  
내 컴퓨터의 README.md 파일에 아직 커밋(저장)하지 않은 수정 내용이 남아있기 때문에 발생함.  
이 상태에서 원격 저장소의 내용을 가져오면(pull), 내가 지금 수정한 내용이 덮어씌워져 사라질 수 있으므로  
Git이 안전을 위해 작업을 중단(Aborting)시킨 것.

해결  
1단계: 내 컴퓨터의 변경 사항을 먼저 커밋(저장)하기  
> git add README.md  
> git commit -m "로컬 README 수정 및 트러블슈팅 기록"  

2단계: 깃허브 내용 가져와서 합치기 (다시 pull)
> git pull origin main --allow-unrelated-histories  

3단계: (필수 체크) 충돌(Conflict) 해결하기  
• 이 명령어를 치면 깃허브의 README.md와 내 컴퓨터의 README.md 내용이 겹치기 때문에  
충돌(Conflict)이 발생할 확률이 높음  
• 충돌이 발생하면 VS Code에서 README.md 파일이 열리며 초록색/파란색 코드로 현재 변경 사항과 수신 변경 사항을 비교해 줌  
• 상단의 Accept Both Changes(양쪽 변경 사항 모두 수락)를 누르거나, 지우고 싶은 부분을 직접 텍스트로 정리한 후
  파일을 저장(Ctrl + S)합니다.  
• 충돌을 해결했다면 아래 명령어로 마무리 커밋을 합니다.  
> git add README.md  
> git commit -m "깃허브와 로컬 README 충돌 해결"  

4단계: 깃허브에 최종 업로드하기  
> git push origin main  

참고. 만약 복잡한 과정 없이 깃허브 내용으로 덮어쓰고 싶다면?  
현재 내 컴퓨터에 있는 README.md 수정본이 중요하지 않고,  
깃허브 웹사이트에 올라와 있는 최신 코드를 그대로 가져와 덮어씌우고 싶다면  
아래 명령어로 로컬 상태를 강제 초기화한 뒤 진행하셔도 됩니다.  
(주의: 커밋하지 않은 내 현재 수정본은 사라집니다.)  
> git reset --hard HEAD  
> git pull origin main  
       
        
## 부록 A. AI 질문 (모델: GPT-5.5)

질문1  
\- 1. 미션 소개, 2. 최종 결과물 내용을 붙여넣음.  

질문2  
\- 4. 기능 요구 사항 내용을 붙여넣고 "위의 미션은 4. 기능 요구 사항을 만족해야된다고 하는데...  
  이러한 요구 사항을 만족하도록 최종 결과물을 어떻게 만들면 되는지 절차적으로 다시 설명해줘." 라고 요청함.
  
## 부록 B. 참고 내용  
\- VS Code 에서 Commit 버튼을 누르기 전에 바로 위의 Message 에 수정한 내용을 꼭 넣을 것.
