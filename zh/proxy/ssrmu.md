# 魔改V3后端一键docker


> 市面上有很多一键部署sspanel v3 mod的脚本.但要么不太好使.要么有使用条件.而且安装时间也比较长.于是做了个docker.利用hyperapp即可一键解决

### 本文原文链接为 https://vinga.tech/ssrmu 原文更新更为及时

## 更新记录

- 2018.02.18:完全重构镜像.合并了latest和db分支.现在完全使用原版赵大魔改ssr后端的环境变量.具体设置看文章.注意!!!需要根据新版的环境变量进行修改!!不予向后兼容!!
- 2017.12.29:重构镜像.对镜像进行了优化提升了性能.通过增加启动参数`--restart=always`来提升稳定性.请自行在options中增加.
- 2017.12.18:压缩了镜像.
- 2017.11.21:增加glzjinmod的链接方式

## 准备

- **HyperApp**
- **耐心.仔细.认真**

## 环境变量

```
NODE_ID=1                     
SPEEDTEST=6                   
CLOUDSAFE=1                   
AUTOEXEC=0                    
ANTISSATTACK=0                
MU_SUFFIX=zhaoj.in            
MU_REGEX=%5m%id.%suffix       
API_INTERFACE=modwebapi       
WEBAPI_URL=https://zhaoj.in   
WEBAPI_TOKEN=glzjin           
MYSQL_HOST=127.0.0.1          
MYSQL_USER=ss                 
MYSQL_PASS=ss                 
MYSQL_DB=shadowsocks          
REDIRECT=github.com           
FAST_OPEN=false
```

## 在HyperApp进行设置

1. **转到商店页面.找到Docker Image然后选择服务器并且保存进入配置界面**
2. **请完全按照下图配置进行填写！**

| 应用设置名称 | 内容                                                         |
| ------------ | ------------------------------------------------------------ |
| Image        | fanvinga/docker-ssrmu                                        |
| Options      | `-e 环境变量名称=你需要的值 -e 环境变量名称=你需要的值 --network=host  --restart=always` |
| Command      |                                                              |
| Args         |                                                              |

1. **保存并且进行安装.**
2. **现在的ssrmu镜像完全复刻出userapiconfig.py和user-config.json文件里面的所有常见配置选项.只需要使用-e的映射方式.参考相关格式进行填写即可**
3. **注意最后两个变量REDIRECT和FAST_OPEN是user-config.json里面的.如果不知道应该改成什么值.保持默认就行**
4. **注意REDIRECT的可能形式为\*:80#127.0.0.1:2333.直接填写 -e REDIRECT=*:80#127.0.0.1:2333即可**

## 大功告成

- **这时候去访问你的域名吧٩(˃̶͈̀௰˂̶͈́)و**

<a href="https://vinga.tech"><img src="https://d.unlimit.fun/design/banner.png" alt="banner" target="_blank"></a>