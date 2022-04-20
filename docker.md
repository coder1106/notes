docker服务挂了查找原因
#inspect这个容器查看具体信息
docker inspect <container_id>
关注State部分
    "State": {
    "Status": "exited",
    "Running": false,
    "Paused": false,
    "Restarting": false,
    "OOMKilled": false,
    "Dead": false,
    "Pid": 0,
    "ExitCode": 137,
    "Error": "",
    "StartedAt": "2016-12-12T02:06:08.243092091Z",
    "FinishedAt": "2016-12-13T01:57:59.927017549Z"
},
#查看容器log
docker logs <container_id>
#查看docker deamon log
journalctl -u docker.service


#系统报错日志
/var/log/messages