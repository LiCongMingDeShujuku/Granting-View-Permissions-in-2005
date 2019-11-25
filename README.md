![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 授予2005年的查看权限
#### Granting View Permissions in 2005
**发布-日期: 2007年05月31日 (评论)**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
是否有过开发人员需要查看一些产品的源代码，表或产品数据库的情况？ 
相对于接收100个发送对象定义的请求，更简单的方法是你可以简单地授予他们权限，查看定义。
 这是一个授予用户查看所有定义权限的示例。可以查看特定数据库的所有表，视图和过程。 
这将为数据库中的每个对象生成一个脚本。每个文件只能使用一个脚本，或者一次运行所有脚本。 记得按CTRL + T将输出设置为文本。



## English
Ever have a case where a developer needs to see the source code
behind some procedures, tables, or views on the production databases?
well instead of receiving 100 requests to send the object definitions of
these objects to them you can simply GRANT them permissions to
VIEW definitions.

Here’s one example to grant a user permissions to see all definitions
of all Tables, Views, and Procedures of a particular database.
this will produce a single script for every object in the database. you
can use just one script per file, or run it all at once.
remember to set the output to text by pressing CTRL+T


---
## Logic
```SQL
use [MyDatabase]
go

set nocount on
select
	‘use [MyDatabase] ‘ + char(10) 
	+ ‘GRANT VIEW DEFINITION ON [dbo].[‘ + name + ‘] TO [DOMAIN\User]’ 	+ char(10) 
	+ ‘go’ + char(10)
from 
	sysobjects 
where 
	xtype 		= ‘P’ 
	or xtype 	= ‘U’ 
	or xtype 	= ‘V’ 
	or xtype 	= ‘X’ 


```
一些开发人员需要在生产中看到特定数据库对象的定义，这样他们就可以在测试/开发平台下创建这些对象。

通常当你想到它时，你不想对每个物体进行更改。这需要开发人员不断回来寻找更多的对象。

一个解决方案是给他们dbo，但这并不是最好的方案。所以还有个最好的方法就是让他们能够看到定义而不授予他们任何额外的权限。那么你只给出每个对象的“视图定义”权限。
就可以了。
完成。



Some developers need to see the definition of particular database objects in production so they can create those objects under their test/development platforms. 
well normally when you think about it… you don’t want to perform grants per object. 

That would take for ever, and the developers would constantly be coming back for more objects. one solution is to just give them dbo which is not warranted right so the next best thing is just give them the ability to see the definition wihout granting them any extra permissions so you give just the `view definition` permission per object. 

thats it.





[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

