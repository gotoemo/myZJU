# git 基础

## 1.&nbsp;基本操作

- 初始化仓库：`git init`
- 添加文件：`git add xxx`
- 提交文件：`git commit -m "备注信息"`
- 提交过的版本：`git log`（精简版用`git log --oneline`）

## 2.&nbsp; 版本回退&nbsp;`git reset`

- 保留工作区和暂存区：`git reset --soft 版本ID`
- 只保留工作区：`git reset 版本ID`(--mixed)
- 全部回退：`git reset --hard 版本ID`

## 3.&nbsp; 对比不同&nbsp;`git diff`

- 对比工作区和暂存区：`git diff`
- 对比工作区和版本库：`git diff HEAD`
- 对比暂存区和版本库：`git diff --cached`
- 对比两个版本：`git diff id1 id2`
- `HEAD`表示最新提交版本，`HEAD~`或`HEAD^`表示上一个提交版本，`HEAD~n`或`HEAD^n`
- `git diff`系列指令后加文件名可只查看该文件变化

## 4.&nbsp; 删除文件&nbsp;`git rm`

 - 删除工作区和暂存区中：`git rm filename`，执行完毕后要执行`git commit`提交修改
 - 只删除版本库：`git rm --cached filename`

## 5.&nbsp; 忽略管理

将不需要git管理的内容写入`.gitignore`文件中

<mark>`.gitignore`只能忽略未添加文件</mark>

- `.gitignore`文件上面比下面优先级高
- **可以使用通配符**
- **`!xxx`表示取反**
- 文件夹后面要加/
- 只忽略符合输入路径格式文件/文件夹

## 6.&nbsp; ssh

1. 配置公钥：在`~/.ssh`文件中执行`ssh-keygen -t rsa -b 4096`，将生成的公钥复制保存到GitHub设置中。如果创建的密钥不是默认路径，需要配置config文件，并写入如下几行：
```bash
# github
Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile  ~/.ssh/filename  #私钥文件名
```

## 7.&nbsp; 远程操作

- 克隆远程仓库：`git clone 仓库地址`
- 推送本地仓库：`git push`
- 拉取远程仓库：`git pull`
- 关联本地仓库和远程仓库：`git remote add origin 远程仓库地址`，*origin是给远程仓库起的别名，叫什么都行*
- 查看已关联的远程仓库：`git remote -v`
- 推送main分支：`git push -u origin main`
- 拉取：`git pull`，默认为`git pull origin main`
- 手动拉取：`git fetch`自行解决冲突