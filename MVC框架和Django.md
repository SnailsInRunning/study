# MVC框架
1. M：即model（模型），指业务模型。 V：即view（视图），指用户界面。 C：controller(控制器)
   model：表示应用程序核心（比如数据库记录列表）。
   view：显示数据（数据库记录）。
   controller：处理输入（写入数据库记录）。
  model（模型）是应用程序中用于处理应用程序数据逻辑的部分。通常模型对象负责在数据库中存取数据。
  view（视图）是应用程序处理数据显示的部分。通常视图是依据模型数据创建的。
  controller（控制器）是应用程序中处理用户交互的部分。通常控制器负责从视图读取数据，控制用户输入，并向模型发送数据。
2. 使用MVC的目的是将M和V的实现代码分离，从而使同一个程序可以使用不同的表现形式。比如，一批统计数据可以分别用柱状图、饼图来表示。C存在的目的则是确保M和V的同步，一旦M改变，V应该同步更新。
3. 视图：是用户看到并与之交互的界面。MVC好处是它能为应用程序处理很多不同的视图。在视图中其实没有真正      的处理发生，不管这些数据是联机存储的还是一个雇员列表，作为视图来讲，它只是作为一种输出数据并允许用户    操纵的方式。
   模型：模型表示企业数据和业务规则。他拥有最多的处理任务。例如它可能用像EJBs和ColdFusion Components这样的构件对象来处理数据库，被模型返回的数据是中立的，就是说模型与数据格式无关，这样一个模型能为多个视图提供数据，由于应用于模型的代码只需写一次就可以被多个视图重用，所以减少了代码的重复性。
   控制器：接受用户的输入并调用模型和视图去完成用户的请求。所以当单击WEB页面中的超链接和发送HTML表单时，控制器本身不输出任何东西和做任何处理。他只是接受请求并决定调用哪个模型构件去处理请求，然后在确定用哪个视图来显示返回的数据。
4. 特点：
       优点：耦合性低、重用性高、生命周期成本低、部署快、可维护性高、有利于软件工程化管理。
       缺点：没有明确的定义、不适合小型/中性规模的应用程序、增加系统结构和实现的复杂性、视图和控制器间的过于紧密的连接、视图对模型数据的低效率的访问、一般高级的界面工具或构造器不支持模式。
#Django（Python Web框架）的MVC框架
1. Django是由Python语言写的一个开放源代码的web应用框架。是一个基于MVC构造的框架。但是在Django中，控制器接受用户输入的部分由框架自行处理，所以Django更关注的是MTV模式，即model（模型）、template（模板）和views（视图），他们各自的职责如下：
   模型：即数据存取层。  处理与数据相关的所有事务：如何存取、如何验证有效性、包含哪些行为以及数据之间的关系等。
   模板：即表现层。  处理与表现相关的决定：如何在页面或其他类型文档中进行显示。
   视图：即业务逻辑层  存取模型即调取恰当模板的相关逻辑。是模型与模板的桥梁。
  用户在浏览器中输入URL后的回车, 浏览器会对URL进行检查, 首先判断协议,如果是http就按照 Web 来处理, 然互调用DNS查询, 将域名转换为IP地址, 然后经过网络传输到达对应Web服务器, 服务器对url进行解析后, 调用View中的逻辑(MTV中的V), 其中又涉及到Model(MTV中的M), 与数据库的进行交互, 将数据发到Template(MTV中的T)进行渲染, 然后发送到浏览器中, 浏览器以合适的方式呈现给用户
2. Django的主要目的是简便、快速的开发数据库驱动的网站。它强调代码复用，多个组件可以很方便的以“插件”形式服务于整个框架，Django有许多功能强大的第三方插件，你甚至可以很方便的开发出自己的工具包。这使得Django具有很强的可扩展性。它还强调快速开发和DRY(Do Not Repeat Yourself)原则。
#创建Django项目
1. MVC框架
     模型： model  封装数据或对数据的处理方法
     视图： view   负责数据显示
     控制器： controller  负责收集从用户端的输入

     用户 --->controller(收集信息) --->model(数据库或文件)--->view--->HTML

2. 网络框架
   Django：2003年发布最成熟的web框架，开发文档全面；
   tornado：2009年发布 异步协程高并发机制；
   Flask: 2010年发布 微型项目
   Twisted：适用于传输层到协议的所有类型网络程序开发

