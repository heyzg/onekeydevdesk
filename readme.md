省事一键DD云虚拟机云容器云桌面云开发(带镜像有演示)
=====

onekeydevdesk是一套可在线一键安装系统的脚本和方案1keydd，及一套增强的虚拟机管理器系统devdeskos，加一套学习编程的软硬选型（定位于掌上蓝牙键盘或移动设备输入+TEXTUI IDE服务端）。   

 * 作为onekeydevdesk的安装脚本部分，基于debianinstaller增强,1keydd支持扩展多机型安装多OS类型，支持自打包，自托管，可将你对应机型包括镜像在内的整个DD方案构建为一个可供DD安装的在线仓库,甚至包括生成编辑镜像在内的全套dd支持方案  
 * 作为onekeydevdesk的围绕虚拟机管理器为统一多OS容器核心，基于lxc增强+pve，devdeskos实现了一套统一透明ve性质pve fork,还将拟集成一套云neovim服务端IDE面板（作为pve的developermode存在），模拟一套全能沉浸碎片化的IDE。    

> onekeydevdesk也指代：1keydd,1keynotedevdesk,1keydevabledocker,1keydiskdump,1keydeepindsm,1keydebiandesk,1keydevdeploy,1keydebugdemo,1key desk dock,1key datacenter and desk,1key dir disk,1key deconterized desk,1kilometer distance to dev,1key for dev over dev(second dev),etc ..

项目地址：https://github.com/minlearn/onekeydevdesk 

演示与特性
-----

1keydd支持多种在线安装方式(wgetdd,liveuntar,nc)，双进度显示(vnc,web)，支持双架构amd,arm，支持自扩硬盘和智能嵌入静态ip参数(包括/32这样的特殊掩码支持)，支持免d坏模式，可达成90%的linux成功率,80%的other os成功率  
![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/1keydd.png)

1keydd支持一键dd多种os，如，支持win uefi/bios gpt二合一兼容，无视机型差别和无须手动，毫无修改毫无感知地以同一效果运行,支持dsm直接安装在云主机上，dsm无须嵌套虚拟化支持>2T硬盘作为启动硬盘,支持osx使用标准全套kvm驱动和bios机型配置，需要安装在支持嵌套虚拟化的2C2G以上云主机上（1c1.5g/2c2g给osx, 2c2g/3c3g给osx母鸡留1c1g最好），与本地组matedesk，win11类同。  
![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/1keydevdeskwin.png)
![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/1keydevdeskdsm.png)
![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/1keydevdeskosx.png)

