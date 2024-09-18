好的，下面是 Nexus 安装的详细步骤，包括环境准备、下载、解压、配置和启动。

## 1、环境准备

1. 安装 Java

   ：

   - Nexus 需要 Java 运行环境（JRE）。确保你的系统已经安装了 JDK 8 或更高版本。

   - 你可以通过以下命令检查 Java 版本：

     ```bash
     java -version
     ```

   - 如果没有安装 Java，可以从 Oracle 或 OpenJDK 下载并安装。

## 2、下载 Nexus

1. 访问 Sonatype 官网：

   - 打开浏览器，访问 Sonatype 官网下载地址[3.70.x Downloads (for OrientDB) (sonatype.com)](https://help.sonatype.com/en/orientdb-downloads.html)
   - 选择下载对应系统的 Nexus。

   ![image-20240918184937043](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20240918184937043.png)

## 3、安装Nexus

### 3.1 linux安装

#### 解压文件

：

- 将下载的压缩包解压到你选择的目录。例如：

  ```bash
  tar -zxvf nexus-3.x.x-unix.tar.gz -C /opt
  ```

- 解压后，你会看到两个主要目录：`nexus-3.x.x` 和 `sonatype-work`。

#### 配置 Nexus

1. **配置端口和上下文路径**：

   - 打开 `nexus-3.x.x/etc/nexus-default.properties` 文件。

   - 你可以修改以下属性来配置 Nexus 的端口和上下文路径：

     ```properties
     application-port=8081
     nexus-context-path=/nexus
     ```

2. **配置 JVM 参数**：

   - 打开 `nexus-3.x.x/bin/nexus.vmoptions` 文件。

   - 根据你的系统资源，调整 JVM 的最大堆和最小堆大小。例如：

     ```properties
     -Xms1200M
     -Xmx1200M
     -XX:MaxDirectMemorySize=2G
     ```

#### 启动 Nexus

1. **启动 Nexus**：

   - 进入 

     ```
     nexus-3.x.x/bin
     ```

      目录，运行以下命令启动 Nexus：

     ```bash
     ./nexus run
     ```

   - 或者你可以将 Nexus 安装为服务：

     ```bash
     ./nexus install
     ./nexus start
     ```

2. **访问 Nexus**：

   - 打开浏览器，输入 `http://localhost:8081`（如果你没有修改端口）。
   - 默认用户名为 `admin`，密码在 `sonatype-work/nexus3/admin.password` 文件中。

## 4、登录和初始配置

1. **首次登录**：
   - 使用默认用户名 `admin` 和密码登录。
   - 系统会提示你更改默认密码，按照提示操作即可。
2. **配置匿名访问**：
   - 登录后，导航到 `Security` -> `Anonymous`。
   - 配置匿名用户的访问权限，建议关闭匿名访问以提高安全性。

## 5、常见问题

#### **Nexus 启动失败**：

- 检查 Java 版本是否正确。
- 确认端口没有被其他应用占用。
- 查看 `sonatype-work/nexus3/log` 目录下的日志文件，获取详细错误信息。

#### 无法访问 Nexus**：

- 确认防火墙设置允许访问配置的端口。
- 检查浏览器是否输入了正确的 URL 和端口。

​                 

​              