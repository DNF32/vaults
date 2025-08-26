---
aliases:
  - pds justice
  - PDS justice
tags: []
title: pds-justice
---

# PDS justice

At create process time we need to generate more things for the juri options

1. filter by species id and jury ( on the rag to see the similar cases)
2. If the number is less than 5 this are the cases
3. If not we can do a similarity with the case summary and truncate the top 5 results

then we need to make some questions for this 5 found cases

Side effect: we should load Redis to take in process_ids that are similar.

-- create

## create_chat

vai ser preciso um servico de carregar os docs/summarios into redis memory for fast access
servico para carregar as perguntas do processo

podemos assumir de process_id + juri flag

-- create process
Na zona de gerar perguntas temos de gerar tambem jurisprudence para os users
No caso de create process ser feito pelo vitor temos de ter uma funcao mais simples

## Tomorrow

I can go only and scrapt some sentencas do then try out the summaries of the case settings this way we can try ajust the summarization of case summary to be something a little bit more strututereed.

- [ ] Having new stuff in the db we can then test the get_similar_cases function

Note: to send to the frontend data we probably need the case name to  then filter out the in the next queries sent