devdeskos类似于colinux和安卓ashmem/binder的技术代替qemu passthrough，用lxc替代qemu+docker实现,实现虚拟机和容器统一透明共存。
![](https://github.com/minlearn/minlearnprogramming/raw/master/p/_contents/assets/intro/1keydirdisk.png)

1keydd+devdeskos支持扩展，包括az,servarica,oracle/oracle arm,ksle,bwg10g512m,及无限增加的机型和系统：   

| 机型             | 是否支持裸机win | 是否支持裸机linux/devdeskos | 是否支持裸机osx | 是否支持pveosx | 是否支持静态ip嵌入 | 是否支持win中d win |
| :------:        | :-: | :-: | :-: | :-: | :-: | :-: | 
| azure b1s       |  √  |  √  |  ×  |  ×  |  √  |  ×  |
| spartan         |  √  |  √  |  ×  |  ×  |  √  |  ×  |
| ikoula c-mem    |  √  |  √  |  ×  |  √  |  √  |  ×  |
| ksle/ksleplus   |  √  |  √  |  ×  |  √  |  √  |  ×  |
| SYS-2-SSD-64    |  √  |  √  |  ×  |  √  |  √  |  ×  |
| gcp             |  √  |  √  |  ×  |  ×  |  √  |  ×  |
| linode          |  √  |  √  |  ×  |  ×  |  √  |  ×  |
| orc amd         |  √  |  √  |  ×  |  ×  |  √  |  ×  |
| orc arm         |  ×  |  √  |  ×  |  ×  |  √  |  ×  |
| ...             | ... | ... | ... | ... | ... | ... |

完整支持查看hub页，更多演示和特性请看和项目文档库[《更多文档》](/onekeydevdesk/docs/)部分

下载安装及用法
-----

以下尽量在debian系linux云主机或本地虚拟机下完成,centos不推荐  

基本用法:  

 * 简单前端交互模式  
`wget -qO- 1keydd.com/inst.sh | bash`   

 * 指定安装目标os镜像：debian是原生方式安装的纯净debian10,devdeskos是live方式安装的devdeskos,debian10r是dd方式安装的debian10的raw系统硬盘格式经过gzip打包,自定义镜像是dd方式安装的raw系统硬盘格式经过gzip打包后托管的http/https地址（ 安装演示：https://www.bilibili.com/video/BV1ug411N7tn/ https://www.bilibili.com/video/BV17B4y1b79Y/ ）  
`wget -qO- 1keydd.com/inst.sh | bash -s - -t debian,devdeskos,debian10r,或自定gz镜像`  

dd过程中，如有网络直接访问ip:80，会看到vnc进度，如果要进一步查看问题，用sshd用户无密码方式访问ssh或访问ip:8000。如无网络5分钟后会重启,并进入DD前的正常系统。免破坏系统。
目标os安装后，会自动扩展磁盘空间和调整网络,用户名为root/admininistraor，密码为1keydd，不做说明的情况下，上述镜像均为脚本内置镜像，第三方gz镜像并不提供开放托管和安装。  

高级用法:  

 * 指定debian镜像源  
`wget -qO- 1keydd.com/inst.sh | bash -s - -m http/https/xxxx ......`  

 * 指定第一张网卡名  
`wget -qO- 1keydd.com/inst.sh | bash -s - -i enp0s1 ......`  

 * 指定静态网络配置（ 安装演示：https://www.bilibili.com/video/BV1pr4y1j75w/ ）  
`wget -qO- 1keydd.com/inst.sh | bash -s - -n ipv4,netmask,gateway .....`  

 * 指定第一个硬盘名(你也可以填分区名把镜像d到仅一个分区里)  
`wget -qO- 1keydd.com/inst.sh | bash -s - -p nvme0n1 ......`  

 * 指定grub启动分区(支持deb和devdeskos,tarball需要镜像配合)  
`wget -qO- 1keydd.com/inst.sh | bash -s - -e nvme0n1 ......`  

更多模式:

 * 进入dump模式：提供blkdevname:ip:port参数形式将作为源端/发送端/连接端/客户端(请自备开启了nc port:保存形态，作为参数的目标端/接收端/本地代理端/守护服务端的被DD机器，并首先开启)  
`wget -qO- 1keydd.com/inst.sh | bash -s - -t dumpblkdevname:sendtoip:sendtoport`   

 * 进入救援/DRYRUN/DEBUG模式,此模式HOLD不重启不插入改写硬盘的操作,可作DD前验证  
`wget -qO- 1keydd.com/inst.sh | bash -s - -d`  

自托管1keydd:  

 * 通过git仓库:  
`fork本仓库后,新的debian镜像源将变成https://github.com/你的用户名/onekeydevdesk/raw/master'`  
`或修改inst.sh头二行debian镜像源地址export autoDEBMIRROR0,export autoDEBMIRROR1为你的仓库对应debian镜像源地址,或修改export FORCEMIRROR指定为新的镜像源地址`  

 * 通过docker:  
`docker pull minlearn/onekeydevdesk`  
`docker run -d --name myonekeydevdesk -e m=你的新debian镜像源地址 -p 80:80 minlearn/onekeydevdesk`  

建立托管后，用新的inst.sh脚本地址调用脚本即可  

服务
-----

免费
 * 只提供inst.sh，可一站式解决你DD中大部分问题，去上面仓库，一键DD即可  
`注：仅拥有常见vps和独服机型上DD常见系统能力`  

收费  
 * 获取指定系统镜像和安装服务1次或解决疑难机型DD服务1次（50元,usdt 10）   
 * 加入付费DD群享免费咨询技术支持（100元,usdt 20）   
`注：加入付群DD群拥有终身免费DD咨询,扩展驱动/定制机型服务和获取[《更多第三方镜像》](/onekeydevdesk/hub/)的能力`  
`加如下作者个人TG：简单说明需求或说明来意即可`     

[minlearn_1keydd](https://t.me/minlearn_1keydd)

捐助
 * 打赏我任意数值虚拟币,20usdt可加入付费DD群享免费咨询技术支持    
`怎么捐助: 用支持tron链的钱包APP扫描下列钱包地址，或二维码`  

TRX/USDT/BTC/ETH: [TZ6YPtsojLCJEifNpwm38mmiq7T2gkhGKj](https://tronscan.io/#/address/TZ6YPtsojLCJEifNpwm38mmiq7T2gkhGKj)
![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/donate.png)

-----


此项目关联 https://github.com/minlearn/minlearnprogramming/raw/master/p/onekeydevdeskopen/ ，同时它是为配合我在《minlearnprogramming》最小编程/统一开发的想法的一个支持项目。作为一套"虚拟机管理器"到系统最小核心，及由基于此核心+入devops，并相关管理工具和相关脚本，最终组合实现的一套"一键开发桌面理念"系统存在。  

本项目长期保存

![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/logo123zd15sz150.png)
