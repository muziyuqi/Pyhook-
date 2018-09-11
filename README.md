
到哪找.whl文件？
http://www.lfd.uci.edu/~gohlke/pythonlibs/

把文件最好放在\Script文件夹里面再pip install xxxx.whl


注意whl文件名不能改 必须一模一样和原名



报错： pyHook-1.5.1-cp37-cp37m-win_amd64.whl is not a supported wheel on this platform.
原因是下载的pyhook版本与python版本不一致

import pip._internal
print(pip._internal.pep425tags.get_supported())


版本的含义
Win32 -> 指的就是Windows系统； 
64 bit- > 指的是Windows是64位的； 
AMD64 -> 指的就是 CPU是x64的
