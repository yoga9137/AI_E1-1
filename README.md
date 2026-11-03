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
- Shell: bash / PowerShell
- Terminal: Terminal / Windows Terminal / VSCode Terminal
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
- [ ] Git 설정
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
> git push origin main --force  


## 부록. AI 질문 (모델: GPT-5.5)

질문1  
\- 1. 미션 소개, 2. 최종 결과물 내용을 붙여넣음.  

질문2  
\- 4. 기능 요구 사항 내용을 붙여넣고 "위의 미션은 4. 기능 요구 사항을 만족해야된다고 하는데...  
  이러한 요구 사항을 만족하도록 최종 결과물을 어떻게 만들면 되는지 절차적으로 다시 설명해줘." 라고 요청함.
