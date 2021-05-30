# My operating system note.  
***
***2021.05.28更新  
开始打算学操作系统是在五一放假期间，那时候还没那么忙，当时实在有些天真，以为这学期课很少，可以学点自己喜欢的课程。后来随着有些课程的结课，复习考试，党课培训，其他课程的实验等接踵而至，五一以后的几天，我确实也有学过操作系统，我是跟着哔哩哔哩上本校计算机学院李治军老师的课学的，一共有32节课，我学到大概10节课左右，基本学完了操作系统的启动，线程和进程等内容，还没做实验，后面的打算放一放了，接下来要准备这学期的考试课，保研或考研，所以操作系统的学习只能先放一放，等一切确定之后在学习。***
***
## 0.1 关于为什么要写这个笔记
This is my first note. I just want to record my experience of learning OS.  
第一句话是在linux系统里写的，我实在找不到怎么切换成中文，我英语又烂极了，好在现在已经切换过来了。在写笔记之前，我同时也在学习markdown的格式，我其实在哪方面都是个小白，希望能够坚持下来。fighting!!!  
github我也是第一次使用，好多功能都不太了解，github可以托管代码，自然也可以托管我的笔记，代码可能不是那么多，我只是当成一个笔记托管平台。
## 0.2 开始之前的一些准备
02/05/2021 20:19  
由于readme.md是markdown格式的，所以有必要简单学习一下markdown的语法
### 0.2.1 markdown语法
学习操作系统之前我想用markdown格式记录一下我的学习历程。这里先简单学习一下markdown的语法。
#### (1)标题
"# head"  
"## subhead"
#### (2)图片
![insert picture](http://www.hit.edu.cn/_upload/article/images/c4/6d/cd373ba64525bccbf69d980fd7f3/2989e504-25fb-422f-aaaf-46079b41746a.jpg)  
感叹号"!"+[图片描述]+("图片链接")
#### (3)强调
*强调*  
**加重强调**  
***特别强调***
#### (4)代码
两种方式  
##### 1.反引号(line code)
`this is a code`  
`#include<stdio.h>`  
##### 2.tab or 4 spaces(block code)
	int main()
	{
		printf("hello world\n");
		return 0;
	}
#### (5)换行
在需要的地方加2 spaces+enter即可。
#### (6)引用
>一级引用  
>>二级引用
#### (7)链接
[链接文字](http://www.hit.edu.cn)  
<993721504@qq.com>  
<http://www.hit.edu.cn>  
[reference shyle](id)  
[id]:http://www.hit.edu.cn   
#### (8)分割线
***  
---  
___  
(以上分割线用三个及以上* or - or _ 才会产生分割线)      
#### (9)列表标记
三种标记方法:  
1. "1."+space  
2. "2."+space  
* "*"+space  
- "-"+space  
***
***以上9条语法应该足够记笔记了，markdown的语法就先简单学到这里，以后要用到其他的语法在进一步学习。***
***
### 0.2.2 Linux系统基础知识
我安装了VirtualBox虚拟机，在里边安了Ubuntu16.04。由于我本身学的是通信工程，学习操作系统对我来说还是有些难度，包括Linux常用命令，汇编等知识知之甚少，虽然以前学过汇编，但当时不求甚解，并没有掌握多少。现在简单学习一下Linux系统基础知识。
#### (1) Linux由来
Linux英文解释是Linux is not Unix. 它是一个完全开源的类Unix操作系统。实际上它是由Linus Bendict Torvalds出于个人爱好而编写的，受到了Minix和Unix操作系统的启发。
#### (2) Linux安装
一般有两种安装方案：  
1. 虚拟机（对电脑配置要求较高）  
2. 双系统（配置要求不高）  
这里我选择的是虚拟机安装，笔记本的系统是windows10。  
首先可选的虚拟机软件有很多，包括VMware，VirtulBox等，这两款软件相对来说比较大，个人亲测，配置不是太高的笔记本建议选择VirtualBox,[官网下载](https://download.virtualbox.org/virtualbox/6.1.22/VirtualBox-6.1.22-144080-Win.exe)或[HIT镜像网站](https://mirrors.hit.edu.cn/virtualbox/)，VMware可能会比较卡，Linux发行版我选择的是[Ubuntu16.04LTS](https://mirrors.hit.edu.cn/#/home),直接选对应的desktop版本即可，server版本是给服务器用的，没有界面，亲测HIT镜像网站下载速度能达到10MB/s,可能是因为我用的校园网吧。  
具体安装教程请参考百度。
#### (2) Linux常用命令
1. `cd`,change directory的缩写，在终端输入该命令`cd /home`可进入home目录，这里有绝对路径和相对路径之分，注意区分。
2. `apt`,advanced packing tool的缩写，是一个软件包管理器。  
常见apt命令：  
>`sudo apt update`:列出所有可更新的软件清单  
>`sudo apt upgrade`:升级软件包  
>`sudo apt install <package_name>`:安装指定软件  
>`sudo apt update <package_name>`:更新指定软件  
>`sudo apt show <package_name>`:显示指定软件的版本等信息  
>`apt list --installed`:列出所有已安装的软件  
>`apt list --all-versions`:列出所有已安装的软件的版本信息  
***注意：带有sudo的命令需要输入密码，密码输入时屏幕上不显示，不要以为系统出问题了***  
***
2021.5.3  
昨天折腾了一天，本来打算在GitHub上写笔记的，但晚上回到寝室我发现了一个大问题，<https://github.com>总是登不上，这一点我非常不能接受，虽然我非常喜欢github网站的风格，也能对我的英语有一定的提高，但我还是换成了<https://gitee.com>。而我发现gitee可以直接关联我的github账号，甚至一键复制我在github上的仓库。
***
