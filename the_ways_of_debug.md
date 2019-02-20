## The way of debugging 

[TOC]



### 一、Django default debug page

- **Exception details**
- **Exception location**

- **Traceback**
- **Request information**



### 二、A better debug page

有一个功能强大的交互式python解释器命令行。开启方法：

- 安装django_extensions和Werkzeug

- 将django_extensions加入到INSTALLED_APPS中
- 通过python manage.py runserver_plus命令来运行



### 三、print大法

**so easy！**



### 四、Django Debug Toolbar

记录请求和响应的详细信息，包括SQL、Headers、Request、Static files、Templates等等。

- 安装django-debug-toolbar

- 确保'django.contrib.staticfiles'有添加到INSTALLED_APPS中

- 将debug_toolbar添加到INSTALLED_APPS中

- 在全局urls.py文件中添加如下路由：

  ```python
  # 在全局urls.py文件中添加
  
  if settings.DEBUG:
      import debug_toolbar
      urlpatterns = [
          path('__debug__/', include(debug_toolbar.urls)),
  
      ] + urlpatterns
  ```

- 在settings.py文件，MIDDLEWARE列表中添加'debug_toolbar.middleware.DebugToolbarMiddleware'

- 在settings.py文件中添加INTERNAL_IPS列表（本机地址），如果你在本地调试，就填写127.0.0.1

  ```python
  # settings.py文件中的配置可以这样添加
  
  if DEBUG:
      # INTERNAL_IPS = ('39.108.191.165', 'www.youkou.site', '127.0.0.1', 'localhost',)
      INTERNAL_IPS = ['35.236.189.85', '110.53.182.23', '36.157.228.156']
      MIDDLEWARE.insert(0, 'debug_toolbar.middleware.DebugToolbarMiddleware')
      INSTALLED_APPS += (
          'debug_toolbar',
      )
      
  ```

  如果不知道如何填写INTERNAL_IPS，可以在你的视图中使用如下代码查看ip地址：

  ```python
  print("IP Address for debug-toolbar: " + request.META['REMOTE_ADDR'])
  ```



### 五、Python debugger pdb

在需要调试的地方，使用如下代码：

```python
import pdb; pdb.set_trace()
```



### 六、我比较喜欢的调试器[pudb](https://documen.tician.de/pudb/starting.html)

在需要调试的地方，使用如下代码：

```python
import pudb; pudb.set_trace()
# import pudb; pu.db
```

