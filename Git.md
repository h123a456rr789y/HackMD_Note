---
title: Git
tags: CSTools
description: git
---



# Git 
## Git 基礎概念
### Git 版本控制
- 為了解決的問題：
    - 程式修改過後紀錄麻煩
    - 怕程式改錯又要重改，又改不回來
    - 多人合作Project時程式容易被覆蓋
- git 使用分散式版本控制系統
![](https://i.imgur.com/0jyhvjX.png)
    - 起初是 Linus torvalds大師為了要控制linux kernel版本而去開發的工具
- git 優點
    - 檔案的狀態（status）作為更新歷史記錄保存
    - 可以復原到以前的檔案狀態
    - 可以顯示編輯過後內容的差異
### 用 Repository 來管理歷史紀錄
- Repository功能
    - 記錄檔案或目錄狀態
    - 儲存內容的歷史修改記錄
    - 追蹤內容的狀態和版本
- Local Repository and Remote Repository 
    - Local Repository:
        - 給大家一起分享的 配有伺服器
    - Remote Repository:
        - 方便用個人用
- Create Repo
    - 在local端建立並init Repo
    - pull from遠端的 Repo
### Git Commit
- 用 git commit 可以把新增的東西丟到Repo中
- 執行完 commit後 Repo會產生一個Revision來紀錄新版舊版間的差異
- Tip:不同含意的更改盡量可以分開來提交以便日後查看（ex:debug, new function）
- Tip: Commit時提交訊息應包含
    - 修改內容的摘要
    - 修改的理由 
### Working Tree and Index（Staging Area）
- Working Tree 負責保存目前正在處理檔案的目錄還有git 指令的相關操作
- Index（Staging Area）是當在交到remote Repo間的一個檔案暫存區

## 開使用 Git 
### Prerequisite
- Create a Github Account
- Git Install 
- gitk 可用GUI來確認提交歷史 
```
Sudo apt install git
```
### Git 環境設定
```
git config --global user.name "Github-user-name"
git config --global user.email "Github-uesd-email"
git config --global color.ui true
git config --global core.editor vim
git config --global alias.co commit
git config --global alias.lg "log --color --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --"
```
### Create Repo
```
mkdir test
cd test
git init
```
- 建一個資料夾並進去裡面做 initialization

### Commit Files 
- 用來看Work Tree 和 Index 狀態
```
git status
```
- 將檔案加入Index （Staging Area）
```
git add <file>

##Add all files
git add.    
```
- 若檔案有更改 或需要比較檔案差別
```
#可用比較兩次上傳檔案之間的差別
 git diff

```
- 上傳檔案到remote Repo
```
# -m代表要丟上去給別人看的訊息 commit message
git commit -m "origin master"
```
- 看歷史提交紀錄
```
git log
```


## Shared Ropo
- Push :到遠端的Repo
- Clone:從遠端的Repo複製檔案
- Pull :同步遠端的Repo 來更新本地的Repo

### 連結到遠端 Repo
- 在Github創一個新的 Repo 並且勾選不用`.gitignore` `README.md` `LICENSE`如下
- `.gitignore` 是用來管理不想被丟上去的東西,`README.md` 則是做紀錄的檔案
![](https://i.imgur.com/4AujKtA.png)

- 去複製自己的 在Github 上的 Repository的 ssh 網址如下`git@github.com:username/git_test.git`
![](https://i.imgur.com/pVxnuVp.png)

- 用以下指令將本地端的資料夾和遠端Repo連結
```
git remote add origin git@github.com:username/git_test.git
```
- 並使用以下指令來將檔案push 上去遠端 Repo
```
git push -u origin master
```
- 通常系統會要求輸入你的遠端帳護名稱和密碼,可用以ssh-keygen來省下每次都要輸入密碼的麻煩
```
#產生你電腦的公鑰私鑰

ssh-keygen -t rsa -b 4096 -C "your_email@gmail.com"

#所生成的公鑰和私鑰在 ~/.ssh/目錄下  id_rsa 和id_rsa.pub中

#複製公鑰中的內容
cat ~/.ssh/id_rsa.pub 
``` 
隨後到GitHub網頁的Setting上新增你的Public SSH key 
![](https://i.imgur.com/rx0jB0G.png)

- 用git clone指令來複製遠端的Repo
```
git clone <repository> <directory>
#ex: git clone https://github.com/h123a456rr789y/HackMD_Note.git HackMD_Note
```
- 用git pull指令來同步遠端的Repo
```
git pull <repository> <refspec>
## git pull origin master
``` 
## 處理合併修改紀錄
- 如果你在push前，有其他人push 更新了遠端的Repo而沒有更新到你的本地端，你的push就會失敗，此時就需要合併在push上去
- 解決方法:
    - 先pull在push:用rebase的方式合併(不是萬能) 如果不行則需手動合併
    `git pull --rebase`
    - 不管他的強制push我現在的上去: -f 是強制的意思 (**別亂用**)
    `git push -f`
### Rebase 合併補充
1. 會先把本地 repo. 從上次 pull 之後的變更暫存起來 
2. 回復到上次 pull 時的情況 
3. 套用遠端的變更 
4. 最後再套用剛暫存下來的本地變更
```
#合併前
      D---E--F master
     /
A---B---C---G origin/master

#Rebase 合併

A---B---C---G---D'---E'---F'   master, origin/master

#merge 合併  

      D---E----F 
     /          \
A---B---C---G----H   master, origin/master
```
- 所以一旦出現conflict 就無法執行rebase，需要手動修復後，然後才可以繼續動作
- merge 如果發生 conflict，你只需要解決衝突一次，合成一個新，然後就可 commit 出去
> 改得比較多 -> 會有較多的 conflict -> merge
> 改得比較少 -> 會有較少的 conflict -> rebase




## 分支Branch 
- 將修改記錄的整體流程分開儲存，讓分開的分支不受其他分支的影響，所以在同一個數據庫裡可以同時進行多個不同的修改
- 分支間可以合併


### 分支的運用
- Integration分支(主要的分支):保持穩定是很重要的，因為新的分支會建立在它的上面，而且Integration分支是為了可以隨時建立發布版本的分支
- Topic分支(次要分支):Topic分支是為了**開發功能**或**修復錯誤**之類的任務所建立的分支。若同時進行多個任務時，您必須建立多個的Topic分支，修改完後再將Topic分支合併到Intergration分支
### 分支的切換
- 用 `checkout`指令:工作目錄裡的檔案會根據切換到不同的分支而呈現該分支最後提交的內容
- HEAD代表當前分支的最新提交名稱