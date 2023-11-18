# workflow-advance

## use service container in Github Action
job里面可以利用service属性加入docker容器
* job runner must be linux based(ubuntu-latest)
* self-hosted runner also must be linux and docker.
* services will be run directly on the runner
* use localhost and a mapped port to connect to the service

展示利用github action构建docker容器

涉及文件：
.github/workflow/service-container.yaml
requirements.txt
seed_database.py

在action的yaml中设置环境变量-数据库配置，然后python脚本运行使用对应的环境变量。

### action可以支持schedule属性来设置定时任务 scheduled triggers
* schedules are Coordinated Universal Time(UTC)
* adjust schedules for your time zone
* schedules are deactived :
    - when a public repo is forked
    - after 60 days of inactivity
