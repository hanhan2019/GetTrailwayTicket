# 抢票脚本项目
本项目来自灵动的艺术分享的GitHub源码，感谢大佬的开源分享。
有所修改，加上学生票的一些操作。
## 刷票
### 脚本说明
扫描模式自动刷票脚本 和 精确模式自动刷票脚本 核心流程原理都一样：利用selenium来模拟真实浏览器，将所有的人工操作都转换为机器自动化完成。

`selenium_12306_ticket.py`脚本的核心在于如果当前票已经卖光了，我们还是想买这张票，就可以利用这个脚本不断的尝试刷票购买，因为`selenium`模拟取网站信息比较慢，我这里利用了协程来加速扫描速度，只要扫描到了我们的票就立即跳转购买了。`selenium_12306_ticket.py`脚本可以配置多车次，多席位，多用户选择。

`selenium_12306_ticket_exact_mode.py`脚本的核心在于它只会精确的刷我们关心的车次，所以它的速度比`selenium_12306_ticket.py`全车次扫描脚本要快的多，因为目前春运的票还没有开始售卖，所以所有的人应该想用的是这个本脚本也支持多席位，多用户。

12306账号密码配置写在config里对应的文件里，目前使用的是手机客户端扫码登陆，账号密码可以不填，如果需要使用账号密码登陆，修改脚本中code_login值为False,然后运行。手动选择验证图片，再按说明执行即可。
### 运行要求
首先安装selenium 和requests

pip3 install -U selenium

pip3 install requests

在http://chromedriver.storage.googleapis.com/index.html上下载对应的browser driver,放到工程目录下

### 运行指令
精确模式自动刷票脚本
python3 selenium_12306_ticket_exact_mode.py
扫描模式自动刷票脚本
python3 selenium_12306_ticket.py