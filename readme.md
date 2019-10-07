## 概述
一个系统监控，针对node-exporter的补充，目前添加两个监控
* 文件系统异常readonly监控：对文件系统尝试读写。解决文件系统异常后导致的readonly不会被node-exporter监测到的问题
* 僵尸进程监控：查询到defunct状态的进程后，获取进程启动时间，大于一小时的会被认为僵尸进程（逻辑有点小问题，需要调整）

监控默认启动端口10000，可以通过service配置文件修改
## 说明
```
├── ops-exporter    # centos6 service
├── ops_exporter.py # exporter
├── ops-exporter.service    # centos7 service
├── prometheus_opsexporter_service_update.yaml  # ansible playbook 更新exporter service文件
├── prometheus_opsexporter_update.yaml  # ansible playbook 更新exporter
├── prometheus_ops_exporter.yaml    # ansible playbook部署exporter
└── readme.md  
```