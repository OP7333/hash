# 轻松搞定 RAR、Zip压缩包密码！Hashcat +john the ripper 亲测好用！

1.hashcat ：https://hashcat.net

2.john the ripper ：https://www.openwall.com

注：官网是英文的，可以通过谷歌浏览器翻译成中文

只需用到2个命令：

rar2john.exe xxxx.rar   –获取hash值

hashcat.exe -m 13000 -w 4 -a 3 $rar5$16$b88c1d7d2c96dc9d1b1a5ccdc5c25d50$15$8f0b287c982535c868bbff486ee9acd2$8$43907bfa03430471 -o password.txt  — 开始

更多的参数说明：
@ hashcat解压到桌面
然后在下载john the ripper解压到桌面  
打开john选择run文件夹把需要破解加密的文件夹拖进去“重命名成英文”然后在路径里面输入 cmd 进入输入rar2john.exe 破解文件名.rar –获取hash值
将获取hash值复制到记事本然后直接关闭终端 打开hashcat文件夹 在路径直接输入cmd hashcat.exe -m 13000 -w 4 -a 3 将记事本保存代码粘贴进来 -o password.txt 然后把代码全部复制进去cmd敲一下回车 按一下s键可以看的到刷新介面看到刷新状态  破解成功后打开hashcat文件夹找到password.txt打开结尾；就是密码


#

针对Word密码的命令：


python office2john.py test.docx                 获取word加密文件的Hash指令(此处需要安装python并配置环境变量)
test.docx:$office$*2013*100000*256*16*561f4dcaaac333e7c06d150f9ea5aea2*ef4e7b026217124561ecb865b324eac4*e9ef4a859f2c81581db0e27d9ce48e6451b82cd1641941e8adc10dc5600969cb                                所得Hash返回结果
hashcat.exe -m 9600 -a 3 $office$*2013*100000*256*16*561f4dcaaac333e7c06d150f9ea5aea2*ef4e7b026217124561ecb865b324eac4*e9ef4a859f2c81581db0e27d9ce48e6451b82cd1641941e8adc10dc5600969cb ?d?d?d?d -o out.txt                 Hashcat破解对应hash
针对PDF密码的命令：

#
#



perl pdf2john.pl test.pdf                       获取pdf加密文件的Hash指令(此处需要安装perl并配置环境变量)
test.pdf:$pdf$4*4*128*-3904*0*16*55f913d20e34724fd70d3004f5e43166*32*7a29310ea5dc0276d34c1bef24595d61984a08eb759eaba56bd4887a260bbcce*32*de0c200bbe6887a980dc429edbdabc40f39a368841d804afefa726b2bd7c7b24   所得Hash返回结果
hashcat.exe -m 10500 -a 3 $pdf$4*4*128*-3904*0*16*55f913d20e34724fd70d3004f5e43166*32*7a29310ea5dc0276d34c1bef24595d61984a08eb759eaba56bd4887a260bbcce*32*de0c200bbe6887a980dc429edbdabc40f39a368841d804afefa726b2bd7c7b24 ?l?l?l?l?l?l -o out.txt  Hashcat破解对应hash，此处?l对应一个小写字母

#
#



针对Zip密码的命令：


zip2john.exe test.zip                            获取zip加密文件的Hash指令
test.zip/test.txt:$pkzip2$1*1*2*0*15*9*4aac42f3*0*26*0*15*4aac*470b*6fa72c2bc69e5738181cb7f406187f8084ce07cf5f*$/pkzip2$:test.txt:test.zip::test.zip                                              所得Hash返回结果
hashcat -a 0 -m 17210 $pkzip2$1*1*2*0*15*9*4aac42f3*0*26*0*15*4aac*470b*6fa72c2bc69e5738181cb7f406187f8084ce07cf5f*$/pkzip2$ password.txt --force
    password.txt中存放密码字典

 

#

提醒：运行John the Ripper需要安装python和perl环境变量，如果命令出错，请自行下载安装python和perl

perl：http://www.activestate.com/activeperl
python：https://www.python.org


#


#-m 指定要破解的hash类型，如果不指定类型，则默认是MD5

-a 指定要使用的破解模式，其值参考后面对参数。-a 0〞 字典攻击，"-a 1"组合攻击; “-a3〞 掩码攻击。

-o。指定破解成功后的hash及所对应的明文密码的存放位置,可以用它把破解成功的hash写到指定的文件中


#

YouTube教程  https://m.youtube.com/watch?v=ifrpYn_Gm54&feature=youtu.be
