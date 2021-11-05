# 1.文件格式
- 使用 YAML 格式管理training data, including NLU data, stories and rules.
# 2.High-Level Structure
- 每一个文件可以包含多个 key, 但是 key 只能出现一次
- 可用的 key:
	- version
	- nlu
	- stories
	- rules
- 例子 
``` yaml
version: "2.0"

nlu:
- intent: greet
  examples: |
    - Hey
    - Hi
    - hey there [Sara](name)

- intent: faq/language
  examples: |
    - What language do you speak?
    - Do you only handle english?

stories:
- story: greet and faq
  steps:
  - intent: greet
  - action: utter_greet
  - intent: faq
  - action: utter_faq

rules:
- rule: Greet user
  steps:
  - intent: greet
  - action: utter_greet

```
- 如果要 test stories, 需要在 yaml 文件名添加前缀 test_. 
- "|" 可以进行换行
