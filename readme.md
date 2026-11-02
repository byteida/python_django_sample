# Windows + VS Code + Python + Django 环境搭建

下面从零开始搭建一套 Windows Django 开发环境。完成后，你可以在 VS Code 中编写 Python、运行 Django、调试代码，并访问本地 Web 页面。

适合初学者 Windows 10 / 11

## 一、需要安装的软件

一共需要 3 个核心软件：

The Python Programming Logo: A Symbol Of Innovation And Community – peerdh.com

1. Python

Python 3.13 或 3.14，建议使用稳定版本

[下载 Python](<https://www.python.org/downloads/windows/?utm_source=chatgpt.com>)

File:Visual Studio Code 1.35 icon.svg - Wikimedia Commons

2. Visual Studio Code

代码编辑器

[下载 VS Code](<https://code.visualstudio.com/Download?utm_source=chatgpt.com>)

Logo Git – Logos PNG

3. Git（可选但推荐）

代码版本管理、连接 GitHub

[下载 Git](<https://git-scm.com/downloads/win?utm_source=chatgpt.com>)

## 二、安装 Python

1. 打开 [Python 官网](<https://www.python.org/downloads/windows/?utm_source=chatgpt.com>)。
2. 下载 Python 3.13 或 3.14 的 Windows 64-bit 安装包。
3. 运行安装程序。

Python 3.14をインストールしよう（Windows11 編） - Python学習チャンネル by PyQ

[blog.pyq.jp](<https://blog.pyq.jp/entry/python_install_251022_win?utm_source=chatgpt.com>)

重点：安装时勾选：

`Add python.exe to PATH`

然后点击 Install Now。

安装完成后，打开 Windows PowerShell，输入：

powershell

```powershell
python --version
```

再输入：

powershell

```powershell
py --version
```

如果显示 Python 版本号，说明安装成功。

## 三、安装 VS Code 和 Python 插件

下载并安装 VS Code：

[VS Code 官方下载](<https://code.visualstudio.com/Download?utm_source=chatgpt.com>)

打开 VS Code，点击左侧 Extensions（扩展），搜索并安装：

VS Code Windows — документация axipy 7.0

Python

Microsoft 官方扩展

必装

VS Code Update Boosts Python IntelliSense -- Visual Studio Magazine

Pylance

代码提示、类型检查

推荐

【Django環境構築】Python・VSCode・Djangoのインストールと初期設定完全ガイド - Django 6入門チュートリアル｜実践ブログ開発で学ぶWeb開発 | Techarm Blog

Django

Django 模板语法支持

可选

官方参考：[VS Code Python 开发教程](<https://code.visualstudio.com/docs/python/python-tutorial?utm_source=chatgpt.com>)

## 四、创建 Django 项目

这里以 `D:\python_projects` 作为项目存放目录。

### 1. 创建项目文件夹

打开 VS Code，选择：

`File → Open Folder`

新建并打开：

text

```text
D:\python_projects\django_demo
```

### 2. 打开 VS Code 终端

快捷键：

text

```text
Ctrl + `
```

选择 PowerShell。

### 3. 创建 Python 虚拟环境

在终端执行：

powershell

```powershell
python -m venv .venv
```

项目目录下会生成：

text

```text
django_demo/
└── .venv/
```

虚拟环境的作用是隔离每个项目的 Python 依赖，避免不同项目之间产生版本冲突。

### 4. 激活虚拟环境

PowerShell 执行：

powershell

```powershell
.\.venv\Scripts\Activate.ps1
```

成功后，终端前面会出现：

text

```text
(.venv) PS D:\python_projects\django_demo>
```

如果提示禁止运行脚本，可以在当前 PowerShell 窗口执行：

powershell

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

然后重新激活。

### 5. VS Code 选择 Python 解释器

按下：

text

```text
Ctrl + Shift + P
```

输入：

text

```text
Python: Select Interpreter
```

选择：

text

```text
.venv\Scripts\python.exe
```

Getting Started with Python in VS Code

[code.visualstudio.com](<https://code.visualstudio.com/docs/python/python-tutorial?utm_source=chatgpt.com>)

这样 VS Code 就会使用当前 Django 项目的独立 Python 环境。

### 6. 安装 Django

powershell

```powershell
python -m pip install --upgrade pip

python -m pip install django
```

检查 Django 是否安装成功：

powershell

```powershell
python -m django --version
```

也可以检查：

powershell

```powershell
pip list
```

## 五、创建第一个 Django Web 项目

在 VS Code 终端执行：

powershell

```powershell
django-admin startproject config .
```

注意最后有一个点 `.`，表示在当前目录创建项目，而不是额外嵌套一层目录。

此时项目结构：

text

```text
django_demo/
│
├── .venv/
│
├── config/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
└── manage.py
```

### 启动 Django

先初始化数据库：

powershell

```powershell
python manage.py migrate
```

启动 Web 服务：

powershell

```powershell
python manage.py runserver
```

启动成功终端会显示类似：

text

```text
Starting development server at
http://127.0.0.1:8000/
```

打开浏览器：

[http://127.0.0.1:8000/](<http://127.0.0.1:8000/?utm_source=chatgpt.com>)

就能看到 Django 欢迎页面。

How to Install Django | LearnDjango.com

[learndjango.com](<https://learndjango.com/tutorials/how-install-django?utm_source=chatgpt.com>)

## 六、创建一个 Hello World 页面

继续创建一个应用：

powershell

```powershell
python manage.py startapp hello
```

项目结构变成：

text

```text
django_demo/
│
├── .venv/
├── config/
│   ├── settings.py
│   └── urls.py
│
├── hello/
│   ├── migrations/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
│
└── manage.py
```

### 1. 编写 views.py

打开 `hello/views.py`：

python

```python
from django.http import HttpResponse


def index(request):
    return HttpResponse("Hello Django!")
```

### 2. 创建 hello/urls.py

python

```python
from django.urls import path
from . import views

urlpatterns = [
    path("", views.index, name="index"),
]
```

### 3. 修改 config/urls.py

python

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path("admin/", admin.site.urls),
    path("hello/", include("hello.urls")),
]
```

### 4. 启动服务

powershell

```powershell
python manage.py runserver
```

打开：

[http://127.0.0.1:8000/hello/](<http://127.0.0.1:8000/hello/?utm_source=chatgpt.com>)

页面显示：

浏览器运行结果

# Hello Django\!

HTTP 200 OK

## 七、配置 Django Admin 后台

Django 自带管理后台，不需要额外安装。

创建管理员：

powershell

```powershell
python manage.py createsuperuser
```

根据提示填写：

- Username：管理员账号
- Email：邮箱
- Password：管理员密码

启动服务：

powershell

```powershell
python manage.py runserver
```

访问：

[http://127.0.0.1:8000/admin/](<http://127.0.0.1:8000/admin/?utm_source=chatgpt.com>)

使用刚才创建的账号登录，就能看到 Django 管理后台。

## 八、保存项目依赖

后续项目上传 GitHub 或换电脑时，需要能够重新安装依赖。

生成 `requirements.txt`：

powershell

```powershell
pip freeze > requirements.txt
```

以后安装项目依赖：

powershell

```powershell
pip install -r requirements.txt
```

建议创建 `.gitignore`：

gitignore

```gitignore
.venv/
__pycache__/
*.pyc
db.sqlite3
.env
.vscode/
```

## 九、最终项目结构

完成上述步骤后：

text

```text
django_demo/
│
├── .venv/                  # Python 虚拟环境
│
├── config/                 # Django 项目配置
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── hello/                  # Django 应用
│   ├── migrations/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── views.py
│   └── urls.py
│
├── manage.py
├── requirements.txt
└── .gitignore
```

## 十、常用命令速查

| 操作 | 命令 |
| --- | --- |
| 创建虚拟环境 | `python -m venv .venv` |
| 激活环境 | `.\.venv\Scripts\Activate.ps1` |
| 安装 Django | `pip install django` |
| 查看 Django 版本 | `python -m django --version` |
| 创建项目 | `django-admin startproject config .` |
| 创建应用 | `python manage.py startapp hello` |
| 启动服务 | `python manage.py runserver` |
| 创建数据库迁移 | `python manage.py makemigrations` |
| 执行数据库迁移 | `python manage.py migrate` |
| 创建管理员 | `python manage.py createsuperuser` |
| 导出依赖 | `pip freeze > requirements.txt` |

## 十一、官方学习资料

- [Django 官方文档](<https://docs.djangoproject.com/en/6.1/?utm_source=chatgpt.com>)
- [VS Code + Django 官方教程](<https://code.visualstudio.com/docs/python/tutorial-django?utm_source=chatgpt.com>)
- [微软 Django 入门 GitHub 项目](<https://github.com/microsoft/python-sample-vscode-django-tutorial?utm_source=chatgpt.com>)
- [Django 官方 GitHub 源码](<https://github.com/django/django?utm_source=chatgpt.com>)

参考：

Django

+3

## 十二、下一步建议

环境搭建完成后，我建议按照下面顺序学习：

1. Django 基础
   URL、View、Template、项目结构
2. 数据库开发
   Model、ORM、SQLite、MySQL、PostgreSQL
3. 后台管理
   Admin、用户管理、权限管理
4. REST API
   Django REST Framework、Serializer、JWT
5. 完整项目实战
   登录注册、增删改查、分页、搜索、文件上传

建议下一步直接做一个 Django + SQLite 的 CRUD 学习项目，从环境、数据库、页面到接口全部跑通。

A step-by-step solution for the official Django tutorial
https://github.com/consideratecode/django-tutorial-step-by-step