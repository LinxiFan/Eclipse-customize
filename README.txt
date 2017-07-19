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

�������.php:
1. XAMPP��Apache���������ں�̨������������в��ˣ�������������
2. Eclipse�Window -> Preference -> PHP server -> Edit default server: local webroot: XXX/xampp/htdocs
Path on server��local path��д�� XXX/xampp/htdocs/ProjectFolder
3. Window -> Preference -> PHP executable -> �½�һ��PHPexeȻ�����php.exe��·������xampp/php/php.exe��

SQL:
 http://localhost/phpmyadmin/ �����½�db�����Բο�youtube�̳�
 Open perspective -> database development
 ����JDBC driver
 Connection: jdbc:mysql://localhost:3306/��database�������ݿ������滻��
 Ȼ�����ü���http://obscuredclarity.blogspot.com/2009/08/setup-mysql-development-in-eclipse.html

===============================

��ΰ�ͼƬbundle��Jar�
images����ļ��б�����src�ļ���*����*������
Ȼ��Ϊ�˳ɹ�access����Ҫ������˵SystemTray��TrayIcon��
trayIcon = new TrayIcon(new ImageIcon(TrayIcon.class.getResource("/images/warning.gif")).getImage());
������class������ getClass().gerResource("/һ��Ҫ��slash/....avi");
����text��ֻ��read-only�Ķ�ȡ��new Scanner(getClass().gerResourceAsStream("/text/config.txt"));
��src�ļ�����������µ�resource֮������ˢ��һ��Project������


�������Ӣ��Javadoc (Ĭ������)
�Ҽ�ĳһ����Ŀ��Export --> JavaDoc --> ������Next֮�����һ��VM Param --> ���� -locale en_US --> Finish

��workbench���Ѿ��е�project���뵽eclipse workspace�У�
New Java Project --> ���ִ�����ȫ��ͬ��project�� --> �Զ�����


����Ĭ�ϵ�code/comment template:
Window --> Preferences --> Java -->Code Style --> Code Template
����Ĭ�ϵĸ�ʽ
���ϲ˵�Code style --> Formatter �˴������԰��Լ���configuration�����profile
����Error/Warning�������
Preferences --> Java --> Compiler --> Errors/Warnings

��Ҫ��ӲTab������Ҫ����space������
Preferences -> General -> Editors -> Text Editors -> Insert spaces for tabs


���import���ص�Library
ÿ��lib���������������Bin (.jar) & source files (.jar or .zip) & javadoc (.jar or .zip)
���Դ�ļ�����source, �������jd-gui��ȡ
��src.zip�л��javadoc: �Ƚ�ѹsrc.zip
��Eclipse���½�New Java Project --> ����proj name --> uncheck the box "use default location" --> Browse, ѡ���Ǹ�����src���ļ���
Ȼ�� ���˵�Project --> Generate javadoc --> selectǰ�洴�������proj --> finish --> ����һ��doc���ļ��� --> ѹ��Ϊxxx-doc.zip����

����������������֮�󣬿�ʼimport lib:
windows --> preferences --> java--> build path--> user library--> New �����Ի��򣬹�ѡSystem Library
create���֮�󣬵��ǰ�洴����lib, ���ұߡ�add jars��--> ѡ��jar (external)
����ǰ���Ǹ��source attachment --> Edit --> external archive --> src.zip browseһ��
"Javadoc location (None)"--> javadoc in archive --> external file browse --> Done

Ҫ���Լ���ĳ��proj�в���lib,
�һ��Լ����Ǹ�java project --> build path --> add libraries

�����������һ���Ե�lib��������ӵ�eclipseϵͳ�У������ֱ���һ�project name --> build path--> add external archives --> Ȼ����С�Referenced lib����

���collapse all code blocks:
�һ������ɫ�߿� �˵�--> Folding --> collapse all


���assertion check:
���룺assert somenumber �� 0;
��eclipse�����У��˵�Run --> Run configuration --> ���Ͻ�Сͼ��New --> [Tab] (x)=argument --> VM arguments�����롰-ea��--> ��Apply, Ȼ��run����


JUnit Testing:
@Test

���ȥ��interface���Զ����ɵ�@override������
Preferences --> Java --> Code Style --> ȥ����add @override...�������
