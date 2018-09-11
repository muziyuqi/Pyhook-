
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


# -*- coding: utf-8 -*- # 
# by oldj http://oldj.net/ #  
 3import pythoncom 
 4import pyHook    
 5def onMouseEvent(event): 
    
   # 监听鼠标事件     
   print "MessageName:",event.MessageName     
   print "Message:", event.Message     
   print "Time:", event.Time     
   print "Window:", event.Window     
   print "WindowName:", event.WindowName     
   print "Position:", event.Position     
   print "Wheel:", event.Wheel     
   print "Injected:", event.Injected           
   print"---"
  
   # 返回 True 以便将事件传给其它处理程序     
   # 注意，这儿如果返回 False ，则鼠标事件将被全部拦截     
   # 也就是说你的鼠标看起来会僵在那儿，似乎失去响应了     
   return True
 
23def onKeyboardEvent(event):
  # 监听键盘事件     
   print "MessageName:", event.MessageName     
   print "Message:", event.Message     
   print "Time:", event.Time     
   print "Window:", event.Window     
   print "WindowName:", event.WindowName     
   print "Ascii:", event.Ascii, chr(event.Ascii)     
   print "Key:", event.Key     
   print "KeyID:", event.KeyID     
   print "ScanCode:", event.ScanCode     
   print "Extended:", event.Extended     
   print "Injected:", event.Injected     
   print "Alt", event.Alt     
   print "Transition", event.Transition     
   print "---"      
   # 同鼠标事件监听函数的返回值     
   return True 

42def main():     
   # 创建一个“钩子”管理对象     
   hm = pyHook.HookManager()      
   # 监听所有键盘事件     
   hm.KeyDown = onKeyboardEvent     
   # 设置键盘“钩子”     
   hm.HookKeyboard()      
   # 监听所有鼠标事件     
   hm.MouseAll = onMouseEvent     
   # 设置鼠标“钩子”     
   hm.HookMouse()      
   # 进入循环，如不手动关闭，程序将一直处于监听状态     
   pythoncom.PumpMessages() 

56if __name__ == "__main__":     
   main()
