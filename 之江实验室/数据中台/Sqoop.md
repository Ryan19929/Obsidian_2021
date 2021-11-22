## sqoop 导出语法
``` shell
sqoop export --connect jdbc:mysql://10.100.29.39:32222/ZhiWangSpider --username root -P --table project1 --columns id,name,ratify_no,type,unit,unit_type,area_code,leader,total_fund,year,keywords_ch,keywords_en,finish,applicant_code,conclusion_abstract,member,abstract_ch,abstract_en,start_time,end_time,time_span,url --fields-terminated-by '\t'  --export-dir /user/data/output/project/job7/
```

``` shell
sqoop export \
--connect \
--username \
--password \
--table \
--columns <> \
--fields-terminated-by \
--export-dir \
```

~~轮询的方法可能会好一点~~
- 使用 os.popen 可以使在后台运行