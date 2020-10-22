#在windows命令行窗口下执行

$ netstat -aon|findstr "8080" 
TCP     127.0.0.1:80         0.0.0.0:0               LISTENING       2448

#查看端口“8080”被哪个应用占用
$ tasklist|findstr "2448"
notepad.exe                     2016 Console                 0     16,064 K

#强行终止进程
$ taskkill /f /im notepad.exe
$ taskkill /f /pid 2152
