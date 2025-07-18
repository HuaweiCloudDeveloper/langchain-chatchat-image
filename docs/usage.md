# Langchain-Chatchat智能对话系统使用指南



# 一、商品链接



[Langchain-Chatchat智能对话系统](https://marketplace.huaweicloud.com/contents/1ff9aa69-614a-461d-96e8-76d544a2577c#productid=OFFI1127508967462903808)

# 二、商品说明

Langchain-Chatchat是一个开源的大模型应用平台，旨在帮助用户快速构建、部署并管理自己的大语言模型应用。无论是企业内部的智能助手，还是个人的知识问答系统，都提供了一个简便的解决方案，支持高效的文档检索和多轮对话，提升工作效率。
本商品通过鲲鹏服务器+EulerOS2.0进行安装部署


# 三、商品购买



您可以在云商店搜索 **Langchain-Chatchat智能对话系统**。

其中，地域、规格、推荐配置使用默认，购买方式根据您的需求选择按需/按月/按年，短期使用推荐按需，长期使用推荐按月/按年，确认配置后点击“立即购买”。

## 3.1 使用 RFS 模板直接部署



[![img.png](https://github.com/HuaweiCloudDeveloper/langchain-chatchat-image/blob/Langchain-Chatchat-0.3.1.3-kunpeng/docs/images/img1.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img1.png) 必填项填写后，点击 下一步 [![img.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img2.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img2.png) [![img.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img3.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img3.png) 创建直接计划后，点击 确定 [![img.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img4.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img4.png) [![img.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img5.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img5.png) 点击部署，执行计划 [![img.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img6.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img6.png) 如下图“Apply required resource success. ”即为资源创建完成 [![img.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img7.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img7.png)

# 3.2ECS 控制台配置



### 准备工作



在使用ECS控制台配置前，需要您提前配置好 **安全组规则**。

> **安全组规则的配置如下：**
>
> - 入方向规则放通端口chatchat的端口8501 7861，xinference的端口9997，必须包含这些端口才能正常访问使用
> - 入方向规则放通 CloudShell 连接实例使用的端口 `22`，以便在控制台登录调试
> - 出方向规则一键放通

### 创建ECS



前提工作准备好后，选择 ECS 控制台配置跳转到[购买ECS](https://support.huaweicloud.com/qs-ecs/ecs_01_0103.html) 页面，ECS 资源的配置如下图所示：

选择CPU架构 [![img.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img8.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img8.png) 选择服务器规格 [![img_1.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img_1.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img_1.png) 选择镜像 [![img_2.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img_2.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img_2.png) 其他参数根据实际请客进行填写，填写完成之后，点击立即购买即可 [![img_3.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img_3.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img_3.png)

> **值得注意的是：**
>
> - VPC 您可以自行创建
> - 安全组选择 [**准备工作**](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/usage.md#准备工作) 中配置的安全组；
> - 弹性公网IP选择现在购买，推荐选择“按流量计费”，带宽大小可设置为5Mbit/s；
> - 高级配置需要在高级选项支持注入自定义数据，所以登录凭证不能选择“密码”，选择创建后设置；
> - 其余默认或按规则填写即可。

# 商品使用



## Langchain-Chatchat使用

使用xinference拉取模型
启动xinference
xinference-local --host 0.0.0.0 --port 9997
拉取模型
使用网址公网ip+9997进入xinference网页，拉取自己需要的vllm、Embedding等模型。
  
使用modelscope的方式下载自己需要的模型。

修改模型配置文件启动Langchain-Chatchat
修改配置文件并初始化
cd /root/chatchat_data目录下，vim model_setting.yaml
修改支持的大模型模型和xinference的模型
  
chatchat init 初始化
启动Langchain-chatchat
cd /home/Langchain-chatchat/docker
docker compose up -d
然后使用公网ip+8501打开网页
上传文档进行知识问答
自建知识库上传文档
   
自建一个知识库上传自己的文档，然后添加文件到知识库。
进行RAG对话
    
选择大模型和知识库来进行RAG对话。




[![img.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img_4.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img_4.png) [![img_1.png](https://github.com/HuaweiCloudDeveloper/superset-image/raw/Superset-4.1.2-kunpeng/docs/images/img_5.png)](https://github.com/HuaweiCloudDeveloper/superset-image/blob/Superset-4.1.2-kunpeng/docs/images/img_5.png)

### 参考文档







[Langchain-Chatchat官网](https://github.com/chatchat-space/Langchain-Chatchat)
