As of Django 1.10, the patterns module has been removed (it had been deprecated since 1.8).

Luckily, it should be a simple edit to remove the offending code, since the urlpatterns should now be stored in a plain-old list:

urlpatterns = [
    url(r'^admin/', include(admin.site.urls)),
    # ... your url patterns
]

高版本django不需要引用patterns，DjangoUeditor可直接删掉，不然出错。
工程minicms的urls.py文件引用from news.views import *，url(r'^$', 'news.views.index', name='index')更改为
url(r'^$', index, name='index')直接引用函数的方式。如此类似，不然会报 TypeError: view must be a callable or a list/tuple in the case of include() 的错误。

django.db.utils.IntegrityError: UNIQUE constraint failed: news_article.slug错误需要删除数据库migrations

no such column: news_column.nav_display：
1. python manage.py dbshell 进入数据库 shell
2. 输入 .tables 查看有SQLite数据库中有哪些表
3. DROP TABLE 表名;