3. 架构：
   Linux + NGINX + UWSGI

4. Django特点：
   1.Django的功能是最完整的；
   2.完善的文档；
   3.集成数据库访问组件；
   4.强大的URL技术；
   5.强大的后台。

5. Django的组成：
   1.管理工具：内置的Django站点维护命令工具。
   2.模型model：提供数据访问接口和模块
   3.视图view：URL绑定   模板绑定
   4.模板template：Django自己的模板渲染语言
   5.表单 Form ：通过类型和控件生成的HTML表单；
   6.管理站点admin：注册管理后台模块  生成后台页面。



#博客系统

    makemigrations  创建数据同步
    migrate         同步到数据库
    runserver       运行数据库
    shell
    showmigrations  看同步信息
    startapp
    startproject
#查看APP中有没有变化，命令：(venv) E:\Djangowj\venv\mysite>python manage.py makemigrations blog
   创建项目的命令：(venv) E:\Djangowj\venv\Scripts>django-admin startproject mysite
    创建新项目下有以下文件：
      mysite
          mysite
            __init__
            settings
            urls
            wsgi
      manage.py

      manage.py：一个实用的命令行，用来与你的项目进行交互。
      mysite/:项目目录，有以下的文件组成：
      init.py：一个空文件用来告诉python这个mysite目录是一个python模块(包)。
      settings.py:项目的设置和配置。里面包含一些初始化的设置（模块或包）。
      urls.py ：URL模式存放的地方。这里定义的每一个URL都映射一个视图。
      wsgi.py: 配置项目运行如同一个WSGI(web server gateway interface)应用。
2. 初始应用在数据库中建表
      默认生成的settings.py文件包含一个使用一个SQLite数据库的基础配置以及一个Django应用列表，这些应用会默认添加到项目中。
      我们需要为这些初始应用在数据库中建表。
      建表命令：(venv) E:\Djangowj\venv\mysite>python manage.py migrate
        Operations to perform:
          Apply all migrations: admin, auth, contenttypes, sessions
        Running migrations:
          Applying contenttypes.0001_initial... OK
          Applying auth.0001_initial... OK
          Applying admin.0001_initial... OK
          Applying admin.0002_logentry_remove_auto_add... OK
          Applying admin.0003_logentry_add_action_flag_choices... OK
          Applying contenttypes.0002_remove_content_type_name... OK
          Applying auth.0002_alter_permission_name_max_length... OK
          Applying auth.0003_alter_user_email_max_length... OK
          Applying auth.0004_alter_user_username_opts... OK
          Applying auth.0005_alter_user_last_login_null... OK
          Applying auth.0006_require_contenttypes_0002... OK
          Applying auth.0007_alter_validators_add_error_messages... OK
          Applying auth.0008_alter_user_username_max_length... OK
          Applying auth.0009_alter_user_last_name_max_length... OK
          Applying sessions.0001_initial... OK


3. 开启开发服务器
   Django自带一个轻量级的web服务器来快速运行你的代码，不需要发费额外的时间来配置一个生产服务器。当你运行Django的开发服务器，他会一直检查你的代码变化。当代码有变化，它会自动重启将你从手动重=解放出来。但是，他可能无法注意到一些操作，例如，在项目中添加了一个新文件，所以，在某些场景下还是需要手动重启。
   打开终端，在你的项目目录下运行以下代码来开启开发服务器：
   运行命令：(venv) E:\Djangowj\venv\mysite>python manage.py runserver
            (venv) E:\Djangowj\venv\mysite>python manage.py runserver 127.0.0.1:8001
            Performing system checks...

            System check identified no issues (0 silenced).
            April 14, 2019 - 23:37:35
            Django version 2.1.7, using settings 'mysite.settings'
            Starting development server at http://127.0.0.1:8001/
            Quit the server with CTRL-FN-SHIFT.

项目和应用的区别：在Django中，一个项目被认为是一个安装了一些设置的Django；一个应用是一个包含模型（models）、视图（views）、模板（templates）以及URLs的组合

