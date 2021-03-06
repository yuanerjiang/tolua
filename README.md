## tolua#

tolua# is a Unity lua static binder solution. the first solution that analyzes code by reflection and generates wrapper classes.

It is a Unity plugin that greatly simplifies the integration of C# code with Lua. which can automatically generate the binding code to access Unity from Lua and map c# constants, variables, functions, properties, classes, and enums to Lua.

tolua# grows up from cstolua. it's goal is to be a powerful development environment for Unity.

Support unity4.6.x and Unity5.x all(copy /Unity5.x/Assets to /Assets)

If you want to test in mobile, first click menu Lua/Copy lua files to Resources. then build it

如果你想在手机上测试，首先点击菜单Lua/Copy lua files to Resources， 之后再build.

有bug 可以到QQ群反馈: 286510803. 不闲聊，非bug相关不要加群, 请加讨论群: <br>
ulua&tolua技术交流群① 341746602(已满) <br>
ulua_tolua技术讨论群② 469941220 <br>
ulua&tolua技术交流群3 434341400(已满) <br>
tolua#技术讨论群④ 543826216<br>

# Library
**Debugger** <br>
https://github.com/topameng/Debugger

**tolua_runtime** <br>
https://github.com/topameng/tolua_runtime

# FrameWork and Demo
**LuaFrameWork**<br>
https://github.com/jarjin/LuaFramework_NGUI <br>
https://github.com/jarjin/LuaFramework_UGUI <br>
**XlsxToLua**<br>
https://github.com/zhangqi-ulua/XlsxToLua<br>
**UnityHello**<br>
https://github.com/woshihuo12/UnityHello<br>
**UWA-ToLua**<br>
http://uwa-download.oss-cn-beijing.aliyuncs.com/plugins%2FiOS%2FUWA-iOS-ToLua.zip<br>
**unity_tolua-_zerobrane_api**<br>
https://github.com/LabOfHoward/unity_tolua-_zerobrane_api

# Packages
　**Basics**　　　　　　　　**Math**　　　　　　**Data Structures**<br>
　luabitop　　　　　　　Quaternion　　　　　　　list<br>
　 struct　　　　　　　 　Vector3　　　　　　　　event<br>
　 int64　　　　 　　　  　Vector4　　　　　　　　slot<br>
　 Time　　　　 　　　  　Vector2<br>
**Networking**　　　　 　　　Ray<br>
　luasocket　　　　 　　　 Color<br>
　**Parsing**　　　　 　　　Bounds<br>
　lpeg　　 　　 　　　 　  　Mathf<br>
　**Protol**　　　　　 　 　　 Touch<br>
　pblua　　　 　　 　 　RaycastHit<br>
# 关于反射
tolua# 不支持动态反射。对于重载函数有参数匹配问题，函数排序问题，ref ,out 参数问题等等，动态反射会有各种问题。<br>
tolua#提供的替换方法是:<br>
1. preloading, 把你未来可能需要的类型添加到导出列表customTypeList，同时也添加到dynamicList列表中，这样导出后该类型并不会随binder注册到lua中，你可以通过 require "namespace.classname" 动态注册到lua中，对于非枚举类型tolua#系统也可以在第一次push该类型时动态载入，当然也可在过场动画、资源下载、登录、场景加载或者某个的函数中require这个类型。<br>
2. 1.0.5 版本开始加入静态反射，参考例子22。通过静态反射支持精确的函数参数匹配和类型检查。不会存在重载函数参数混乱匹配错误问题
　
# Performance
|   平台    |   属性读写   | 重载函数  | Vector3构造 |GameObject构造|Vector3归一化|Slerp|
| :-- 		| :-----------:|:---------:| :---------: |:-----------: |:----------: |:--: |
| PC  		|  0.0465:0.15 | 0.076:0.19|0.02:0.001   |0.1:0.14		|0.014:0.001  |0.10:0.11|
| Android   |   0.26:1.03  | 0.39:1.15 |0.2:0.0049   |0.43:0.5		|0.27:0.02	  |0.49:0.16|
| iOS       |  0.04:0.145  | 0.055:0.146 |0.017:0.05   |0.074:0.08	|0.035:0.11	  |0.078:0.58|

测试结果为C#:Lua. 环境不同会略有差异。可用数字倍率做参考<br>
PC: Intel(R) Core(TM) i5-4590 CPU@3.3GHz + 8GB + 64 位win7<br>
Android: 中兴nubia z9 max(NX512J) + Adnroid5.0.2<br>
iOS(il2cpp): IPhone6 Plus<br>
# Examples
参考包内1-20例子

# About Lua
win, android ios using luajit2.1-beta2. macos using luac(for u5.x). 
