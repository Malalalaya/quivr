#                      中文版一Quivr如何在本地部署？（Windows）

**项目已经开源**

Github链接：https://github.com/StanGirard/quivr

关于如何部署，其实官方文档经有完整介绍，如下：

https://github.com/StanGirard/quivr/blob/main/README.md 

------

[TOC]

------

## **一、先决条件，安装软件**

### 1、Docker与Docker Compose

```python
Docker网址：https://www.docker.com/
```

- **Docker**
- **Docker Compose**（集成在Dockers，不需要单独安装）

谷歌搜索Docker的官方网址，https://www.docker.com/，打开。

![2](D:\GitLoadWareHouse\quivr\pictures\2.png)

现在只需要点击右上角**Get Started**（开始使用），即可下载，大概**600MB**左右，迅雷或者IDM下载会比较快。

![3](D:\GitLoadWareHouse\quivr\pictures\3.png)  

不过，这里你可以现在在**网页端登录**，如此应用程序安装后会自动登录。点击**Sign In**进入登录界面，可以选择**谷歌账号**，也可以是**Github**。我是以Google登录。

![4](D:\GitLoadWareHouse\quivr\pictures\4.png)

 选择账号，如果原先在浏览器中没有登录，直接输入邮箱和验证码。我这里曾经在浏览器谷歌账号中登录过。

![5](D:\GitLoadWareHouse\quivr\pictures\5.png)

 登录好了，进入了**Docker网页端程序**。

![6](D:\GitLoadWareHouse\quivr\pictures\6.png)

之后，应用程序安装完毕就是登录，非常简单。**Sign in（登录按钮）**在右上角，由于在网页端登录过了，点击后会自动登录。

![7](D:\GitLoadWareHouse\quivr\pictures\7.png)

跳转网页，因为之**前已经登录**，会主动登陆成功。

![8](D:\GitLoadWareHouse\quivr\pictures\8.png)

 **Docker**自动登陆成功，如下。

![9](D:\GitLoadWareHouse\quivr\pictures\9.png)

>  **注：另外，之前说过，Docker Compose（集成在Dockers，不需要单独安装）**

### 2、Supabase

```python
Supabase网址：https://supabase.com/
```

- **Creating a new Supabase project（创建账户）**
- **Supabase Project API key（API密钥）**
- **Supabase Project URL（URL网址）**

打开网址后，点击**Start your Project**【开始你的项目】。

![11](D:\GitLoadWareHouse\quivr\pictures\11.png)

 使用右上角的**Sign in**或者点击开始你的项目，弹出登录界面。这里以**Github**账号登录。

![12](D:\GitLoadWareHouse\quivr\pictures\12.png)

进入**Supabase**后，点击**【新建项目】**，输入名称，我设置为Quivr，密码，然后保存。

**（图片好像丢了……）**



此时会出现后面非常重要的**Supabase**的**API**、**URL**、**JWT**。

![13](D:\GitLoadWareHouse\quivr\pictures\13.png)

当然， 如果，你不小心关闭了**Supabase的网页**，找不到API、URL，点击你创建的项目（我这里是Quivr），**进入**。

![14](D:\GitLoadWareHouse\quivr\pictures\14.png)

 点击**【设置】**中的**API**，你看，现在就又可以瞧见了。

![15](D:\GitLoadWareHouse\quivr\pictures\15.png)

### 3、Git

```python
Git网址：https://git-scm.com/
```

谷歌搜索Git，打开官网https://git-scm.com/，安装**最新版本**。

![16](D:\GitLoadWareHouse\quivr\pictures\16.png)

下载好，安装步骤默认。或者自己修改路径。

### 4、Python

```python
Python网址：https://www.python.org/downloads/
```

谷歌搜索**Python**，打开官网，安装**最新版本**。

![17](D:\GitLoadWareHouse\quivr\pictures\17.png)

下载好，安装步骤默认。或者自己修改路径。

### 5、编辑器（自己选择）

可以下载**编辑器**，后面需要修改克隆Quivr中文件的代码，例如IntelliJ 、Sublime Text ……

------



## **二、程序脚本** 

#### **第一步**：克隆存储库：

```python
git clone https://github.com/StanGirard/Quivr.git
```

在文件夹中**新建一个文件**，我建的是**Quivr**，鼠标右键，选择**Open Git Bash Here**（安装的Git应用程序）。

![18](D:\GitLoadWareHouse\quivr\pictures\18.png)

打开**Github**中**Quivr**的开源地址，对**Code**（编码）中的地址进行复制。

![19](D:\GitLoadWareHouse\quivr\pictures\19.png)

输入**git clone +URL**粘贴到**Git界面**，这里**粘贴**的时候需要用**鼠标右键复制**，快捷键并不是默认的ctrl+C,然后点击回车键。

![20](D:\GitLoadWareHouse\quivr\pictures\20.png)

等一会儿就基本下载完了，应该是需要一会儿。

![21](D:\GitLoadWareHouse\quivr\pictures\21.png)

**注：这里有可能会出现一些错误**，你可以百度搜，例如

```
错误： git SSL certificate problem: unable to get local issuer certificate 
```

这个问题是由于没有配置信任的服务器HTTPS验证。默认，[URL](https://so.csdn.net/so/search?q=cURL&spm=1001.2101.3001.7020)被设为不信任任何CAs，就是说，它不信任任何服务器验证。

只需要执行下面命令就可以解决：

```python
Git config --global http.sslVerify false
```

#### **第二步**：（1）程序脚本自动执行：

```python
 brew install gum # Windows (via Scoop) scoop install charm-gum
 brew install postgresql # Windows (via Scoop) scoop install postgresql
```

程序脚本自动执行后续操作，可以使用 **install_helper.sh** 脚本来设置 **env 文件**并**执行迁移**。当然，你也可以直接在如下**Git界面**输入如上代码（记得需要在Quivr目录输入，可同时复制，也可一个一个复制）。

![22](D:\GitLoadWareHouse\quivr\pictures\22.png)

- 因为我下了编辑器**IntelliJ** ，所以后续操作就在**IntelliJ** 进行

在**IntelliJ IDEA**中打开刚才克隆好的**quiver**文件夹，找到**install_helper.sh** 脚本，点击运行。

![23](D:\GitLoadWareHouse\quivr\pictures\23.png)

运行完**install_helper.sh**脚本之后输入以下命令：

```python
brew install gum # Windows (via Scoop) scoop install charm-gum
brew install postgresql # Windows (via Scoop) scoop install postgresql
```

![24](D:\GitLoadWareHouse\quivr\pictures\24.png)

#### **第二步**：（2）复制文件.XXXXX_env

```python
cp .backend_env.example backend/.env
cp .frontend_env.example frontend/.env
```

同样，在这里输入以上命令，运行：

![25](D:\GitLoadWareHouse\quivr\pictures\25.png)

#### **第三步**：更新 和 文件backend/.env 与frontend/.env

```python
更改变量   backend/.env
更改变量   frontend/.env
```

##### 1、更改变量backend/.env

找到**backed**文件夹下的**.env**，打开。

![26](D:\GitLoadWareHouse\quivr\pictures\26.png)

**（一）**

```python
1  SUPABASE_URL=           # Supabase中的Project URL,点击右边Copy复制  
2  SUPABASE_SERVICE_KEY=   # Supabase中的Project API keys，点击右边Copy复制 
```

![27](D:\GitLoadWareHouse\quivr\pictures\27.png)

**（二）**

```python
3  OPENAI_API_KEY=         # ChatGPT的API key，需要自己先注册3.5账号
```

![28](D:\GitLoadWareHouse\quivr\pictures\28.png)

------

**插播：如何获取ChatGPT的API？**

**插播：如何获取ChatGPT的API？**

**插播：如何获取ChatGPT的API？**

```python
Open Ai网址：https://openai.com/chatgpt
```

打开网址https://openai.com/chatgpt，点击右上角**Log in**（登录）。

![29](D:\GitLoadWareHouse\quivr\pictures\29.png)

这里选择**API**，点击进入。

![30](D:\GitLoadWareHouse\quivr\pictures\30.png)

打开**API keys**，选择【**创建新的密钥**】，输入一个名称，点击创建就可以。

![31](D:\GitLoadWareHouse\quivr\pictures\31.png)

 复制**API密钥**就好。

![32](D:\GitLoadWareHouse\quivr\pictures\32.png)

------

**（三）**

```python
4  JWT_SECRET_KEY=         # Supabase中的JWT Settings,点击右边Copy复制
```

![33](D:\GitLoadWareHouse\quivr\pictures\33.png)

#####     2、更改变量frontend/ .env

找到**frontend**文件夹下的**.env**，打开。

![34](D:\GitLoadWareHouse\quivr\pictures\34.png)

 **打开Supabase**

```python
Supabase的API位置：   https://supabase.com/dashboard/project/nednxikufheqmljgsvmd/settings/api
```

打开，https://supabase.com/dashboard/project/nednxikufheqmljgsvmd/settings/api，这里的步骤跟**backend/.env**一样，不再赘述。

![35](D:\GitLoadWareHouse\quivr\pictures\35.png)

如此，就设置好了 。

#### **第四步**：通过Web在Supabase数据库上运行脚本

```python
Scripts文件夹地址https://github.com/StanGirard/quivr/tree/main/scripts #这里寻找的就是数据库，以table.sql格式保持
```

关于脚本内容可以打开**Scripts**：https://github.com/StanGirard/quivr/tree/main/scripts

文件夹中找到**table.sql**，打开。

![36](D:\GitLoadWareHouse\quivr\pictures\36.png)

 打开**Table**，选择右上角的**Coep raw file**，进行复制。

![37](D:\GitLoadWareHouse\quivr\pictures\37.png)

然后，打**开Supabase**，进行粘贴。

```python
地址；https://supabase.com/dashboard/project/nednxikufheqmljgsvmd/editor
```

![38](D:\GitLoadWareHouse\quivr\pictures\38.png)

找到右下角**Run**，运行table.Sql（表）。

![39](D:\GitLoadWareHouse\quivr\pictures\39.png)

 运行完毕，你就可以看到数据库已经弄好了。

![40](D:\GitLoadWareHouse\quivr\pictures\40.png)

#### **第五步**：启动应用程序

```python
docker compose up --build    #运行的时候不管是什么程序一定需要在Quivr目录之下
```

打开**Git**，输入**docker compose up --build**，回车键。

可能会**运行时间比较长**（可选择科学上网）。如果，**运行中间出现错误**，**重向**在**Git**输入指令运行，程序会接着下载（一般是由于**下载响应时间过长**造成）。

![41](D:\GitLoadWareHouse\quivr\pictures\41.png)

 运行完成

（**忘记截图了……**）

------



## **三、登陆失败与谷歌授权**

#### 1、报错原因

```python
本地地址：      http://localhost:3000
```

一切配置好了，打开一个浏览器。点击本地地址：http://localhost:3000打开。本地部署的**Quivr**的界面打开了，试着用**谷歌邮箱**登录。

![42](D:\GitLoadWareHouse\quivr\pictures\42.png)

**报错了？**如何做呢？可能是**Supabase**中没有进行**谷歌**的**云端授权**。

所以，打开 https://supabase.com/dashboard/project/nednxikufheqmljgsvmd/auth/providers

```python
Auth Providers地址：https://supabase.com/dashboard/project/nednxikufheqmljgsvmd/auth/providers
```

你也可以在**Supabase**中找到**自己创建的项目**，然后打开**授权界面**。

![43](D:\GitLoadWareHouse\quivr\pictures\43.png)

 往下划，找到谷歌，这里需要设置谷歌的**客户端ID**与**客户端密钥**。

![44](D:\GitLoadWareHouse\quivr\pictures\44.png)

#### 2、创建Web客户端

```python
谷歌云端链接：https://console.cloud.google.com/apis/credentials?authuser=1&project=quivr-406405
```

如何做呢？

打开，链接

https://console.cloud.google.com/apis/credentials?authuser=1&project=quivr-406405

你会看到**谷歌云端**中的**凭证**，然后点击**【建立凭证】**，这里要选择**OAuth客户端ID**。

![45](D:\GitLoadWareHouse\quivr\pictures\45.png)

 应用程序选择**网页应用程序**。

![46](D:\GitLoadWareHouse\quivr\pictures\46.png)

-  **URI1*：已授权的JavaScript**

 **URI1*：**输入你的本地地址：http://localhost:3000

![47](D:\GitLoadWareHouse\quivr\pictures\47.png)

-  **URI1：已授权的重新导向*：**

 这里输入在**Supabase授权中谷歌**哪里会提供一个**重向导向URI**

![48](D:\GitLoadWareHouse\quivr\pictures\48.png)

 然后点击建立就可。

![49](D:\GitLoadWareHouse\quivr\pictures\49.png)

 此时，你会发现多了一个客户端，打击打开，就会出现你需要的谷歌**客户端ID**与**客户端密钥**。

![50](D:\GitLoadWareHouse\quivr\pictures\50.png)

 再次返回**Supabase**谷歌**授权中**填入相关信息，保存，等大概三四分钟。

![51](D:\GitLoadWareHouse\quivr\pictures\51.png)

 再次在浏览器打开**本地地址**：http://localhost:3000。

![52](D:\GitLoadWareHouse\quivr\pictures\52.png)

发现出现账号登录界面，选择自己账号，如果没有在浏览器登录，可以输入邮箱和密码。

![53](D:\GitLoadWareHouse\quivr\pictures\53.png)

  如此，就**登陆成功**。

![54](D:\GitLoadWareHouse\quivr\pictures\54.png)

------

好了，就到这儿了

过程中，有些时候可能需要科学上网

另外，……欢迎补充！