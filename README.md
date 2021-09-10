## 安装 matplotlib 命令
Linux  
```
pip install --upgrade pip
pip install django
```

Windows  
红线处 al + enter 自动下载包

# 创建项目

django-admin startproject learning_log .

注意：千万别忘了这个句点，否则部署应用时将遭遇一些配置问题。如果忘记了这个句点，
要删除已创建的文件和文件夹，再重新运行这个命令。

## 说明
**manage.py**

是一个简单的程序，接受命令并将其交给 Django 的相关部分运行。
我们将使用这些命令来管理使用数据库和运行服务器等任务。
目录 learning_log 包含 4 个文件

**settings.py:**

指定 Django 如何与系统交互以及如何管理项目。在开发项目的过程中，
我们将修改其中一些设置，并添加一些设置。

**urls.py**

告诉 Django，应创建哪些页面来响应浏览器请求。

**wsgi.py**

帮助 Django 提供它创建的文件，这个文件名是 Web 服务器网关接口(Web Server Gateway interface)
的首字母缩写

# 创建数据库
```
python manage.py migrate
```
会创建一个 db.sqlite3 文件
SQLite 是一种使用单个文件的数据库，是编写简单应用程序的理想选择，因为它让你不用太关注数据库管理问题。

# 运行项目
```
python manage.py runserver
```
默认使用 8000 端口，如果被占用，使用命令
```
python manage.py runserver 8001
```

# 创建应用程序 learning_logs
```
python manage.py startapp learning_logs
```
命令 startapp appname 让 Django 搭建创建应用程序所需的基础设施。如果限制查看目录，将看到其中新增了
learning_logs 目录，其中最重要的文件是 models.py、admin.py 和 views.py。
我们将使用 models.py 来定义要在应用程序中管理的数据

## 让 Django 修改数据库
```
python manage.py makemigrations learning_logs
```
命令 makemigrations 让 Django 确定该如何修改数据库，使其能够存储与前面定义的新模型相关联的数据。
输出表明 Django 创建了一个名为 0001_initial.py 的迁移文件，这个文件将在数据库中为模型 Topic 创建一个表。

下面应用这种迁移，让 Django 替我们修改数据库：
```
python manage.py migrate
```
这个命令的大部分输出与首次执行命令 migrate 的输出相同。
每当需要修改“学习笔记”管理的数据时，都采取如下三个步骤：
修改 models.py，对 learning_logs 调用 makemigrations，以及让 Django 迁移项目。

## Django 管理网站
### 创建超级用户
```
python manage.py createsuperuser
```
username:admin

password:123456

## Django shell
输入一些数据后，就可以通过交互式终端会话以编程方式查看这些数据了。这种交互式环境称为 Django shell，
是测试项目和排除故障的理想之地。下面是一个交互式 shell 会话示例：
```
(venv) ~/.../python/learning_log >>> python manage.py shell                                                                                                         ±[●●●][master]
Python 3.9.6 (default, Jun 30 2021, 10:22:16)
[GCC 11.1.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from learning_logs.models import Topic
>>> Topic.objects.all()
<QuerySet [<Topic: Chess>, <Topic: Rock Climbing>]>
>>> topics = Topic.objects.all()
>>> for topic in topics:
...   print(topic.id, topic)
...
1 Chess
2 Rock Climbing
>>> t = Topic.objects.get(id=1)
>>> t.text
'Chess'
>>> t.date_added
datetime.datetime(2021, 9, 6, 7, 39, 41, 252224, tzinfo=<UTC>)
>>> t.entry_set.all()
<QuerySet [<Entry: Entry object (1)>]>
```
按 Ctrl + D 退出 shell。如果是 Windows 系统，应按 Ctrl + Z，再按回车键。

# 创建应用程序 users
```
python manage.py startapp users
```

# 安装 django-bootstrap4
```
pip install django-bootstrap4
```