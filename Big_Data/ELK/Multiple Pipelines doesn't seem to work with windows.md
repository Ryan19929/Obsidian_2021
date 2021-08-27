## 1.problem
- when I edit the pipeline.yml to run two pipeline, the configurations is here
```yml
- pipeline.id: "astrex-logs"
  path.config: "C:/Daten/QS_Progs/logstash-6.2.1/config/astrex-logs.conf"
  pipeline.workers: 1
  queue.type: memory

- pipeline.id: "astrex-html"
  path.config: "C:/Daten/QS_Progs/logstash-6.2.1/config/astrex.conf"
  pipeline.workers: 1
  queue.type: memory
 ```
 - like this, but I ran the logstash without no -f, it doesn't work in the winodows os. It said logstash successfully run, but immediately closed.
## 2. solution
- The problem is in the path.
- Because in the linux, I usually know the path started with /, but in the winodws ,I usually write path in this way, C:XXX/XXXX
- But the true path is /C:XXXX/XXXX 