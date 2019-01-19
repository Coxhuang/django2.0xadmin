
# xadmin

## #0 blog

```
https://blog.csdn.net/Coxhuang/article/details/86558372
```

## #1 环境

```
python==3.6
Django==2.0.7
xadmin==2.0.1  # django >= 2 不要安装低版本的xadmin
```

## #2 下载 xadmin

```
https://github.com/sshwsfc/xadmin/tree/django2
```

## #3 安装

### #3.1 pip安装

将上面的zip文件下载好了之后，我们在终端进入下载好的zip文件的目录下，然后执行


```
pip3 install xadmin-django2.zip
```

查看xadmin版本

```
pip3 list
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190119221726879.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NveGh1YW5n,size_16,color_FFFFFF,t_70)

### #3.2 源码安装
首先也是需要将zip文件下载好。然后在pycharm的项目下新建一个package，命名为extra_apps,并且Mark为Sources Root，再把zip压缩包中的xadmin文件夹复制到extra_apps中,然后在settings中配置xadmin的路径

```
import sys
sys.path.insert(0,os.path.join(BASE_DIR,'extra_apps'))
```


## #4 xadmin的配置

### #4.1 新建一个django项目
### #4.2 修改settings.py

```
INSTALLED_APPS = [
    ...
    'xadmin', # 添加
    'crispy_forms', # 添加
    'app', # 添加app名
]
```

### #4.3设置urls.py文件

```
...
import xadmin

urlpatterns = [
    path('admin/', admin.site.urls),
    path('xadmin/', xadmin.site.urls),
]
```

### #4.4数据库迁移

```
 python3 manage.py makemigrations
 python3 manage.py migrate 
```

### #4.5新增超级管理员

```
python3 manage.py createsuperuser
```
### #4.6 启动项目,进入xadmin

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190119222301220.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NveGh1YW5n,size_16,color_FFFFFF,t_70)

### #4.7 pip安装和源码安装的区别
- 使用pip安装不用在settings中配置xadmin的路径。而源码安装需要配置xadmin的路径。
- 使用pip安装的方式可以在pip list中看到安装的xadmin，而使用源码的不能。
- 使用pip安装的每次新建项目时只需要指定解释器为安装了xadmin的就行了。而使用源码安装的每次做一个新的项目的时候都需要将源码复制过去，进行配置。
- 使用pip安装的需要更改源码不方便，而使用源码安装的更改源码比较方便。

## #5 使用

### #5.1 设置中文
settings.py

```
# LANGUAGE_CODE = 'en-us'
LANGUAGE_CODE = 'zh-hans'
# TIME_ZONE = 'UTC'
TIME_ZONE = 'Asia/Shanghai'
```