#创建第一个应用
1. 创建应用
    创建blog应用的命令：(venv) E:\Djangowj\venv\mysite>python manage.py startapp blog
    新应用下面有以下文件：
    admin.py:在这你可以注册你的模型（models）并将它们包含到Django的管理页面当中。使用Django的管理页面是可选的。
    migrations:这个目录将会包含你的应用的数据库迁移。migrations允许Django跟踪你的模型（model）变化并因此来同步数据库。
    models.py:你的应用的数据模型（models）。所有的Django应用都需要拥有一个models.py文件，但是这个文件可以是空的。
    tests.py:在这你可以为你的应用创建测试。
    views.py:你的应用逻辑将会放在这里。每一个视图（view）都会接受一个HTTP请求，处理该请求，最后返回一个响应。

2. 设计数据结构
   一个模型(model)就是一个python类，该类继承了django.db.models.model,在其中的每一个属性表示一个数据库字段。Django将会为models.py中的每一个定义的模型（model）创建一张表。当你创建好一个模型（model），Django会提供一个非常实用的API来方便的查询数据库。

   博文： 草稿状态  发布状态

   数据库中的字段必须是一种类型：models.xxxField.

   数据库普通字段类型：
    CharField：字符串字段 用于存储较短的字符串
               max_length = 250
    SlugField：只包含字母下划线和连字符的输入字段（URL）
              unique_for_date 使用日期构建url
    TextField：大容量的文本字段
    DateTimeField：日期字段  支持时间的输入
    DateField：日期字段  可选参数：auto_now:当该字段被保存时设置为当前的时间
                                 auto_now_add:当对象首次被创建时，将该字段的值设置为当前时间
    FileField：一个文件的上传字段
    FloatField：浮点型字段
    ImageField：类似于FileField
    PhoneNumberField：带有美国风格的电话号码 CharField
    TimefField:时间字段
    URLField：保存URL
    Foreighkey：外键
                related_name指定反向关系名称
    
   设计博客
   定义数据表：class post()
   标题： title = CharField(max_length = 250)
   标识： slug = SlugField(max_length = 250)
   作者： author = ForeignKey(User)
   博客内容： body = TextField()
   发布时间：publish= DateTimeField(default=timezone.now)
   创建时间：created = DateTimeField(auto_now_add = True)
   更新时间：updated = DateTimeField(auto_now =True)
   状态：
     #定义状态列表（两种状态：草稿状态  发布状态）
      STATUS_CHOICES = (
                            ('draft','Draft'),  #定义草稿元组
                             ('published','Published'), #定义发布元组
                          )
      #定义status字段
        status =models.CharField(max_length=10,
                             choices = STATUS_CHOICES,
                             default = 'draft'
                          ) 
   在模型类中的Meta子类定义元数据
      数据库表名称
      数据库字段排序
      abstract: True or False 标识本类是否为抽象的基类
      app_label:定义这个类所属的应用 例如：app_label = 'blog'
      db_table:映射数据库表名称  如果不指定此字段Django会自动创建格式：应用名称_模型名称
      order_with_respect_to:定义按照某个外键的应用关系排序
      ordering：按默认的字段排序 默认是升序  "-"是降序
  
  3. 激活APP运行
    先安装pytz,命令： (venv) E:\Djangowj\venv\mysite>pip install pytz

    为了让Django能保持跟踪你的应用并且根据你的应用中的模型（models）来创建数据库表，我们必须激活你的应用。因此，
    1.编辑settings.py 文件，在INSTALLDE_APPS设置中添加blog。
    2.执行数据库同步：(venv) E:\Djangowj\venv\mysite>python manage.py makemigrations blog

                    Migrations for 'blog':
                    blog\migrations\0001_initial.py
                      - Create model post
    3.查看信息：命令：(venv) E:\Djangowj\venv\mysite>python manage.py sqlmigrate blog 0001
      BEGIN;
      --
      -- Create model post
      --
      CREATE TABLE "blog_post" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "title" varchar(250) NOT NULL, "slug" varchar(250) NOT NULL, "body" text NOT NULL, "publish" datetime NOT NULL, "created" datetime NOT NULL, "updated" datetime NOT NULL, "status" varchar(10) NOT NULL, "author_id" integer NOT NULL REFERENCES "auth_user" ("id") DEFERRABLE INITIALLY DEFERRED);
      CREATE INDEX "blog_post_slug_b95473f2" ON "blog_post" ("slug");
      CREATE INDEX "blog_post_author_id_dd7a8485" ON "blog_post" ("author_id");
      COMMIT;
    4.同步到数据库
      命令：(venv) E:\Djangowj\venv\mysite>python manage.py migrate
                  Operations to perform:
                    Apply all migrations: admin, auth, blog, contenttypes, sessions
                  Running migrations:
                    Applying blog.0001_initial... OK

