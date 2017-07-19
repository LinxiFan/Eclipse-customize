========= Eclipse updates site =============
PyDev: http://pydev.org/updates
CDT: http://download.eclipse.org/tools/cdt/releases/kepler
Vrapper: http://vrapper.sourceforge.net/update-site/stable
EclipseFP (Haskell): http://eclipsefp.sf.net/updates
Cusp (Lisp): http://www.sergeykolos.com/cusp/update/
ProDT (Prolog): http://sewiki.iai.uni-bonn.de/public-downloads/update-site-pdt/
WebTools (XML, JavaScript, etc): http://download.eclipse.org/webtools/repository/juno/
Matclipse: http://matclipse.eclipselabs.org.codespot.com/git.update/
JadClipse: http://jadclipse.sf.net/update
Eclipse chrome theme: https://raw.github.com/jeeeyul/eclipse-themes/master/net.jeeeyul.eclipse.themes.updatesite/
Eclipse background: http://eclipse-color-theme.github.com/update
GLSL openGL shading language: http://sourceforge.net/p/glshaders/wiki/Home/
(manual download unzip and copy to plugin folder, right click a shader file -> editor open with -> Cg Editor -or- GLSL Editor)
JavaOperatorOveroading: http://amelentev.github.io/eclipse.jdt-oo-site/

===================================
After installing JDK/JRE,
If you want to let mouse hovering show javadoc, you must config and set the installation dir to JDK instead of JRE
Preferences -> Java -> Installed JREs -> jre8 -> Edit -> JRE home -> C:\Program Files\Java\jdk1.8.0

--------------------------------------------
Install plugin from .jar files:
Copy the .jar to plugin folder
restart eclipse using command line, with eclipse.exe -clean
to clean the cache and make sure Eclipse sees the new plugin

Change Eclipse Workspace
Window -> Preferences -> General -> Startup and Shutdown -> Workspaces

----------------------------------------------
Set environment variables (only 3 needed)
JAVA_HOME = C:/Program Files/Java/jdk1.7....
path=%JAVA_HOME%/bin
CLASSPATH=%JAVA_HOME%/lib/dt.jar; %JAVA_HOME%/lib/tools.jar

If javac compiles a simple java program successfully, then environment is good. 

----------------------------------------------
Eclipse preference
1. change workspace 
All settings are stored in the .metadata/.plugins/org.eclipse.core.runtime/.settings directory
I mean -- all relevant settings. If you look into .metadata/.plugins directory there are many more directories with settings, but they are too project specific.

2. Import/Export plugins
http://help.eclipse.org/indigo/index.jsp?topic=/org.eclipse.pde.doc.user/guide/tools/import_wizards/import_plugins.htm

-----------------------------------------------
Create far jars
Right click project -> Export -> Runnable JAR file -> "Copy required libs into a sub-folder ..."
Then use JarSplice.jar to create an exe/fat jar. 

-----------------------------------------------
Ctrl+Shift+F changes indentation style
if (true){
}
to 
if (true)
{
}

Ctrl+Shift+G show all references to a class
-----------------------------------------------
Java native locations:
You can simply copy the *.dll to the whole project's folder and no need to specify it under "native location" in "Build Path" menu.

-----------------------------------------------
Eclipse LUNA new features:
Ctrl + { 	horizontal split
Ctrl + _	vertical split
TFC terminal (install from luna official update site)

-----------------------------------------------
Eclipse vim settings:
edit C:\Users\Jim\_vrapperrc

----------------------------------------------
Eclipse change Javadoc tag @author default:
in the eclipse install folder -> eclipse.ini -> add line:
-Duser.name=Jim Fan  (c) 2014

----------------------------------------------

如何运行.php:
1. XAMPP的Apache必须运行于后台！！！如果运行不了，试着重启电脑
2. Eclipse里，Window -> Preference -> PHP server -> Edit default server: local webroot: XXX/xampp/htdocs
Path on server和local path都写成 XXX/xampp/htdocs/ProjectFolder
3. Window -> Preference -> PHP executable -> 新建一个PHPexe然后添加php.exe的路径，在xampp/php/php.exe里

SQL:
 http://localhost/phpmyadmin/ 里面新建db。可以参考youtube教程
 Open perspective -> database development
 配置JDBC driver
 Connection: jdbc:mysql://localhost:3306/《database》用数据库名字替换掉
 然后设置见：http://obscuredclarity.blogspot.com/2009/08/setup-mysql-development-in-eclipse.html

===============================

如何把图片bundle在Jar里：
images这个文件夹必须在src文件夹*里面*！！！
然后为了成功access，需要（比如说SystemTray的TrayIcon）
trayIcon = new TrayIcon(new ImageIcon(TrayIcon.class.getResource("/images/warning.gif")).getImage());
其他的class可以用 getClass().gerResource("/一定要有slash/....avi");
对于text，只能read-only的读取。new Scanner(getClass().gerResourceAsStream("/text/config.txt"));
往src文件夹里添加完新的resource之后勿忘刷新一下Project！！！


如何生成英文Javadoc (默认中文)
右键某一个项目，Export --> JavaDoc --> 点三次Next之后会有一个VM Param --> 输入 -locale en_US --> Finish

把workbench中已经有的project导入到eclipse workspace中：
New Java Project --> 打字打入完全相同的project名 --> 自动导入


更改默认的code/comment template:
Window --> Preferences --> Java -->Code Style --> Code Template
更改默认的格式
以上菜单Code style --> Formatter 此处还可以把自己的configuration保存成profile
更改Error/Warning的情况：
Preferences --> Java --> Compiler --> Errors/Warnings

不要用硬Tab！！！要换成space！！！
Preferences -> General -> Editors -> Text Editors -> Insert spaces for tabs


如何import下载的Library
每个lib最好有三个东西：Bin (.jar) & source files (.jar or .zip) & javadoc (.jar or .zip)
如果源文件中无source, 则可以用jd-gui提取
从src.zip中获得javadoc: 先解压src.zip
在Eclipse里新建New Java Project --> 输入proj name --> uncheck the box "use default location" --> Browse, 选择那个还有src的文件夹
然后 主菜单Project --> Generate javadoc --> select前面创建的这个proj --> finish --> 生成一个doc的文件夹 --> 压缩为xxx-doc.zip即可

有了以上三样东西之后，开始import lib:
windows --> preferences --> java--> build path--> user library--> New 弹出对话框，勾选System Library
create完毕之后，点黑前面创建的lib, 按右边“add jars”--> 选择jar (external)
拉开前面那个项，source attachment --> Edit --> external archive --> src.zip browse一下
"Javadoc location (None)"--> javadoc in archive --> external file browse --> Done

要在自己的某个proj中插入lib,
右击自己的那个java project --> build path --> add libraries

方法二：如果一次性的lib，不想添加到eclipse系统中，则可以直接右击project name --> build path--> add external archives --> 然后就有“Referenced lib”了

如何collapse all code blocks:
右击左侧蓝色边框 菜单--> Folding --> collapse all


如何assertion check:
代码：assert somenumber ≥ 0;
在eclipse中运行：菜单Run --> Run configuration --> 左上角小图标New --> [Tab] (x)=argument --> VM arguments里输入“-ea”--> 点Apply, 然后run即可


JUnit Testing:
@Test

如何去除interface里自动生成的@override字样：
Preferences --> Java --> Code Style --> 去除“add @override...”这个勾
