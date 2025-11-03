깃헙 레포지토리를 로컬로 복사하기
```bash
git clone <레포지토리 주소>
```

`main` 브랜치에서 작업하다가 "새로운 기능"을 추가해버림
`feature/api` 브랜치로 옮겨야 함
```bash
# 1. 현재 커밋 확인
git log --oneline

# 2. 새 브랜치로 커밋 옮기기
git switch -c feature/new-api # 현재 상태로 브랜치 생성

# main 브랜치 원상복구
git switch main
git reset --hard origin/main

# 4. 새 브랜치에서 계속 개발 
```

