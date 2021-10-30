# Tokenization
# Featurization
# Intent Classification / Response Selectors
- However, sometimes it makes sense to restrict the features that are used by a specific component.
```python
language: "en"

pipeline:
  - name: ConveRTTokenizer
  - name: ConveRTFeaturizer
    alias: "convert"
  - name: RegexFeaturizer
    alias: "regex"
  - name: LexicalSyntacticFeaturizer
    alias: "lexical-syntactic"
  - name: CountVectorsFeaturizer
    alias: "cvf-word"
  - name: CountVectorsFeaturizer
    alias: "cvf-char"
    analyzer: "char_wb"
    min_ngram: 1
    max_ngram: 4
  - name: DIETClassifier
    epochs: 100
  - name: EntitySynonymMapper
  - name: ResponseSelector
    featurizers: ["convert", "cvf-word"]
    epochs: 100
```

# Improving Performance
- 对于各类意图分类的数据要平均
```python
language: "en"

pipeline:
# - ... other components
- name: "DIETClassifier"
  batch_strategy: sequence
```

# Slot
- Slot是给对话机器人提供记忆功能，用于存储用户提供的信息。
```python
slots:
  slot_name:
    type: text
	# this slot will not influence the predictions
	# of the dialogue policies
	influence_conversation: false
```
## Slot-Type
1. text
2. bool
3. categorical: Storing slots which can take one of N values.
4. float: max_value, min_value
5. list: Storing lists of values, only zero or non-zero data influence slot.
6. any: Can't influnce conversation.