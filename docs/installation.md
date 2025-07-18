# EulerOS2.0部署langchain-chatchat

 

# **安装必要的软件**

## **1.安装docker**

如果之前安装过docker，要先删掉之后再安装依赖

sudo dnf remove docker docker-ce-cli docker-selinux docker-engine

下载repo文件

wget -O /etc/yum.repos.d/docker-ce.repo https://mirrors.huaweicloud.com/docker-ce/linux/centos/docker-ce.repo

sudo sed -i 's+download.docker.com+mirrors.huaweicloud.com/docker-ce+' /etc/yum.repos.d/docker-ce.repo

sudo sed -i 's+$releasever+9.9+' /etc/yum.repos.d/docker-ce.repo

安装新版本

sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

设置开机启动

sudo systemctl enable --now docker

配置镜像加速器

vi /etc/docker/daemon.json

\# 粘贴以下配置,保存退出,镜像地址可替换成自己在华为云申请的镜像加速器地址{

  "registry-mirrors": [ 自己申请的镜像加速地址]}

重启docker

systemctl restart docker

## **2.安装conda**

mkdir -p ~/miniconda3

wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh -O ~/miniconda3/miniconda.sh

bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3

rm -f ~/miniconda3/miniconda.sh

source ~/miniconda3/bin/activate

conda init --all

创建虚拟环境

conda create -n chat python=3.9

 

# **源码下载**

## **1.下载langchain-chatchat的源码**

创建xinference缓存路径

mkdir -p ~/xinference

 

下载源码 git clone https://github.com/chatchat-space/Langchain-Chatchat.git

 

安装必要的包

pip install langchain-chatchat -U -i https://pypi.tuna.tsinghua.edu.cn/simple

pip install "langchain-chatchat[xinference]" -U #安装推理组件xinference

 

## **2.初始化项目配置和数据目录**

export CHATCHAT_ROOT=/root/chatchat_data

chatchat init

然后在这个目录下就会有相对应的配置文件。

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps1.jpg) 

model_setting.yaml是模型配置文件，后续需要进行修改。

 

# **启动项目**

## **1.修改配置文件**

因为使用的是arm架构进行的部署，xinference的镜像有限，arm架构的镜像有局限性，所以使用xinference-local 方式启动xinference来获取模型。Langchain-chatchat使用docker compose启动。

### ***\*（1）启动模型\****

首先是使用 xinference-local --host 0.0.0.0 --port 9997启动xinference，成功启动后，使用ip+9997来打开页面。

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps2.jpg) 

 

 

 

 

 

 

 

 

 

 

 

 

打开这个页面后，就可以拉取模型来使用了，xinference里面包含的模型可以直接点击下载使用，不包含的需要先使用modelscope下载，然后再注册到xinference以便后续使用。

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps3.jpg)![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps4.jpg) 

 

 

 

 

 

 

 

 

 

词嵌入模型和大模型都按照自己所需要的配置进行下载，然后下载方式选择modelscope即可。

### ***\*（2）修改模型文件\****

修改/root/chatchat_data目录下model_settings.yaml,让拉取的模型添加到model的配置文件，可以把需要的模型都添加进行然后再到xinference拉取模型。

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps5.jpg)![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps6.jpg) 

需要修改的是两个地方，第一是支持的Agent模型把需要使用的添加进去，然后再到xinference部分添加上。

### ***\*（3）修改docker配置文件\****

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps7.jpg) 

 

 

 

 

 

 

 

 

将修改好的model的路径挂载到docker内，最好是内外路径设定为一样的。因为docker启动后会自动生成/root/chatchat_data内容。

 

# **2.启动服务**

修改好配置后，需要初始化一下，以保证修改生效。

export CHATCHAT_ROOT=/root/chatchat_data

chatchat init

之后就可以启动docker了

docker-compose up -d

启动成功后的输出为：

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps8.jpg) 

 

需要注意的是每次使用都需要先本地启动xinference启动模型后再打开docker才能使用。

然后使用ip+8501打开网页

 

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps9.jpg) 

 

 

 

 

 

 

 

 

 

 

 

部署成功后会有一些默认的模型可以使用，这个是在部署之前的一些配置文件中就设定好的，但是只能选择已经下载获取的模型进行使用。

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps10.jpg) 

 

 

 

 

 

 

 

 

 

# **使用体验**

## **1.新建知识库**

自定义名称和选择合适的向量库和词嵌入模型来创建新的知识库。

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps11.jpg) 

 

 

 

 

 

 

 

 

 

创建完成后就可以上传文档了

 

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps12.jpg) 

 

 

 

 

 

 

 

 

 

 

## **2.知识库问答**

使用RAG对话进行问答，选择合适的知识库和模型。

![img](file:///C:\Users\lenovo\AppData\Local\Temp\ksohtml7436\wps13.jpg) 
