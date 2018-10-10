GIT使用密技
===
###### tags: `git`

# Commit
[當commit都丟出去了，結果還有一個檔案忘了add](https://stackoverflow.com/questions/40503417/how-to-add-a-file-to-the-last-commit-in-git)

```bash=
git add the_left_out_file
git commit --amend --no-edit
```



# Branch

## 刪除遠端分支
如果不再需要某個遠端分支了，比如搞定了某個特性並把它合併進了遠端的 master 分支（或任何其他存放穩定代碼的分支），可以用這個非常無厘頭的語法來刪除它：git push [遠端名] :[分支名]。如果想在伺服器上刪除 serverfix 分支，執行下面的命令：

```shell=
$ git push origin :serverfix
```

https://git-scm.com/book/zh-tw/v1/Git-%E5%88%86%E6%94%AF-%E9%81%A0%E7%AB%AF%E5%88%86%E6%94%AF


## add remote branch
First, you create your branch locally:

```shell=
git checkout -b <branch-name> # Create a new branch and check it out
```
The remote branch is automatically created when you push it to the remote server. So when you feel ready for it, you can just do:

```shell=
git push <remote-name> <branch-name> 
```


Where <remote-name> is typically origin, the name which git gives to the remote you cloned from. Your colleagues would then just pull that branch, and it's automatically created locally.

Note however that formally, the format is:

```shell=
git push <remote-name> <local-branch-name>:<remote-branch-name>```

https://stackoverflow.com/questions/1519006/how-do-you-create-a-remote-git-branch