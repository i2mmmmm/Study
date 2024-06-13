### 1. 로컬 리포지토리 생성 또는 초기화

**새 리포지토리 생성**  
`mkdir new_project`  
`cd new_project`  
`git init`

**기존 리포지토리 초기화**  
`cd existing_project`  
`git init`  

### 2. 원격 리포지토리 연결

`git remote add origin https://github.com/i2mmmmm/repository.git`  

### 3. 변경 사항 추가 및 커밋
**모든 변경 사항 스테이징**  
`git add .`

**커밋 메시지와 함께 커밋**  
`git commit -m "Update my_project"`

### 4. 로컬 브랜치를 원격 리포지토리에 푸시
`git push -u origin main`
