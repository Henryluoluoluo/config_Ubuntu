# <center> docker常用命令

**将当前用户添加到docker用户组**
*避免每次使用docker命令都加上sudo权限*
`sudo usermod -aG docker $USER`

**镜像(images)**
1. `docker pull ubuntu:20.04`:拉取一个镜像
   > 镜像由 *名称:版本* 组成
2. `docker images`:列出本地所有镜像
3. `docker rmi ubuntu:20.04`:删除镜像20.04
4. `docker [container] commit CONTAINER IMAGE_NAME:TAG`:创建某个container的镜像
5. `docker save -o ubuntu_20_04.tar ubuntu:20.04`:保存镜像为压缩包
6. `docker load -i ubuntu_20_04.tar`:将镜像加载出来

**容器(container)**
1. `docker create -it ubuntu:20.04`:利用镜像ubuntu:20.04创建一个容器。
2. `docker rm CONTAINER`:删除一个容器
3. `docker container prune`:删除所有已停止的容器
4. `docker ps -a`:查看本地的所有容器
5. `docker start CONTAINER`:启动容器
6. `docker stop CONTAINER`:停止容器
7. `docker restart CONTAINER`:重启容器
8. `docker run -itd ubuntu:20.04`:创建并启动一个容器
9. `docker attach CONTAINER`:进入容器
   * 先按Ctrl-p，再按Ctrl-q挂起容器
10. `docker exec CONTAINER COMMAND`:容器中执行命令
11. `docker export -o xxx.tar CONTAINER`:将容器CONTAINER导出到本地文件xxx.tar中
12. `docker import xxx.tar image_name:tag`:将本地文件xxx.tar导入成镜像，并将镜像命名为image_name:tag
13. `docker top CONTAINER`:查看某个容器内的所有进程
14. `docker stats`:查看所有容器的统计信息，包括CPU、内存、存储、网络等信息
15. `docker cp xxx CONTAINER:xxx` 或 `docker cp CONTAINER:xxx xxx`:在本地和容器间复制文件
16. `docker rename CONTAINER1 CONTAINER2`:重命名容器
17. `docker update CONTAINER --memory 500MB`:修改容器限制
18. `docker run -p 20000:22 --name my_docker_server -itd docker_lesson:1.0 `# 创建并运行docker_lesson:1.0镜像