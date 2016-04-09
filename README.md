
#**Sublime编译环境配置** && **常用插件**

####[环境配置文件](https://github.com/Aaron-Lea/sublime-setting)
####[常用插件](https://github.com/Aaron-Lea/sublime-setting/archive/master.zip)

###**Java环境配置**
####新建runJava.bat文件放入jdk\bin中
代码如下:
>@ECHO OFF 
>cd %~dp1 
>ECHO Compiling %~nx1……
>IF EXIST %~n1.class ( 
>?DEL %~n1.class 
>) 
>javac %~nx1 
>IF EXIST %~n1.class ( 
>ECHO ———OUTPUT———
>java %~n1 
>)

###sublime->Tools->Build System->new Build System
####文件名保存为JavaC..sublime-build 
代码如下：
>{
>  "shell_cmd": "runJava.bat \"$file\"",
>  "file_regex": "^(...*?):([0-9]*):?([0-9]*)",
>  "selector": "source.java",
>  "encoding": "UTF-8"
>}

###**Sublime中CPP环境配置**
####系统的*g++ $ gcc*配置略
#####sublime->Tools->Build System->new Build System
######文件名保存为C++.sublime-build
代码如下：
>{
>    "cmd": ["g++", "${file}", "-o", "${file_path}/${file_base_name}"],
>    "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
>    "working_dir": "${file_path}",
>    "selector": "source.c, source.c++",
>    "encoding":"UTF-8",
>    "variants":
>    [
>       {
>            "name": "Run", 
>            "shell": true,
>            "cmd" : ["start", "cmd", "/k", "${file_path}/${file_base_name} &&echo. & pause && exit"] 
>        }
>    ]
>}

###**Sublime中Python环境配置**
####sublime->Tools->Build System->new Build System
#####文件名保存为 Python.sublime-build 
代码如下：
>{
>    "cmd": ["python", "-u", "$file"],
>    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
>    "selector": "source.python",
>   "encoding":"utf-8",
>    "variants": 
>    [
>        {
>            "name": "Run", 
>            "shell": true,
>            "cmd" : ["start", "cmd", "/k", "python", "${file_path}/${file_base_name}.py"] 
>        }
>    ]
>}

###**Sublime中Ruby环境配置**
####sublime->Tools->Build System->new Build System
#####文件名保存为 Ruby.sublime-build 
代码如下：
>{
>    "cmd": ["ruby", "$file"],
>    "file_regex": "^(...*?):([0-9]*):?([0-9]*)",
>    "selector": "source.ruby",
>    "encoding":"utf-8",
>    "variants": 
>    [
>        {
>            "name": "Run", 
>            "shell": true,
>            "cmd" : ["start", "cmd", "/k", "ruby", "${file_base_name}.rb"] 
>        }
>    ]
>}
