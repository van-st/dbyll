---
layout: post
title: simple git using
categories: git
fullview : true
comments : true
---
<h1> Initial </h1><br>
* 어디까지나 주의사항 : 이 모든 내용은 github에서만 실행해보았다. 다른 git은 내용은 같지만 address부분에서 미묘하게 차이가 날 수 있다.<br>
<br>
<h1> Basic </h1><br>
<h3> GIT을 처음 사용할 시 </h3><br>
<h5>git init</h5> git을 처음 사용할 때에는 git 저장소라는 것이 필요하다. 이는 작업할 때는 안보이지만, git에서 일어난 변경사항을 모두 담고있는 폴더이다. 참고로 이 git폴더를 지울 때에는 관리자 권한이 필요하다.<br><br>
<h5>git remote add origin [address]</h5> 자신이 git을 저장할 장소를 설정한다. github에 있는 repository에 저장하려고 한다면 'https://github.com/[자기 닉네임]/[자기 git repository].git'이라고 [address]자리에 적으면 된다.<br>
예시)git remote add origin https://github.com/van-st/asdf.git<br><br>
<h5>git commit</h5> 메세지 없이 그냥 commit하는 것. commit은 git에 add한 것을 확정지을 때 쓴다. <br><br><br>
<h5>git clone [address]</h5> git에 올려진 repository에 있는 내용을 자신의 작업창에 옮기고 싶을 때 쓴다. 여기서 말하는 address는 repository의 address를 나타낸다.<br><br><br>
<h5>git add [file name] </h5> [file name] 파일을 git 저장소에 첨부한다. <br><br>
git commit -m "[message]" : commit message를 남긴 채로 커밋한다.<br><br>
*주의* : 커밋 없이는 git push를 할 수 없다. git에 더해져 있는 내용들이 확정된 것인지 아닌 지 알 수 없기 때문이다.<br><br>
git push : 온라인 상에 git을 올린다. <br><br>
* 주로 git add [file name] 한 뒤 git commit -m "message" 를 하고 git push를 한다.<br><br>
<h3>추가 사항</h3><br>
<h4>address에 관하여 </h4><br><br>
<h5>https://를 쓰는 경우</h5> https://github.com/[github 아이디]/[github에 올릴 레포].git<br>
<h5>ssh키를 쓰는 경우</h5> git@github.com:[github 아이디]/[github에 올릴 레포].git<br><br><br>
<h4>명령어에 관하여 </h4><br>
<h5>git remote set-url origin [address] </h5> 깃의 repo를 바꾸는 명령어이다. 이 명령어를 실행하면 [address]로 origin의 주소가 바뀐다.<br>
<br>
<br>
<h1>Normal </h1><br>
git 브랜치란? 특정 커밋에 대한 참조이다.<br><br>
브랜치를 많이 만들어도 메모리나 디스크 공간에 부담이 되지 않기 때문에, 많이 만들어도 된다. <br><br>
<br>
git branch [브랜치명] : [브랜치명]을 가진 새로운 브랜치를 만든다.<br>
git checkout [브랜치명] : [브랜치명]을 가진 브랜치로 이동한다.<br>
* checkout을 하지 않으면 master가 가리키는 commit과 branch가 가리키는 commit이 의도치 않게 다를 수 있다. 따라서 checkout으로 같은 곳을 가리키게 하거나 의도한데로 가리키도록 checkout을 사용해야 한다.<br>
<br>
브랜치 합치기 (Merge)란? 두 개의 부모를 가리키는 특별한 커밋을 만들어 내는 것. 즉 두 부모의 작업내역과 그 부모의 부모들의 모든 작업내역을 포함해 새로운 브랜치를 만들어 내는 것.<br>
* 순서로 암기하는 것이 좋다.<br>
git branch bugFix : git branch bugFix가 생성되었다.<br>
git checkout master : master쪽을 마음껏 움직일 수 있게 되었다.<br>
git merge bugFix master : bugFix를 master 가지로 merge했다.<br>
<br>
리베이스란? (rebase) 브랜치끼리의 작업을 접목하는 방법 중 하나. 커밋들을 모와서 복사한 뒤, 다른 곳에 떨궈 놓는 것.<br>
장점 : 커밋들의 흐름을 보기 좋게 한 줄로 만들 수 있다.<br>
	즉, 저장소의 커밋 로그와 이력이 한결 깨끗해진다.<br>
따로따로 개발한 bugFix와 masteR이라는 브랜치가 있다고 하자. 이 둘을 머지할 수도 있지만 그렇게 하면 커밋 로그가 이리갔다 저리갔다 하기 때문에 이 둘을 순서대로 개발한 것처럼 보이기로 했다. (누가 먼저고 누가 나중이냐는 bugFix에서 개발한 것을 name이 쓰느냐 마느냐에 따라 달려있다.)<br>
같이 있을 때, bugFix를 선택하고 git rebase master라고 치면 bugFix가 밑으로 내려가고 대신 bugFix가 원래 가리키고 있었던 커밋은 남는다. (bugFix가 밑으로 내려가면서 가르키는 건 bugFix가 가리키고 있던 커밋의 복사본)<br>
이걸 해결하기 위해서 master를 checkout으로 선택한 뒤, git rebase bugFix 를 하면 master가 bugFix의 부모쪽에 있었기 때문에 단순히 그 브랜치를 더 앞으로 가리키게 이동하는 것으로 문제가 해결된다. (bugFix가 있었던 원래 commit을 접속할 브랜치가 없기 때문)<br>
*참고 : 너무 헷갈릴 때에는 checkout만 움직인다고 생각하면 편하다. master는 항상 최신것을 가리켜야 하므로라고 하면 이해가 쉽다.<br>
<br>
git에서 작업 되돌리기.<br>
1. git reset : 예전의 커밋을 가리키도록 이동시키는 방식으로 변경 내용을 되돌리는 것. <br>
* 단점 : 히스토리를 고쳐쓰기 때문에 다른 사람이 작업하는 리모트 브랜치에는 쓸 수 없다.<br>
*실행시 : git reset HEAD~1<br>
<br>
<br>
2. git revert : 변경분을 되돌리고 이 되돌린 내용을 다른 사람과 공유하기 위해서 쓰는 것.<br>
자신이 되돌린 내용을 복사한 새로운 브랜치를 만듬.<br>
*실행시 : git revert HEAD<br>
<br>
<br>
cherry-pick? 특정 commit을 branch로 복사하고 싶을 때! 개별 커밋을 골라서 HEAD 위에 떨어뜨릴 수 있음.<br>
git checkout [branch이름]<br>
git cherry-pick [복사하고 싶은 commit]<br>
<br>
<br>
<br>
로컬에 쌓인 커밋<br>
불필요한 디버그용 코드들이 들어가지 않게 하기 위해서 Git의 마법을 사용합니다!<br>
git rebase -i : 어떤 커밋을 취하거나 버릴지를 선택하는 것, 커밋의 순서를 바꾸는 것.<br>
git rebase -i HEAD~# : HEAD에서 #만큼 수를 바꾸거나 버린다.<br>
<br>
<br>
git commit --amend : 커밋 내용을 정정함.<br>
<br>
<br>
Link : <http://learnbranch.uriqit.com/><br>
