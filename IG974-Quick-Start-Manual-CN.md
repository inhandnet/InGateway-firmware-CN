# InGateway974快速使用手册
本文档用于对InGateway974（以下简称IG974）联网、软件版本更新等基础配置操作进行说明，便于用户掌握IG974的基础配置和常用功能的使用方法。

  - [1. 配置IG974网络参数](#configure-ig974-network-parameters)
    - [1.1 访问IG974](#set-lan-parameters)
    - [1.2 IG974连接Internet](#set-wan-parameters)
  - [2. 更新软件版本](#update-the-software)
    - [2.1 更新IG974固件版本](#update-the-firmware-software)
    - [2.2 更新IG974 Python SDK版本](#update-the-sdk-software)
    - [2.3 更新IG974 Docker SDK版本](#update-the-docker-software)
  - [3. Pyhon边缘计算](#use-python-edge-computing)
    - [3.1 安装和运行Python App](#install-and-run-python-app)
    - [3.2 更新Python App运行配置](#update-configuration-file-for-app)
    - [3.3 更新Python App版本](#update-python-app-version)
    - [3.4 开启调试模式](#enable-the-debug-mode)
  - [4. 设备远程监控平台](#device-manager)
  - [5. IO模块](#io-module)
  - [附录](#appendix)
    - [恢复出厂设置](#factory-reset)


<a id="configure-ig974-network-parameters"> </a>  

## 1. 配置IG974网络参数

<a id="set-lan-parameters"> </a>  

### 1.1 访问IG974
- 步骤1：IG974 WAN口的默认为DHCP；LANX口的默认ip地址为192.168.2.1。本文档以通过LANX口访问IG974为例，设置PC的IP地址与LANX口处于同一网段。  
  - 方法一：自动获取IP地址（推荐）  

     ![](./images/2019-11-07-10-36-47.png)  
  
  - 方法二：使用固定IP地址  
  
    选择“使用下面的IP地址”，输入IP地址（默认为192.168.2.2~192.168.2.254中任意值）；子网掩码（默认255.255.255.0）；默认网关（默认为192.168.2.1）以及DNS服务器地址，单击确定。  

    ![](images/2020-01-13-10-16-08.png)   

- 步骤2：打开浏览器，访问IG974的GE 0/2口IP地址并输入登录用户名和密码。设备出厂的用户名/密码默认为adm/123456。  

  ![](images/2021-09-07-14-51-44.png)  

- 步骤3：登录成功后，您可以看到如下图所示的网页。  

  ![](images/2021-09-07-14-52-30.png)  

- 步骤4：如需修改WEB管理界面的用户名和密码可进入IG974的“系统管理>>用户管理”页面设置新的用户名和密码。  

  ![](images/2021-09-07-14-53-02.png)  

- 步骤5：如需修改LANX口的IP地址可访问IG974的“网络>>网络接口>>LAN”页面进行修改。  

  ![](images/2021-09-07-14-54-14.png)  

<a id="set-wan-parameters"> </a>  

### 1.2 IG974连接Internet
  - 方法一：使用SIM卡拨号连接Internet（要改）
    - 步骤1：将SIM卡插入卡槽（注意：插拔SIM卡操作时，必须拔掉电源，以免造成数据丢失或设备损坏）。插入SIM卡后将5G天线与ANTX口连接，接通IG974的电源。  

      ![](images/2021-09-07-15-51-29.png)  

    - 步骤2：进入IG974的“网络>>网络接口>>蜂窝网”页面，勾选“启用蜂窝网”并点击提交。  

      ![](images/2021-09-07-15-31-11.png)  

      待网络连接状态显示为“已连接”并且显示已分配相应IP地址等状态时说明IG974已通过SIM卡联网。  

      ![](images/2021-09-07-15-59-36.png)  

  - 方法二：使用以太网连接Internet
    - 步骤1：使用以太网线连接IG974的GE 0/1和GE 0/2口，如下图：  

      ![](images/2021-09-07-17-12-38.png)  

    - 步骤2：进入IG974的“网络>>网络接口>>WAN”页面，配置WAN口的IP地址（网络类型为静态IP地址时需要根据现场网络情况配置IP、子网掩码等信息）并点击提交。  

      ![](images/2021-09-07-17-21-16.png)  

      ![](images/2021-09-07-17-20-32.png)  

    - 步骤3：进入IG974的“系统管理>>工具”页面，使用Ping命令检测IG974是否成功接入Internet。  

      ![](images/2021-09-07-17-35-09.png)

<a id="update-the-software"> </a>  

## 2. 更新软件版本
如需获取IG974产品最新软件版本及其功能特性信息，请访问[资源中心](https://www.inhand.com.cn/downlist/edge-computing-gateway/)。如需更新IG974的软件版本，请参考如下方法。

<a id="update-the-firmware-software"> </a>  

### 2.1 更新IG974固件版本  
  
  点击“系统管理>>固件升级”，选择相应的固件文件后点击“开始升级”并“确认”。IG974升级完成后，会提示重启设备以应用新的固件。  

  ![](images/2021-09-07-17-54-54.png) 
   
<a id="update-the-sdk-software"> </a>  

### 2.2 更新IG974 Python SDK版本  
  
  进入“边缘计算>>Python边缘计算”页面，点击“升级”并选择相应的Python SDK文件;弹出升级确认窗口时点击“确认”，IG974会自动完成升级操作。  

  ![](images/2021-09-07-17-42-29.png)  
   
<a id="update-the-docker-software"> </a>  

### 2.3 更新IG974 Docker SDK版本  
  
  进入“边缘计算>>Docker管理”页面，点击升级并选择相应的Docker SDK文件。  

  ![](images/2021-09-07-17-56-19.png)  
   
  安装成功后，勾选“启用Portainer管理器”并点击“提交”。  

  ![](images/2021-09-07-17-59-52.png)  
   
  启用Portainer管理器后，可以点击“进入Portainer管理页面”访问管理页面。  

  ![](images/2021-09-07-18-03-10.png)  
  
  输入上图中设置的账号密码即可登录管理页面。  

  ![](images/2020-02-11-09-15-25.png)

  登录成功后选择“Local”并点击“Connect”。  

  ![](images/2021-09-07-18-04-15.png)

<a id="use-python-edge-computing"> </a>  

## 3. Pyhon边缘计算

<a id="install-and-run-python-app"> </a>  

### 3.1 安装和运行Python App
在IG974中安装和运行Python App（以下简称App）请参考如下流程：  
- 步骤1：安装App  
  
  安装App前需要确保已安装Python SDK且Python边缘计算引擎已启用，如下图所示：  

  ![](images/2021-09-08-13-47-33.png)  

  进入“边缘计算>>Python边缘计算”页面，点击添加按钮并选择需要安装的App包文件，随后点击确定。  

  ![](images/2021-09-08-13-51-47.png)  

  导入成功后可以查看已导入的App，如下图所示：  

  ![](images/2021-09-08-13-53-54.png)  

- 步骤2：运行App  
  
  勾选启用App并点击提交。  

  ![](images/2021-09-08-13-54-29.png)  

  启用后App将在IG974中运行并且每次开机后自动运行。  

  ![](images/2021-09-08-14-00-44.png)

<a id="update-configuration-file-for-app"> </a>  

### 3.2 更新Python App运行配置
如果已安装的App支持导入配置文件修改运行方式，可参照如下流程更新App运行配置：
- 步骤1：进入“边缘计算>>Python边缘计算”页面，点击导入配置按钮并选择需要导入的配置文件，随后点击确认。  

  ![](images/2021-09-08-14-46-54.png)  
   
- 步骤2：导入成功后重启App，App重启完成后将按照导入后的配置文件运行。  

  ![](images/2021-09-08-14-47-56.png)

<a id="update-python-app-version"> </a>  

### 3.3 更新Python App版本
通常如需更新Python App版本时只需要在“边缘计算>>Python边缘计算”页面导入新版本的App即可。  

![](images/2021-09-08-14-50-05.png)  

更新完成后如下图所示：  

![](images/2021-09-08-14-51-39.png)

<a id="enable-the-debug-mode"> </a>  

### 3.4 开启调试模式
如需在IG974上运行并调试Python代码，需要启用IG974的调试模式。在“边缘计算>>Python边缘计算”页面中，勾选“启用调试模式”，启用后可通过VS Code对IG974进行开发。如何使用VS Code对IG974进行Python开发请参考[MobiusPi Python开发快速入门](http://sdk.ig.inhand.com.cn/zh_CN/latest/MobiusPi-Python-QuickStart-CN.html)。  

![](images/2021-09-08-14-52-05.png)  

启用调试模式后，IG974启动一个SSH Server，监听LAN网络(默认IP地址192.168.2.1)的222端口。SSH Server的用户名和密码将被显示到上述网页中。为了提高安全性，每次开启调试模式或重启设备，都会重新随机生成新的密码。

<a id="device-manager"> </a>  

## 4. 设备远程监控平台
映翰通开发的设备云平台支持监视IG974状态、远程维护设备、远程批量下发IG974配置和IG974批量升级等功能，帮助用户便捷、高效的管理IG974和现场设备。为了使设备云平台能够远程管理IG974和现场设备，需要将IG974连接到云平台上，连接方法如下：  
进入“系统管理>>设备云平台”页面，勾选启用设备云平台并配置相应的服务器地址以及注册账户，配置完成后点击提交即可。其中**InHand Connect Service**平台主要为用户提供远程维护通道，**InHand Device Manager**平台主要为用户提供网关管理服务（如批量远程升级等）。  
- 服务器地址：即设备云平台地址 
- 注册账户：即IG974关联的设备云平台账号（如果还未注册账户需要先注册一个账号）  
- 高级设置：包含心跳间隔等配置，一般使用默认配置即可

![](images/2021-01-19-18-09-35.png)  

IG974与设备云平台连接成功后状态描述为连接成功。  

![](images/2021-01-19-18-10-10.png)  

<a id="appendix"> </a>  

## 附录

<a id="factory-reset"> </a>  

### 恢复出厂设置
IG974恢复出厂设置的方式有两种：硬件恢复出厂设置和软件恢复出厂设置  
- 硬件恢复出厂设置  
  - 步骤1：设备上电后10内长按RESET键；  
  - 步骤2：ERR灯常亮时，松开RESET键；  
  - 步骤3：ERR灯熄灭后，再次按住RESET键，ERR灯闪烁时松开RESET键；等待ERR灯熄灭，表明恢复出厂设置成功。  
   
- 软件恢复出厂设置  
  
  进入“系统管理>>配置管理”页面，点击重置按钮并选择确定。IG974将自行完成恢复出厂设置操作。  

  ![](images/2021-09-08-15-04-25.png)