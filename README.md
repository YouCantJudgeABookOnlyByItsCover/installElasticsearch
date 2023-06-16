# installElasticsearch
安装es记录.  about how to install elasticsearch

参考文章：https://blog.csdn.net/robinson_911/article/details/94554607

总结步骤：
1.下载6.6.2到本地
下载链接：https://www.elastic.co/cn/downloads/past-releases#elasticsearch
2.cd到解压后的elasticsearch目录。
3.执行./bin/elasticsearch
4.出现问题：程序没有权限：解决：1.终端开启权限：sudo spctl  --master-disable。2.设置：接着打开【系统偏好设置】，选择【安全性与隐私】，选择【通用】，可以看到【任何来源】已经选定
参考：https://zhuanlan.zhihu.com/p/385082722
5.执行./bin/elasticsearch
6.出现问题：[2023-06-16T15:03:49,497][WARN ][o.e.b.ElasticsearchUncaughtExceptionHandler] [unknown] uncaught exception in thread [main]
org.elasticsearch.bootstrap.StartupException: java.lang.RuntimeException: can not run elasticsearch as root
	at org.elasticsearch.bootstrap.Elasticsearch.init(Elasticsearch.java:163) ~[elasticsearch-6.6.2.jar:6.6.2]

7.解决：执行两个命令：
bin/elasticsearch-plugin remove ingest-geoip 
bin/elasticsearch-plugin install ingest-geoip
参考：https://discuss.elastic.co/t/try-to-run-elasticsearch-but-keeps-stopping-immediately/141886/4
8.执行./bin/elasticsearch。
能够打开 http://localhost:9200/
