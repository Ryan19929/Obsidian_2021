# 问题汇总
- **问题一**<br/>Diagnostics: Exception from container-launch.<br/>Container id:container_1536891254067_0001_02_000001<br/>Exit code: 1<br/>Exception message: /bin/bash: line 0: fg: no job control
- **解决方法**<br/>去把集群中的mapred-site配置添加
```xml

<!--允许跨平台提交-->

<property>
	
<name>mapreduce.app-submission.cross-platform</name>
	
<value>true</value>
	
</property>

```