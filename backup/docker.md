# Docker常用命令

### 使用镜像

**镜像拉取**

```powershell
docker pull ubuntu:18.04
```

**列出镜像**

```powershell
docker image ls
```
列表包含了`仓库名`、`标签`、`镜像ID`，`创建时间`和`所占用空间`。**镜像ID**是镜像的唯一标识，一个镜像可以对应多个标签。`docker image ls`只会显示顶层镜像，增加参数`-a`可以显示包括中间层镜像的所有镜像。

**删除镜像**

```powershell
docker image rm <镜像>
```

其中，`<镜像>`可以是`镜像短ID`、`镜像长id`和`镜像名`。

___

### 操作镜像

**创建并运行容器**

```powershell
docker run -it --rm --name ublinux ubuntu:18.04 bash
```

- `-it`：包含两个参数，`-i`：交互式操作；`-t`终端；表示打开交互式终端。
- `--rm`：容器退出后自动删除容器。
- `--name`：给容器命名。
- `ubuntu:18.04`：这是指用`ubuntu:18.04`镜像为基础来启动容器。
- `bash`：放在镜像名后的是 **命令**，表示使用交互式shell。

利用`docker run`创建容器时，Docker 在后台运行的标准操作包括：

- 检查本地是否存在指定的镜像，不存在就从 [registry](https://yeasy.gitbook.io/docker_practice/repository) 下载
- 利用镜像创建并启动一个容器
- 分配一个文件系统，并在只读的镜像层外面挂载一层可读写层
- 从宿主主机配置的网桥接口中桥接一个虚拟接口到容器中去
- 从地址池配置一个 ip 地址给容器
- 执行用户指定的应用程序
- 执行完毕后容器被终止

**启动和终止容器**
```powershell
docker container start
docker container stop
```

___

### .vhdx磁盘清理

```powershell
# 关闭 WSL2 中的 linux distributions
wsl --shutdown
# 运行管理计算机的驱动器的 DiskPart 命令
diskpart
# 选择虚拟磁盘文件
select vdisk file="F:\Docker_Desktop\WSL\DockerDesktopWSL\disk\docker_data.vhdx"
# 只读 附加磁盘镜像文件
attach vdisk readonly
# 压缩 vhdx 磁盘镜像文件
compact vdisk
# 分离 vhdx 磁盘镜像文件
detach vdisk
#退出
exit
```





# Docker国内加速镜像地址

[Docker最新镜像地址](https://xuanyuan.me/blog/archives/1154?from=tencent#_registry_mirror)



# Docker容器内GPU配置

[在 Docker 容器中使用 Nvidia 显卡的方法](https://torchtree.com/zh/posts/docker/how-to-use-nvidia-gpu-in-docker/)