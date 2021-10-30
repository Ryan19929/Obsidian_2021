# PIPELINE
- In Rasa Open Source, incoming messages are processed by a sequence of components. These components are executed one after another in a so-called processing `pipeline` defined in your `config.yml`
- pipeline可以理解为处理数据的一个管道，通过在config.yml自定义数据处理的方法。
- https://rasa.com/docs/rasa/ideal-img/component-lifecycle-img.0111328.1202.png
- 多意图识别，
	- intent_tokenzation_flag: Set it to `True`, so that intent labels are tokenized.
	- intent_split-symbol: Set it to the delimiter string that splits the intent labels. In this case `+`, default `_`.