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

# 创建应用程序
```
python manage.py startapp learning_logs
```
命令 startapp appname 让 Django 搭建创建应用程序所需的基础设施。如果限制查看目录，将看到其中新增了
learning_logs 目录，其中最重要的文件是 models.py、admin.py 和 views.py。
我们将使用 models.py 来定义要在应用程序中管理的数据

