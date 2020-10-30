###### 设置用户信息

```shell
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

###### 关联远程分子

```shell
git branch --set-upstream-to=origin/master master
```

###### 查看分支创建时间

```shell
git reflog show --date=iso master
```

###### 退到/进到 指定commit的sha码

```shell
$ git reset --hard a8f946f     
```

######  强推到远程

```shell
$ git push origin HEAD --force  
```

