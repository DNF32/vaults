---
aliases:
  - use-case-justice
tags: []
title: use-case-justice
---

# use-case-justice

1)Criar dossier do juíz (caracterizando-o com nome, número do processo, tipo, …)
2)Classificação dos documentos (alegação, parecer, contra-alegação, …)
3)Pesquisar sentenças com base nos documentos do dossier e na sua caracterização
  1)TJUE
  2)Acórdãos de um determinado tipo
  3)Só os meus acórdãos
  4)Adicionar sumarização
5)Elaborar draft do parecer


hyper link for acordaos que foram buscados
  - analisar os chunks


problems:
 - o user tem que saber o que esta no input. Two modes where the context is feed with difference options.  
 - add own rules for each settings
 - really concerned with hallucinations. Fact checking everything takes a lot of time. 

wants:
 - logic of agents for difference settings (primeira instancia, segunda )
    - jurisdicao
 - factos provados por acordo (ver o que foi provado)
 - in parallel a chat interface (maybe fetch the vector store)
 - agreggate simmillar cases, check if there isn't something new 
 - formatting text, fazer com seja facil editar e exportar em word

------------------
First let's start using the good documents. Parsing the pdf text and the OCR.


Try the new reasoning model with the goal of comparing if two cases are simillar, get a way of having a simillarity score.

Maybe to get a score we can have a BERT output and then compute cosine similarity




  
