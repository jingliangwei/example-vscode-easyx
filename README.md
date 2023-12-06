# example-vscode-easyx
一个在vscode中使用easyx的例子（需提前配置好easyx图形库）  
这是我第一个在vscode上成功运行的使用easyx的c++代码，留作备份以供参考。  
对参考文章的作者表示感谢，如有侵权，请联系我删除。

文档中的tasks.json文档是只能对单文件进行编译的，如果想对多文件同时编译，则需要把里面的内容改为以下内容：

```cpp
{
    "tasks": [
        {
            "type": "shell",
            "label": "C/C++: cl.exe 生成活动文件",
            "command": "cl.exe",
            "args": [
                "/Zi",
                "/EHsc",
                "kernel32.lib",//这里开始
				"gdi32.lib",
				"winspool.lib",
				"comdlg32.lib",
				"advapi32.lib",
				"shell32.lib",
				"ole32.lib",
				"oleaut32.lib",
				"uuid.lib",
				"odbc32.lib",
				"odbccp32.lib",
				"user32.lib",//这里结束
                "/nologo",
                "/Fe${fileDirname}\\${fileBasenameNoExtension}.exe",
                "C:\\visual studio code\\neweasyx\\*.cpp"    //更改的地方
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": [
                "$msCompile"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "detail": "调试器生成的任务。"
        }
    ],
    "version": "2.0.0"
}
```


## 参考文章：
[VSCode配置MSVC+VSCode使用easyx库,2021.5.13日配置~~](https://www.cnblogs.com/zaunekko/p/14774675.html)
