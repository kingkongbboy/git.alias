# git.alias
將常用的一系列 git 下指令流程，製成一整串自動化指令

<code>
git config --global alias.gg '!$(if [ $1 ] ; then target_branch=$1; else target_branch=$(git branch --show-current); fi && git checkout develop && git merge $target_branch --no-ff --no-edit && git push origin develop && git checkout $target_branch && git rebase develop) #'
</code>  
  
***


#指令流程  
  
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


#使用方式  

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


#影片 DEMO  

https://user-images.githubusercontent.com/6315361/187609174-a5b48585-6ca7-45db-bef0-54caf0f5635c.mov