#为应用创建一个管理站点
1. 创建超级用户
   命令：(venv) E:\Djangowj\venv\mysite>python manage.py createsuperuser
                Username (leave blank to use 'hp'): admin
                Email address: admin@163.com
                Password:wj123567

2. 运行打开默认后台管理页面
   首先运行服务器,命令：(venv) E:\Djangowj\venv\mysite>python manage.py runserver
                        http://127.0.0.1:8000/admin/
                        账号：admin
                        密码：wj123567
  Group和User模型（models）位于django.contrib.auth,是Django权限管理框架的一部分。如果你点击Users，你将会看到你之前创建的用户信息。你的blog应用的post模型（model）和User（model）关联在一起。记住，它们是通过author字段进行关联的。
3. 在管理站点中添加模型
   编辑admin.py
    from django.contrib import admin
    from .models import post
    # Register your models here.
    admin.site.register(post)

#为models定制管理后台
1. 编辑admin.py
   属性 = 元组
    list_display:定义要显示的字段
    list_filter:过滤菜单（默认在右侧）
    search_fields:定制搜索框
    prepopulated_fields:填充,slug与标题一致(字典类型：prepopulated_fields = {'slug':('title',)})
    raw_id_fields:搜索控件
    date_hierarchy:时间层的快速导航栏（字符串类型）
    ordering:排序[列表类型]


#QuerySet 查询集（作用：就是查询的作用）
 python   manage.py   shell
  Django自带了一个强大的数据库抽象API可以让你轻松地创建、检索、更新以及删除对象。Django的object-relational Mapper(ORM)可以兼容MySQL,PostgreSQL,SQLite以及Oracle。请记住你可以在你项目下的setting.py中编辑DATABASES设置来指定数据库。Django可以同时与多个数据库进行工作，这样你可以编写数据库路由通过任何你喜欢的方式来操作数据。
1. 创建对象
   1. import(导入包)
       from django.contrib.auth.models import User
       from blog.models import Post
   2. get user(获取对象)
       user = User.objects.get(username='admin')
   3. Post object(创建对象即博客项)
      post = Post.objects.create(title='shell test',slug='stest',body='post test',author=user)
   4. save
      post.save()
2. 更新对象
   post.title='Hello'
   post.save()
3. 获取对象
   data = Post.objects.all()
   >>> data
  <QuerySet [<Post: Hello>, <Post: weather>, <Post: today data>, <Post: my first blog>]>
  >>> for i in data:
  ...     print(i)
  ...
  Hello
  weather
  today data
  my first blog
  >>> data = Post.objects.all()
  >>> data[0]
  <Post: Hello>

  QuerySet数据集查询的函数：
    filter()  过滤(符合条件的)  #Post.objects.filter(publish__year=2019)
    exclued() 取反(不符合条件的)
    order_by()  针对某个字段排序
    all() 所有queryset
    get() 获取唯一元素  如果不唯一则报错
    first() 获取第一个元素
    last()  获取最后一个元素
    exists()  检查某条记录是否存在
    update()  更新字段
    delete()  删除指定记录
    create()  创建
    save()  保存
#创建模型管理器(返回定制的查询管理对象)
1. class PublishedManager(models.Manager):#定制过滤所有的发布过的对象
    def get_queryset(self):#返回执行过的查询集的方法
        return super(PublishedManager,self).get_queryset().filter(status='published')

  objects = models.Manager()
    published = PublishedManager()


#构建视图
决定展示页面；通过函数或模板渲染器（渲染后）把数据传递给网页服务器

一个Django视图（view）就是一个python方法（函数），它可以接收一个web 请求（request）然后返回一个web响应（response）。在视图（view）中通过所有的逻辑处理返回期望的响应。
1. 创建视图
   视图-->URL-->template
2. 为视图指定URL
   一个URL模式是由一个python正则表达式，一个视图（view），一个全项目范围内的命名组成。Django在运行中会遍历所有URL模式直到第一个匹配的请求URL才停止。

3. 创建模板




