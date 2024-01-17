# GitFlow

> **클래식한 깃 전략**

![](https://hudi.blog/static/06afc02aa2ac15fd613f860c94d13cc2/ca1dc/git-flow.png)

Main, Develop, Supporting으로 브랜치를 구분하는 클래식한 깃 전략이다.

## Main 브랜치

바로 출시할 수 있는 프로덕션 코드를 모아두는 브랜치이다.  
 프로젝트 시작시 생성되며, 배포된 각 버전을 Tag를 통해 표시해둔다.

## Develop 브랜치

다음 버전 개발을 위한 코드를 모아두는 브랜치이다.  
 개발이 완료되면 Main 브랜치로 코드를 Merge한다.

## Feature 브랜치

기능 하나를 개발하기 위한 브랜치이다.  
 Develop 브랜치에서 생성하며, 기능 개발이 끝나면 Develop 브랜치로 Merge한다.  
 이때 Fast-Forward가 아닌 Merge Commit을 통해 Merge해야 한다.

## Release 브랜치

배포를 준비하기 위한 브랜치이다.
Develop 브랜치에서 생성되며, 소소한 데이터 수정이나 버그 수정에 사용된다.  
 배포 준비가 끝나면 Main과 Develop 브랜치에 Merge한다.

## Hotfix 브랜치

배포후 급히 해결해야 할 문제가 발생했을 때 생성하는 브랜치이다.  
 문제가 해결되면 Main과 Develop 브랜치에 Merge한다.

## 한계

웹 애플리케이션은 항상 최신 버전을 사용할 수 밖에 없기 때문에, 여러 버전을 지원할 필요가 없다.  
 이러한 이유로 웹 어플리케이션엔 적합하지 않다는 한계점이 존재한다.
