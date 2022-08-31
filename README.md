# git.alias
將常用的一系列 git 下指令流程，製成一整串自動化指令

<code>
git config --global alias.gg '!$(if [ $1 ] ; then target_branch=$1; else target_branch=$(git branch --show-current); fi && git checkout develop && git merge $target_branch --no-ff --no-edit && git push origin develop && git checkout $target_branch && git rebase develop) #'
</code>  
  
***


#### 指令流程
----------------
  
* 判斷是否有輸入 分支名稱

  > 有提供，以手動輸入的字串為主 target_branch=$1
  
  > 若無提供，則以目前的分支名稱為主 target_branch=$(git branch --show-current)

* 切換到 develop 分支

  >  git checkout develop 

* 合併指定分支，執行指令 

  >  git merge $target_branch --no-ff --no-edit

* git push 推送到 server 伺服器端 分支 develop

  >  git push origin develop

* 將 client 本地端 分支，切換為剛才指定的分支 target_branch 

  > git checkout $target_branch

* 在 target_branch 分支，執行 rebase 到 develop 

  > git rebase develop

* 最後的 # 是忽略手動輸入的參數

  >  \#

* 完成！



***



#### 使用方式1: 偵測目前分支
----------------

* 開啟 terminal 終端機

* 輸入指令

  >git config --global alias.gg '!$(if [ $1 ] ; then target_branch=$1; else target_branch=$(git branch --show-current); fi && git checkout develop && git merge $target_branch --no-ff --no-edit && git push origin develop && git checkout $target_branch && git rebase develop) #'

* 檢查別名 gg 是否已生成

  >git config --global -l 
  
* 確認沒問題的話，按 q 可離開

  >q

* 在終端機內，執行 cd xxxx 切換目前位置到專案路徑內

* 在數個 commit 指令之後，目前處理的功能區塊，告一段落

* 在終端機內，輸入 git gg

* 完成！

***


#### 影片 DEMO
----------------

https://user-images.githubusercontent.com/6315361/187609174-a5b48585-6ca7-45db-bef0-54caf0f5635c.mov



***


#### 使用方式2: 合併指定分支
----------------


* 在終端機內，執行 cd xxxx 切換目前位置到專案路徑內

* 在數個 commit 指令之後，目前處理的功能區塊，告一段落

* 在終端機內，輸入 git gg {{ custom_branch_name | 指定分支名稱 }}
  >git gg feature__demo

* 完成！

***

#### 影片 DEMO 2
----------------

https://user-images.githubusercontent.com/6315361/187614955-1a5dd0c3-8856-4255-9447-89bd9f21f2cb.mov

***

#### 使用方式2: 使用情境
----------------


* 當同時有多個分支，互相切換，並各自都有提交 commit

* 假設目前分支位置在 master or feature__xxx

* 分支 feature__demo 已提交 commit 並確認 目前工作段落已完成

* 就可以在 master 或 其他分支

* 指定 feature__demo 合併至 develop

* 不需要重新切回 feature__demo 才執行指令 git gg 

***

#### GIT 分支線圖 成果
----------------

<img width="1787" alt="git alias demo result" src="https://user-images.githubusercontent.com/6315361/187618127-be2f92ea-cd96-4803-adce-def379e30a9e.png">


***

#### 歡迎請我喝杯咖啡  ☕ ❤️ 😍
----------------

USDT Tron (TRC20) 錢包地址  
  
TVaJYd7DyqJ8hYVgpaZkWJs6oDnscyvbEm
    
<img width="300px" height="300px" alt="USDT Tron (TRC20) address" src="https://user-images.githubusercontent.com/6315361/187622580-053baf74-9114-43b7-be39-aefa34bf410e.png">
