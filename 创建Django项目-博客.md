1. 创建项目
   要求:项目必须在当前文件夹下
   1.可以用命令：(venv) E:\my_blog\blog_10>django-admin help打开帮助（django-admin.py是一切的开始）
        Type 'django-admin help <subcommand>' for help on a specific subcommand.

            Available subcommands:

            [django]
                check
                compilemessages
                createcachetable
                dbshell
                diffsettings
                dumpdata
                flush
                inspectdb
                loaddata
                makemessages
                makemigrations
                migrate
                runserver
                sendtestemail
                shell
                showmigrations
                sqlflush
                sqlmigrate
                sqlsequencereset
                squashmigrations
                startapp
                startproject    #创建一个项目 *+项目名称
                test
                testserver
            Note that only Django core commands are listed as settings are not properly configured (error: Requested setting INSTALLED_APPS, but settings are not configured. You
            must either define the environment variable DJANGO_SETTINGS_MODULE or call settings.configure() before accessing settings.).
    2.(venv) E:\my_blog\blog_10>django-admin.py help startproject查看startproject下的帮助命令
        usage: django-admin.py startproject [-h] [--template TEMPLATE]
                                    [--extension EXTENSIONS] [--name FILES]
                                    [--version] [-v {0,1,2,3}]
                                    [--settings SETTINGS]
                                    [--pythonpath PYTHONPATH] [--traceback]
                                    [--no-color]
                                    name [directory]  # 项目的名称 + 目录（指定在哪个目录下创建项目）
    例如：在当前目录下创建项目blog：(venv) E:\my_blog\blog_10>django-admin startproject blog .（.表示当前目录）

    3.项目目录如下：
    blog
         __init__.py:
        settings.py:做全局配置的。本项目的配置文件。数据库参数等
        urls.py:做路由用的，路由是：解决URL与某函数对应用的。URL路径映射配置。默认下，只配置/admin的路由。
        wsgi.py:定义wsgi接口信息，一般无需改动。
    manage.py:项目内创建的所有子命令都是由此文件来开始管理命令，用来管理。应用创建、数据库迁移等都使用它完成。
    3.数据库配置
    在settings.py中修改默认数据库
    DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'blog',
        'USER': 'root',
        'PASSWORD': 'wangjiong',
        'HOST': 'localhost',
        'PORT': '3306',
                }
            }
    4.安装数据库驱动
    pip install mysqlclient
2. 创建应用
    创建用户应用：(venv) E:\my_blog\blog_10>python manage.py startapp user
    注册应用：在settings.py文件中增加user应用。目的为了后台管理admin使用，或迁移migrate使用。
    INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'user',
    ]
3. 模型（model）
   创建user的model类

