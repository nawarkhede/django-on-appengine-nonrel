# django-on-appengine-nonrel

Google App Engine - django with non rel database

**Prerequisite**

Python – 2.7<br>
Django- 1.5<br>
Appengine – 1.9.6<br>

Download following packages ,<br>
django-nonrel   https://github.com/django-nonrel/django<br>
djangoappengine https://github.com/django-nonrel/djangoappengine<br>
djangotoolbox https://github.com/django-nonrel/djangotoolbox<br>
django-autoload https://bitbucket.org/twanschik/django-autoload<br>
django-dbindexer https://github.com/django-nonrel/django-dbindexer<br>

Now create django project named testapp,
Now unzip all the above packages and paste in your django project , now your project should like this ,

![Structure](http://2.bp.blogspot.com/-b9HWGJyDSFQ/U8BQL7ZemVI/AAAAAAAABCs/9-qyPlY8sg4/s1600/tree1.png "Optional title")


Now download django-testapp from https://github.com/django-nonrel/django-testapp and unzip it elsewhere, and copy manage.py file from this to our projct root directory.It will prompt you to replace with previous one ? click on yes. Now copy settings.py , indexes.py  and app.yaml file from  this folder and and paste it to our root directory ,

Now our project  under directory testapp looks like ,

![Structure](http://3.bp.blogspot.com/-73ZBif2OBwA/U8BQjN3BHvI/AAAAAAAABC0/EixeUcqJCBQ/s1600/tree2.png "Optional title")

Now just cut and paste urls.py from testapp app.  And finally our project looks like ,

![Structure](http://1.bp.blogspot.com/-dsV5iqckzx0/U8BQ2oSXDTI/AAAAAAAABC8/yAWHZRexFCw/s1600/tree3.png "Optional title")

Now run django project using runserver command locally , you should see homepage for django project.

Now edit views.py from testapp add following contents ,

```
from django.http import HttpResponse
def home(request):
    return HttpResponse("Hello World")
```

and modify urls.py file to the following contents,

```
from django.conf.urls import patterns, include, url

from django.contrib import admin
admin.autodiscover()

urlpatterns = patterns('',
    url(r'^$', 'testapp.views.home', name='home'),
)
```

# Uploading it to appengine ,

First go to appengine.google.com and create a new application by specifying applicaition name and title. And click on create application , now edit your app.yaml file and edit application name , make sure that name application created is same as name in app.yaml.
Now final step ,Run following command and provide valid creadentials ,
```
python manage.py deploy
```
and follow instrucions.

Now you can see you app online <appname>.appspot.com 

Note : If tou want to change appname then edit app.yaml file.
