# InGateway501快速使用手册
本文档用于对InGateway501（以下简称IG501）联网、软件版本更新等基础配置操作进行说明，便于用户掌握IG501的基础配置和常用功能的使用方法。

  - [1. 配置IG501网络参数](#configure-ig902-network-parameters)
    - [1.1 访问IG501](#set-lan-parameters)
    - [1.2 IG501连接Internet](#set-wan-parameters)
  - [2. 更新软件版本](#update-the-software)
    - [2.1 更新IG501固件版本](#update-the-firmware-software)
    - [2.2 更新IG501 Python SDK版本](#update-the-sdk-software)
  - [3. Pyhon边缘计算](#use-python-edge-computing)
    - [3.1 安装和运行Python App](#install-and-run-python-app)
    - [3.2 更新Python App运行配置](#update-configuration-file-for-app)
    - [3.3 更新Python App版本](#update-python-app-version)
    - [3.4 开启调试模式](#enable-the-debug-mode)
  - [4. 设备远程监控平台](#device-manager)
  - [附录](#appendix)
    - [恢复出厂设置](#factory-reset)

<a id="configure-ig902-network-parameters"> </a>  

## 1. 配置IG501网络参数

<a id="set-lan-parameters"> </a>  

### 1.1 访问IG501
- 步骤1：IG501的FE 0/1口的默认ip地址为192.168.1.1，设置PC的IP地址与FE 0/1口处于同一网段。  
  - 方法一：自动获取IP地址（推荐）  

     ![](./images/2019-11-07-10-36-47.png)  

  - 方法二：使用固定IP地址   
  
    选择“使用下面的IP地址”，输入IP地址（默认为192.168.1.2~192.168.1.254中任意值）；子网掩码（默认255.255.255.0）；默认网关（默认为192.168.1.1）以及DNS服务器地址，单击<确定>。  

    ![](./images/2019-11-29-16-00-56.png)   

- 步骤2：打开浏览器，访问IG501的FE 0/1口IP地址并输入登录用户名和密码。设备出厂的用户名/密码默认为adm/123456。  

  ![](images/2020-02-14-16-10-50.png)   

- 步骤3：登录成功后，您可以看到如下图所示的网页。  

  ![](images/2020-02-13-14-21-09.png)   

- 步骤4：如需修改WEB管理界面的用户名和密码可进入“系统管理>>用户管理”页面设置新的用户名和密码。  

  ![](images/2020-01-13-13-21-42.png)   

- 步骤5：如需修改FE 0/1口的IP地址可访问“网络>>网络接口>>以太网”页面进行修改。  

  ![](images/2020-02-13-14-24-43.png)   

<a id="set-wan-parameters"> </a>  

### 1.2 IG501连接Internet
- 步骤1：将SIM卡插入卡槽（注意：插拔SIM卡操作时，必须拔掉电源，以免造成数据丢失或设备损坏）。插入SIM卡后将4G LTE天线与ANT口连接，接通IG501的电源。  

  ![](./images/2019-11-29-16-18-51.png) 

- 步骤2：进入“网络>>网络接口>>蜂窝网”页面，勾选“启用蜂窝网”并点击提交。  

  ![](images/2020-02-13-14-32-14.png)  

  待网络连接状态显示为“连接”并且显示已分配相应IP地址等状态时说明IG501已通过SIM卡联网。  

  ![](images/2020-02-13-14-41-04.png)

<a id="update-the-software"> </a>  

## 2. 更新软件版本
如需获取IG501产品最新软件版本及其功能特性信息，请联系客服。如需更新IG501的软件版本，请参考如下方法。

<a id="update-the-firmware-software"> </a>  

### 2.1 更新IG501固件版本   
  
  点击“系统管理>>固件升级”，选择相应的固件文件后点击“开始升级”。IG501升级完成后，会提示重启设备以应用新的固件。  

  ![](images/2020-01-13-18-53-19.png)  
   
<a id="update-the-sdk-software"> </a>  

### 2.2 更新IG501 Python SDK版本   
  
  进入“边缘计算>>Python边缘计算”页面，勾选“Python边缘计算引擎”并选择相应的Python SDK文件点击“升级”;弹出升级确认窗口时点击“确认”，IG501会自动完成升级操作。  

  ![](images/2020-02-10-11-49-57.png)   
   
<a id="use-python-edge-computing"> </a>  

## 3. Pyhon边缘计算

<a id="install-and-run-python-app"> </a>  

### 3.1 安装和运行Python App
在IG501中安装和运行Python App（以下简称App）请参考如下流程：  
- 步骤1：安装App   
  
  安装App前需要确保Python边缘计算引擎已启用且已安装Python SDK，如下图所示：  

  ![](images/2020-02-14-15-57-12.png)  

  进入“边缘计算>>Python边缘计算”页面，点击添加按钮并选择需要安装的App包文件，随后点击确定。  

  ![](images/2020-02-14-15-58-05.png)  

  导入成功后可以查看已导入的App，如下图所示：  

  ![](images/2020-02-14-15-58-56.png)  
   
- 步骤2：运行App   
  
  勾选启用App并点击提交。  

  ![](images/2020-02-14-15-59-25.png)   

  启用后App将在IG501中运行并且每次开机后自动运行。  

  ![](images/2020-02-14-16-01-57.png)

<a id="update-configuration-file-for-app"> </a>  

### 3.2 更新Python App运行配置
如果已安装的App支持导入配置文件修改运行方式，可参照如下流程更新App运行配置：  
- 步骤1：进入“边缘计算>>Python边缘计算”页面，点击导入配置按钮并选择需要导入的配置文件，随后点击确认。  
  
  ![](images/2020-02-14-16-03-08.png)  
   
- 步骤2：导入成功后重启App，App重启完成后将按照导入后的配置文件运行。  

  ![](images/2020-02-14-16-03-42.png)

<a id="update-python-app-version"> </a>  

### 3.3 更新Python App版本
通常如需更新Python App版本时只需要在“边缘计算>>Python边缘计算”页面导入新版本的App即可。  

![](images/2020-03-19-16-01-32.png)  

更新完成后如下图所示：  

![](images/2020-03-19-16-03-04.png)

<a id="enable-the-debug-mode"> </a>  

### 3.4 开启调试模式
如需在IG501上运行并调试Python代码，需要启用IG501的调试模式。在“边缘计算>>Python边缘计算”页面中，勾选“启用调试模式”，启用后可通过VS Code对IG501进行开发。如何使用VS Code进行Python开发请参考[MobiusPi Python开发快速入门](http://sdk.ig.inhand.com.cn/zh_CN/latest/MobiusPi-Python-QuickStart-CN.html)。  

![](images/2020-02-14-16-04-18.png)  

启用调试模式后，IG501启动一个SSH Server，监听LAN网络(默认IP地址192.168.1.1)的222端口。SSH Server的用户名和密码将被显示到上述网页中。为了提高安全性，每次开启调试模式或重启设备，都会重新随机生成新的密码。

<a id="device-manager"> </a>  

## 4. 设备远程监控平台
映翰通开发的设备远程监控平台支持监视IG501状态、远程维护设备、远程批量下发IG501配置和IG501批量升级等功能，帮助用户便捷、高效的管理IG501和现场设备。为了使设备远程监控平台能够远程管理IG501和现场设备，需要将IG501连接到云平台上，连接方法如下：  
进入“系统管理>>设备远程监控平台”页面，勾选启用设备远程监控平台并配置相应的服务器地址以及注册账户，配置完成后点击提交即可。  
- 服务器地址：即设备远程监控平台地址。映翰通开发的远程监控平台地址如下：  
  - 国内版Device Manager：`c.inhandcloud.com`  
  - 海外版Device Manager：`iot.inhandnetworks.com`  
  - 国内版InConnect：`ics.inhandiot.com`  
  - 海外版InConnect：`ics.inhandnetworks.com`  
- 注册账户：即IG501关联的设备远程监控平台账号（如果还未注册账户需要先注册一个账号）  
- 高级设置：包含心跳间隔等配置，一般使用默认配置即可  

![](images/2020-03-19-16-06-28.png)   

IG501与设备远程监控平台连接成功后状态描述为连接成功。  

![](images/2020-03-19-16-07-07.png)  

<a id="appendix"> </a>  

## 附录  

<a id="factory-reset"> </a>  

### 恢复出厂设置
IG501恢复出厂设置的方式有两种：硬件恢复出厂设置和软件恢复出厂设置。
- 硬件恢复出厂设置  
  - 步骤1：在设备面板上找到 RESET 复位键；  
  - 步骤2：设备加电后 10 秒内长按 RESET 键不松开；  
  - 步骤3：当 WARN 灯变黄后，松开 RESET 键；  
  - 步骤4：当 WARN 灯变黄后，松开 RESET 键；  
  - 步骤5：当看到 WARN 灯闪烁时松开 RESET 键，稍后 WARN 灯熄灭，表明恢复出厂设置成功。 

- 软件恢复出厂设置  
  
  进入“系统管理>>配置管理”页面，点击重置按钮并选择确定。IG501将自行完成恢复出厂设置操作。  

  ![](images/2020-02-14-16-05-18.png)