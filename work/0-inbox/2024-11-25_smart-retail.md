---
aliases:
  - smart-retail
tags: []
title: smart-retail
---

# smart-retail

Metrica para saber quanto tempo passar a olhar para omontras e produtos.

- code from 2022

Object detection - bbox of person
- Person tracking, connect information from frames (samurai model)
- Transition from two cameras or intersection of cameras. Someform of tracking ID (complex, para o fim)

- Pose estimation person (face blur might not be necessary)

Projection matrix
- Manual annoation of points from plant to image to compute a projection matrix. (Computer graphics maybe can be solv this.)

Projection and then add a vector on top
- Key points can give us a vector


---
Framework Mediapipe
---

DeepSort

Sift feature - large change of intensity of color


https://miro.com/welcomeonboard/TFdOWS9ucURBaHVwWWo0cXJkVFNNRU1VNGJ1aUU1U1d0OUl3ZEpvTEk1SVBqMFN0Rlc0bjhVY0xjTUVXcjUrdmswSXdlMS9hUnBWTGF2RGFGbzZTY1lRd05pOExTSWF1WnY5cDVySkFlRTR5MlU5RjRDTGtHaWlqWHRDT2lZbWMhZQ==?share_link_id=449958033292

https://teams.microsoft.com/l/message/19:meeting_YTkxMjhlOTAtYjcyNy00YjRkLThjMWQtNzExMmMxMDZkMzQ5@thread.v2/1732532637099?context=%7B%22contextType%22%3A%22chat%22%7D

Person detection and tracking - em images 
- DeepSort analisar performance
- So depois usar outra coisa

Performance vs accuracy, fast models

SmartRetail

pasta models modelos pre treinados
notebooks experiments
results - graficos e afins
src - ficheiro de architerura/train
tests - unit tests


---
pre processamento das imagens
---
Use for code Analysis the legacy code

- Modelos 
- Deep sort

Explorar MediaPipe - tele js Repo



---
For ML inference Pytorch and super gradient solutions are slow.

By using ONNX and   OpenVINO speeds can triple, on cpu inference.

Here is a [Github post](https://github.com/ultralytics/yolov5/pull/6613) where it's showed for Yolov5.



-----

https://arxiv.org/pdf/2411.03724 - CCTV paper
