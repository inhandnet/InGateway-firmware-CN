# InGateway902命令行指令说明手册

  - [命令行指令说明](#command-line-instructions)
    - [1. 帮助命令](#help-command)
      - [1.1 ?](#firstone)
    - [2. 视图切换命令](#view-switching-commands)
      - [2.1 enable](#enable)
      - [2.2 disable](#disable)
      - [2.3 exit](#exit)
    - [3. 查看系统状态命令](#view-system-status-commands)
      - [3.1 show version](#show-version)
      - [3.2 show system](#show-system)
      - [3.3 show clock](#show-clock)
      - [3.4 show log](#show-log)
      - [3.5 show users](#show-users)
      - [3.6 show startup-config](#show-startup-config)
    - [4. 查看网络状态命令](#view-network-status-command)
      - [4.1 show interface](#show-interface)
      - [4.2 show ip route](#show-ip-route)
      - [4.3 show arp](#show-arp)
    - [5. 网络测试命令](#network-test-commands)
      - [5.1 ping](#ping)
      - [5.2 telnet](#telnet)
      - [5.3 traceroute](#traceroute)
    - [6. 配置命令](#configuration-commands)
      - [6.1 configure terminal](#configure-terminal)
      - [6.2 hostname](#hostname)
      - [6.3 clock timezone](#clock-timezone)
      - [6.4 clock set](#clock-set)
      - [6.5 sntp-client](#sntp-client)
    - [7. 系统管理命令](#system-management-commands)
      - [7.1 reboot](#reboot)
      - [7.2 enable password](#enable-password)
      - [7.3 username](#username)

<a id="command-line-instructions"> </a>

##  命令行指令说明

<a id="help-command"> </a>

### 1. 帮助命令
在控制台输入 help 或 ? 可获取命令帮助，在输入命令的过程中可随时输入 ? 获取当前命令或命令参数的帮助，在命令或命令参数唯一时还能自动补全命令或参数。

<a id="firstone"> </a>

#### 1.1 ?
**命令**：[\<cmd>] ?  
**功能**：获取命令的帮助。  
**视图**：所有视图  
**参数**：命令名cmd  
**示例**：
- 输入：`?`  
获得当前所有可用命令的列表。  
- 输入：`show ?`  
显示 show 命令的所有参数及其使用说明。  

<a id="view-switching-commands"> </a>

### 2. 视图切换命令

<a id="enable"> </a>

#### 2.1 enable
**命令**：enable 15 [\<password>]  
**功能**：切换到特权用户级别。  
**视图**：普通用户视图  
**参数**：
- 15：用户权限级别，目前只支持权限级别 15（超级用户）  
- password：特权级别对应的密码，如果不输入则会给出输入密码的提示  

**示例**：
- 在普通用户视图下输入： `enable 15 123456`
切换到超级用户，密码为 123456。

<a id="disable"> </a>

#### 2.2 disable
**命令**：disable  
**功能**：退出特权用户级别。  
**视图**：超级用户视图，配置视图  
**参数**：无   
**示例**：
- 在超级用户视图下输入： `disable`  
返回普通用户视图。

<a id="exit"> </a>

#### 2.3 exit
**命令**： exit  
**功能**：退出当前视图，返回前一视图（如果当前为普通用户视图则退出控制台。   
**视图**：所有视图  
**参数**：无   
**示例**：
- 在配置视图下输入： `exit`  
返回到超级用户视图。  
- 在普通用户视图下输入： `exit`  
  退出控制台。

<a id="view-system-status-commands"> </a>

### 3. 查看系统状态命令

<a id="show-version"> </a>

#### 3.1 show version
**命令**：show version  
**功能**：显示路由器的型号、软件版本等信息。   
**视图**：所有视图  
**参数**：无   
**示例**：
- 输入： show version
  显示如下信息：  
  型号 : 显示IG902出厂型号  
  序列号 : 显示IG902出厂序列号  
  固件版本 : 显示IG902固件版本  
  Bootloader 版本 : 显示IG902的Bootloader版本  

<a id="show-system"> </a>

#### 3.2 show system
**命令**：show system  
**功能**：显示路由器系统信息。   
**视图**：所有视图  
**参数**：无   
**示例**：
- 输入： `show system`  
显示如下示例信息：
`09:26:45 up 5 days, 14:33,  1 users,  load average: 0.00, 0.01, 0.04`

<a id="show-clock"> </a>

#### 3.3 show clock
**命令**：show clock  
**功能**：显示路由器的系统时间。   
**视图**：所有视图  
**参数**：无   
**示例**：
- 输入： `show clock`  
  显示如下示例信息：  
  `Wed Apr 15 09:33:48 UTC 2020`

<a id="show-log"> </a>

#### 3.4 show log
**命令**：show log [lines \<n>]  
**功能**：显示路由器的系统日志，默认显示最新的 100 条日志。   
**视图**：所有视图  
**参数**：lines <n> 限制显示的日志条数，其中 n 为正整数时显示最新的 n 条日志，为负整数时显示最早的 n 条日志，为 0 表示输出所有日志。  
**示例**：
- 输入： `show log`  
  显示最新的 100 条日志记录。
- 输入： `show log lines 10`  
  显示最新的 10 条日志记录。

<a id="show-users"> </a>

#### 3.5 show users
**命令**：show users  
**功能**：显示路由器的用户列表。   
**视图**：所有视图  
**参数**：无  
**示例**：
- 输入： `show users`  
  显示如下示例信息：  
  <table>
  <tr>
  <td>USER</td>
  <td>TTY</td>
  <td>IDLE</td>
  <td>TIME</td>
  <td>HOST</td>
  </tr>
  <tr>
  <td>adm</td>
  <td>pts/0</td>
  <td>00:00</td>
  <td>Apr 15 09:26:41</td>
  <td>192.168.1.15</td>
  </tr>
  </table>

<a id="show-startup-config"> </a>

#### 3.6 show startup-config
**命令**：show startup-config  
**功能**：显示路由器的启动配置。   
**视图**：超级用户视图、配置视图  
**参数**：无  
**示例**：
- 输入： `show startup-config`  
  显示系统的运行配置。

<a id="view-network-status-command"> </a>

### 4. 查看网络状态命令

<a id="show-interface"> </a>

#### 4.1 show interface
**命令**：show interface  
**功能**：显示路由器的接口状态信息。   
**视图**：所有视图  
**参数**：无  
**示例**：
- 输入： `show interface`  
  显示所有接口的状态信息。

<a id="show-ip-route"> </a>

#### 4.2 show ip route  
**命令**：show ip route  
**功能**：显示路由器的路由表。   
**视图**：所有视图  
**参数**：无  
**示例**：
- 输入： `show ip route`  
  显示系统的路由表。

<a id="show-arp"> </a>

#### 4.3 show arp
**命令**：show arp  
**功能**：显示路由器的 ARP 表。   
**视图**：所有视图  
**参数**：无  
**示例**：
- 输入： `show arp`  
  显示系统的ARP表。

<a id="network-test-commands"> </a>

### 5. 网络测试命令
IG902提供了 ping、telnet 和 traceroute 等网络测试工具用于网络测试。  

<a id="ping"> </a>

#### 5.1 ping
**命令**：ping \<hostname> [count \<n>] [size \<n>] [source \<ip>]  
**功能**：对指定的主机执行 ICMP 探测。   
**视图**：所有视图  
**参数**：
- hostname: 要探测的主机地址或域名  
- count \<n>: 探测的次数  
- size \<n>: 探测数据包的大小（字节）  
- source \<ip>: 指定探测时所使用的 IP 地址  

**示例**：
输入： ` ping www.baidu.com count 5 size 32`  
执行对 www.baidu.com 的探测并显示探测结果。

<a id="telnet"> </a>

#### 5.2 telnet
**命令**：telnet \<hostname> [\<port>] [source \<ip>]   
**功能**：telnet 登录到指定的主机。   
**视图**：所有视图  
**参数**：  
- hostname： 要 telnet 登录的主机地址或域名  
- port： telnet 的端口  
- source \<ip>： 指定 telnet 登录时所使用的 IP 地址  

**示例**：
- 输入： `telnet 192.168.1.1`  
telnet 登录到 192.168.2.2。

<a id="traceroute"> </a>

#### 5.3 traceroute
**命令**：traceroute \<hostname> [maxhops \<n>] [timeout \<n>]   
**功能**：对指定的主机执行路由探测。   
**视图**：所有视图  
**参数**：  
- hostname： 要探测的主机地址或域名  
- maxhops \<n>：探测的最大路由跳数
- timeout \<n>： 每一跳探测的超时时间（秒）  

**示例**：
- 输入： `traceroute www.baidu.com`  
执行对 www.baidu.com 的路由探测并显示探测结果。

<a id="configuration-commands"> </a>

### 6. 配置命令
在超级用户视图下，可用 `configure terminal` 命令切换到配置视图对IG902进行管理。一些设置
命令同时支持 no 和 default 两种变形，其中 no 表示取消某项参数的设置，default 表示恢复
某项参数为默认配置。

<a id="configure-terminal"> </a>

#### 6.1 configure terminal 
**命令**：configure terminal   
**功能**：切换到配置视图，从终端输入配置。   
**视图**：超级用户视图  
**参数**：无    
**示例**：
- 在超级用户视图下输入： `configure terminal`  
切换到配置视图。

<a id="hostname"> </a>

#### 6.2 hostname
**命令**：  
- hostname [\<hostname>]   
- default hostname  

**功能**：设置路由器的主机名。   
**视图**：配置视图   
**参数**：\<hostname>：新的主机名    
**示例**：
- 在配置视图下输入： `hostname MyRouter`  
设置IG902的主机名为 MyRouter。  
- 在配置视图下输入： `default hostname`  
恢复IG902的主机名为出厂设置。

<a id="clock-timezone"> </a>

#### 6.3 clock timezone
**命令**：
- clock timezone \<timezone>-\<n>   
- default clock timezone  
**功能**：设置路由器的时区信息。   
**视图**：配置视图  
**参数**：
- \<timezone>：时区名称，3 个大写英文字母  
- \<n>：时区偏差值，-12~+12  
**示例**：
- 在配置视图下输入： `clock timezone UTC-8`  
设置路由器的时区为UTC+08:00 中国大陆，香港，西澳大利亚，新加坡，台湾，俄罗斯。  
- 在配置视图下输入： `default clock timezone`  
恢复路由器的时区为出厂设置。

<a id="clock-set"> </a>

#### 6.4 clock set
**命令**：clock set \<YEAR/MONTH/DAY>-\<HH:MM:SS>   
**功能**：设置路由器的日期和时间。   
**视图**：配置视图  
**参数**：
- \<YEAR/MONTH/DAY>： 日期，格式为：年-月-日
- \<HH:MM:SS>： 时间，格式为：小时-分钟-秒   

**示例**：
- 在配置视图下输入： `clock set 2009.10.5-10:01:02`  
设置路由器的时间为 2009 年 10 月 5 日上午 10 点 01 分 02 秒。

<a id="sntp-client"> </a>

#### 6.5 sntp-client
**命令**：
- sntp-client update-interval \<n>  
- sntp-client source interface \<interface> \<slot/port>   
- sntp-client server \<hostname> [\<port>] \<n>   

**功能**：设置网络时间SNTP客户端。   
**视图**：配置视图  
**参数**：
- update-interval \<n>：更新时间间隔，合法值  
- \<interface> \<slot/port>：源接口，合法值`cellular1`等接口  
- \<hostname>： 时间服务器的主机地址或域名 
- [\<port>] \<n>：时间服务器端口号
 
**示例**：
- 在配置视图下输入： `sntp-client update-interval 7200`  
  设置SNTP客户端的更新时间间隔为7200秒。
- 在配置视图下输入： `sntp-client source interface cellular 1`  
  设置SNTP客户端的源接口为cellular1。
- 在配置视图下输入： `sntp-client server 0.pool.ntp.org port 123`  
  设置SNTP客户端的服务器地址为 0.pool.ntp.org ，端口号123。

<a id="system-management-commands"> </a>

### 7. 系统管理命令

<a id="reboot"> </a>

#### 7.1 reboot
**命令**：reboot   
**功能**：重启系统。   
**视图**：超级用户视图，配置视图  
**参数**：无    
**示例**：
- 在超级用户视图下输入： `reboot`  
  系统重新启动。

<a id="enable-password"> </a>

#### 7.2 enable password
**命令**：enable password [\<password>]   
**功能**：更改超级用户的密码。   
**视图**：配置视图  
**参数**：\<password>：新的超级用户密码     
**示例**：
- 在配置视图下输入： `enable password`  
  更改超级用户的密码。

<a id="username"> </a>

#### 7.3 username
**命令**：
- username \<name> [password [\<password>]]   
- no username \<name>   

**功能**：设置用户名、密码。   
**视图**：配置视图  
**参数**：  
- \<name>：用户名  
- \<password>：密码  

**示例**：
- 在配置视图下输入： `username abc password 1234567`  
增加一个普通用户，用户名为 abc，密码为 1234567；或修改普通用户abc的密码为1234567  
- 在配置视图下输入： `no username abc`  
删除用户名为 abc 的普通用户。