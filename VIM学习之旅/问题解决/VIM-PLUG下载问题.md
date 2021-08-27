# vim安装vim-plug报错：Failed connect to raw.githubusercontent.com:443;（拒绝连接）
- 问题:Failed connect to raw.githubusercontent.com:443; Connection refused；
- 解决:网上都会更改hosts文件，他们所有人都改成
	```
	199.232.28.133 raw.githubsercontent.com
	```
	但是并不能解决问题，一直下载不了。
	- 继续研究问题所在，更改hosts是因为域名被污染，所以先去找到该域名的IP，通过线上的工具，可以查到其域名的IP为185.199.108.133。
	- 最终，只要把199.232.28.133替换成185.199.108.133即可，如果还是不行可以查最新的IP地址，不要一味的复制当前的IP。