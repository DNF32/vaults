---
aliases:
  - dera-vs-ira
tags: []
title: dera-vs-ira
---

# dera-vs-ira
In DERA we have the LLM chains for data extraction. There is a strucutre called the `extraction schema` that especifies the information to retreave.

In IRA the task is of token classification. Given an image and bounding boxes we can classify each token, then we can further join the token according to the classification given.


## IRA

- [x] Ja consigo sacar as images, agora tenho de ver se consigo os JSON. 
- [x] Passar as boas funcoes para um outro script externo 

Os ficheiros model.py inference.py process_image and processor -> only changed because of black
reverte the inference_debug.py



Usar um evaluation schema para as metricas.

here There are some metrics for LLM evaluation- https://www.confident-ai.com/blog/llm-evaluation-metrics-everything-you-need-for-llm-evaluation

It took 13.14 minutos to process the testbed
