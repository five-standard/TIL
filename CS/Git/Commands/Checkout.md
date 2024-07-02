# Checkout

> **git checkout**

깃에서 브랜치를 그냥 이동하려 하면, 커밋되지 않은 파일로 인해 오류가 발생한다.
이를 임시로 저장하고 다른 브랜치로 이동하기 위해 checkout을 사용한다.  
 이 외에도 이전 커밋으로 되돌리기 위해 checkout을 사용하는 경우도 있다.

## 명령어

```bash
git checkout [-q] [-f] [-m] [<branch>]
git checkout [-q] [-f] [-m] --detach [<branch>]
git checkout [-q] [-f] [-m] [--detach] <commit>
git checkout [-q] [-f] [-m] [[-b|-B|--orphan] <new-branch>] [<start-point>]
git checkout [-f] <tree-ish> [--] <pathspec>…​
git checkout [-f] <tree-ish> --pathspec-from-file=<file> [--pathspec-file-nul]
git checkout [-f|--ours|--theirs|-m|--conflict=<style>] [--] <pathspec>…​
git checkout [-f|--ours|--theirs|-m|--conflict=<style>] --pathspec-from-file=<file> [--pathspec-file-nul]
git checkout (-p|--patch) [<tree-ish>] [--] [<pathspec>…​]
```

---

**참고**  
https://git-scm.com/docs/git-checkout (Git 공식 문서)
https://www.freecodecamp.org/korean/news/git-remote-branch-checkout/ (FreeCodeCamp 설명서)
