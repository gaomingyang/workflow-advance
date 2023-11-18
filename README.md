# workflow-advance

## Action 的job里面可以利用service属性利用docker容器部署和运行
* job runner must be linux based(ubuntu-latest)
* self-hosted runner also must be linux and docker.
* services will be run directly on the runner
* use localhost and a mapped port to connect to the service

涉及文件：
.github/workflows/service-container.yaml
requirements.txt
seed_database.py

在action的yaml中设置环境变量-数据库配置，然后python脚本运行使用对应的环境变量。

### action可以支持schedule属性来设置定时任务 scheduled triggers
* schedules are Coordinated Universal Time(UTC)
* adjust schedules for your time zone
* schedules are deactived :
    - when a public repo is forked
    - after 60 days of inactivity

涉及文件：
.github/workflows/scheduled-build.yaml

set-output被废弃了，需要调整。还没调整好。


### composite actions 合成行为
多个项目可以共用一个compositive的action的reference
直接引用action地址就可以
<!-- runs-on:xxx 改成 runs: "composite" -->

库中文件名必须为action.yml或action.yaml


composite actions 属性：
* name
* description
inputs 可选
outpus 可选
runs:
   using:"composite"
   steps:
     - run: xxx
     - uses: xxx



    