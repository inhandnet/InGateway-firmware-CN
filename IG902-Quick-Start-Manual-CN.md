# InGateway902快速使用手册
本文档用于对InGateway902（以下简称IG902）联网、软件版本更新等基础配置操作进行说明，便于用户掌握IG902的基础配置和常用功能的使用方法。

  - [1. 配置IG902网络参数](#configure-ig902-network-parameters)
    - [1.1 访问IG902](#set-lan-parameters)
    - [1.2 IG902连接Internet](#set-wan-parameters)
  - [2. 更新软件版本](#update-the-software)
    - [2.1 更新IG902固件版本](#update-the-firmware-software)
    - [2.2 更新IG902 Python SDK版本](#update-the-sdk-software)
    - [2.3 更新IG902 Docker SDK版本](#update-the-docker-software)
  - [3. Pyhon边缘计算](#use-python-edge-computing)
    - [3.1 安装和运行Python App](#install-and-run-python-app)
    - [3.2 更新Python App运行配置](#update-configuration-file-for-app)
    - [3.3 更新Python App版本](#update-python-app-version)
    - [3.4 开启调试模式](#enable-the-debug-mode)
  - [4. 设备远程监控平台](#device-manager)
  - [5. IO模块](#io-module)
  - [附录](#appendix)
    - [恢复出厂设置](#factory-reset)


<a id="configure-ig902-network-parameters"> </a>  

## 1. 配置IG902网络参数

<a id="set-lan-parameters"> </a>  

### 1.1 访问IG902
- 步骤1：IG902的GE 0/1口的默认ip地址为192.168.1.1；GE 0/2口的默认ip地址为192.168.2.1。本文档以通过GE 0/2口访问IG902为例，设置PC的IP地址与GE 0/2口处于同一网段。  
  - 方法一：自动获取IP地址（推荐）  

     ![](./images/2019-11-07-10-36-47.png)  
  
  - 方法二：使用固定IP地址  
  
    选择“使用下面的IP地址”，输入IP地址（默认为192.168.2.2~192.168.2.254中任意值）；子网掩码（默认255.255.255.0）；默认网关（默认为192.168.2.1）以及DNS服务器地址，单击确定。  

    ![](images/2020-01-13-10-16-08.png)   

- 步骤2：打开浏览器，访问IG902的GE 0/2口IP地址并输入登录用户名和密码。设备出厂的用户名/密码默认为adm/123456。  

  ![](images/2020-01-13-10-51-57.png)  

- 步骤3：登录成功后，您可以看到如下图所示的网页。  

  ![](images/2020-01-13-10-52-29.png)  

- 步骤4：如需修改WEB管理界面的用户名和密码可进入IG902的“系统管理>>用户管理”页面设置新的用户名和密码。  

  ![](images/2020-01-13-13-21-42.png)  

- 步骤5：如需修改GE 0/2口的IP地址可访问IG902的“网络>>网络接口>>以太网>>千兆以太网0/2”页面进行修改。  

  ![](images/2020-01-13-10-54-00.png)  

<a id="set-wan-parameters"> </a>  

### 1.2 IG902连接Internet
  - 方法一：使用SIM卡拨号连接Internet
    - 步骤1：将SIM卡插入卡槽（注意：插拔SIM卡操作时，必须拔掉电源，以免造成数据丢失或设备损坏）。插入SIM卡后将4G LTE天线与ANT口连接，接通IG902的电源。  

      ![](./images/2019-11-07-13-21-24.png)  

    - 步骤2：进入IG902的“网络>>网络接口>>蜂窝网”页面，勾选“启用蜂窝网”并点击提交。  

      ![](images/2020-01-13-13-43-16.png)  

      待网络连接状态显示为“连接”并且显示已分配相应IP地址等状态时说明IG902已通过SIM卡联网。  

      ![](images/2020-01-13-13-48-18.png)  

  - 方法二：使用以太网连接Internet
    - 步骤1：使用以太网线连接IG902的GE 0/1和GE 0/2口，如下图：  

      ![](images/2020-01-13-18-43-38.png)  

    - 步骤2：进入IG902的“网络>>网络接口>>以太网>>千兆以太网0/1”页面，配置GE 0/1口的IP地址（网络类型为静态IP地址时需要根据现场网络情况配置IP、子网掩码等信息）并点击提交。  

      ![](images/2020-01-13-13-57-07.png)  

      ![](images/2020-01-13-13-57-33.png)  

    - 步骤3：进入IG902的“网络>>静态路由>>配置”页面，为GE 0/1口添加静态路由（接口项选择“Gigabitethernet 0/1”，其余项根据现场网络情况配置）并点击提交。  

      ![](images/2020-01-13-15-10-47.png)  

    - 步骤4：进入IG902的“系统管理>>工具”页面，使用Ping命令检测IG902是否成功接入Internet。  

      ![](images/2020-01-13-15-23-46.png)

<a id="update-the-software"> </a>  

## 2. 更新软件版本
如需获取IG902产品最新软件版本及其功能特性信息，请联系客服。如需更新IG902的软件版本，请参考如下方法。

<a id="update-the-firmware-software"> </a>  

### 2.1 更新IG902固件版本  
  
  点击“系统管理>>固件升级”，选择相应的固件文件后点击“开始升级”。IG902升级完成后，会提示重启设备以应用新的固件。  

  ![](images/2020-01-13-18-53-19.png)  
   
<a id="update-the-sdk-software"> </a>  

### 2.2 更新IG902 Python SDK版本  
  
  进入“边缘计算>>Python边缘计算”页面，勾选“Python边缘计算引擎”并选择相应的Python SDK文件点击“升级”;弹出升级确认窗口时点击“确认”，IG902会自动完成升级操作。  

  ![](images/2020-02-10-11-49-57.png)  
   
<a id="update-the-docker-software"> </a>  

### 2.3 更新IG902 Docker SDK版本  
  
  进入“边缘计算>>Docker管理”页面，点击升级并选择相应的Docker SDK文件。  

  ![](images/2020-02-10-14-13-15.png)  
   
  安装成功后，勾选启用Docker管理器并点击“提交”。  

  ![](images/2020-02-11-09-12-14.png)  
   
  启用Docker管理器后，可以点击Docker管理器的访问按钮访问管理页面。  

  ![](images/2020-02-11-09-14-20.png)  
  
  输入上图中设置的账号密码即可登录Docker管理器。  

  ![](images/2020-02-11-09-15-25.png)

<a id="use-python-edge-computing"> </a>  

## 3. Pyhon边缘计算

<a id="install-and-run-python-app"> </a>  

### 3.1 安装和运行Python App
在IG902中安装和运行Python App（以下简称App）请参考如下流程：  
- 步骤1：安装App  
  
  安装App前需要确保Python边缘计算引擎已启用且已安装Python SDK，如下图所示：  

  ![](images/2020-02-10-10-11-10.png)  

  进入“边缘计算>>Python边缘计算”页面，点击添加按钮并选择需要安装的App包文件，随后点击确定。  

  ![](images/2020-02-10-10-13-29.png)  

  导入成功后可以查看已导入的App，如下图所示：  

  ![](images/2020-02-10-10-16-55.png)  

- 步骤2：运行App  
  
  勾选启用App并点击提交。  

  ![](images/2020-02-10-10-35-53.png)  

  启用后App将在IG902中运行并且每次开机后自动运行。  

  ![](images/2020-02-10-10-38-59.png)

<a id="update-configuration-file-for-app"> </a>  

### 3.2 更新Python App运行配置
如果已安装的App支持导入配置文件修改运行方式，可参照如下流程更新App运行配置：
- 步骤1：进入“边缘计算>>Python边缘计算”页面，点击导入配置按钮并选择需要导入的配置文件，随后点击确认。  

  ![](images/2020-02-10-10-43-06.png)  
   
- 步骤2：导入成功后重启App，App重启完成后将按照导入后的配置文件运行。  

  ![](images/2020-02-10-10-45-55.png)

<a id="update-python-app-version"> </a>  

### 3.3 更新Python App版本
通常如需更新Python App版本时只需要在“边缘计算>>Python边缘计算”页面导入新版本的App即可。  

![](images/2020-03-18-19-54-07.png)  

更新完成后如下图所示：  

![](images/2020-03-18-19-54-44.png)

<a id="enable-the-debug-mode"> </a>  

### 3.4 开启调试模式
如需在IG902上运行并调试Python代码，需要启用IG902的调试模式。在“边缘计算>>Python边缘计算”页面中，勾选“启用调试模式”，启用后可通过VS Code对IG902进行开发。如何使用VS Code对IG902进行Python开发请参考[MobiusPi Python开发快速入门](http://sdk.ig.inhand.com.cn/zh_CN/latest/MobiusPi-Python-QuickStart-CN.html)。  

![](images/2020-02-10-11-00-28.png)  

启用调试模式后，IG902启动一个SSH Server，监听LAN网络(默认IP地址192.168.2.1)的222端口。SSH Server的用户名和密码将被显示到上述网页中。为了提高安全性，每次开启调试模式或重启设备，都会重新随机生成新的密码。

<a id="device-manager"> </a>  

## 4. 设备远程监控平台
映翰通开发的设备远程监控平台支持监视IG902状态、远程维护设备、远程批量下发IG902配置和IG902批量升级等功能，帮助用户便捷、高效的管理IG902和现场设备。为了使设备远程监控平台能够远程管理IG902和现场设备，需要将IG902连接到云平台上，连接方法如下：  
进入“系统管理>>设备远程监控平台”页面，勾选启用设备远程监控平台并配置相应的服务器地址以及注册账户，配置完成后点击提交即可。  
- 服务器地址：即设备远程监控平台地址。映翰通开发的远程监控平台地址如下：  
  - 国内版Device Manager：`c.inhandcloud.com`   
  - 海外版Device Manager：`iot.inhandnetworks.com`   
  - 国内版InConnect：`ics.inhandiot.com`   
  - 海外版InConnect：`ics.inhandnetworks.com`   
- 注册账户：即IG902关联的设备远程监控平台账号（如果还未注册账户需要先注册一个账号）  
- 高级设置：包含心跳间隔等配置，一般使用默认配置即可

![](images/2020-03-18-19-29-37.png)  

IG902与设备远程监控平台连接成功后状态描述为连接成功。  

![](images/2020-03-19-16-07-07.png)  

<a id="io-module"> </a>  

## 5. IO模块
<font color=#FF0000>注意：以下信息仅针对下图所示的带IO模块的IG902  </font>  

![](images/2021-04-16-20-02-42.png) 

IG902支持数字量输入、脉冲计数、数字量输出和脉冲输出功能。同时，通过Modbus TCP协议可以远程读取IO的状态数据或者上报至云平台。
各模式下的IO定义如下：
- 数字量输入（根据实际接线情况区分干湿接点）
  - 干接点  

    0：断开  

    1：闭合  

    接线方式如下图所示：  

    ![](images/2021-04-06-10-59-57.png)


  - 湿接点  

    0: 0 ~ 3VDC/-3 ~ 0VDC  

    1：10 ~ 30VDC/-30 ~ -10VDC（4mA min.）  

    接线方式如下图所示：  

    ![](images/2021-04-06-11-00-38.png)

- 脉冲计数  

  最高支持3000Hz脉冲信号计数，最大支持计数至4294967296。  
  接线方式如下图所示：  

  ![](images/2021-04-06-11-00-38.png)

- 数字量输出  

  0：OFF。  

  1：ON。根据外接的电源输出电压，如果未外接电源则无电压输出，最大为30V，500ma。  

  接线方式如下图所示：  

  ![](images/2021-04-06-11-04-28.png)

- 脉冲输出  

  最大支持5000Hz脉冲信号输出。  
  
  接线方式如下图所示：  

  ![](images/2021-04-06-11-04-28.png)

配置IO并获取IO状态数据的步骤如下：
- 步骤1：进入“边缘计算 > IO模块 > 配置”页面，按照实际情况配置IO功能。配置示例如下：  

  - 数字量输入
    
    ![](images/2021-03-12-16-58-24.png)

  - 脉冲计数  

    从0开始计数，掉电后保持掉电前的计数值。  

    ![](images/2021-03-12-16-58-51.png)

  - 数字量输出
    
    ![](images/2021-03-12-17-00-16.png)

  - 脉冲输出  

    按照5000Hz的频率，50%的占空比输出脉冲。  

    ![](images/2021-03-12-17-01-44.png)


- 步骤2（可选）：脉冲计数和脉冲输出设置  

  DI设置为脉冲计数后，点击“开始计数”后对DI接收到的脉冲进行计数，否则不计数。点击“重置计数”后将计数值重置为起始值。  

  ![](images/2021-04-06-11-35-55.png) 

  DO设置为脉冲输出后，点击“开始输出”后按照设定的输出频率输出脉冲，否则不输出。  

  ![](images/2021-04-06-11-36-15.png)

- 步骤3：设置Modbus TCP从站  

  开启“启用”后启用Modbus TCP从站功能，该功能支持Modbus TCP Master读取IG902的IO状态；开启“外部访问”后允许网关外部的Modbus TCP Master读取IG902的IO状态（如SCADA软件）。其余项根据实际情况配置，示例配置如下：  

  ![](images/2021-04-06-11-34-20.png)
  
- 步骤4：通过Modbus TCP读取IO状态  

  以Device Supervisor读取步骤3配置中的IG902 IO状态为例。首先添加一个Modbus TCP协议的控制器，控制器通讯参数按照Modbus TCP从站进行配置。  

  ![](images/2021-04-06-11-43-25.png)

  随后按照Modbus映射表的说明配置要采集的数据，以读取“DI0计数值”为例。  

  ![](images/2021-04-06-11-44-53.png)  

  ![](images/2021-04-06-11-45-25.png)

  配置完成后可以获取到“DI0计数值”。

  ![](images/2021-04-06-11-46-23.png)


<a id="appendix"> </a>  

## 附录

<a id="factory-reset"> </a>  

### 恢复出厂设置
IG902恢复出厂设置的方式有两种：硬件恢复出厂设置和软件恢复出厂设置  
- 硬件恢复出厂设置  
  - 步骤1：设备上电且ERR灯熄灭后，按住RESET键；  
  - 步骤2：ERR灯常亮时，松开RESET键；  
  - 步骤3：ERR灯熄灭后，再次按住RESET键，ERR灯闪烁时松开RESET键；等待ERR灯熄灭，表明恢复出厂设置成功。  
   
- 软件恢复出厂设置  
  
  进入“系统管理>>配置管理”页面，点击重置按钮并选择确定。IG902将自行完成恢复出厂设置操作。  

  ![](images/2020-02-10-11-18-16.png)