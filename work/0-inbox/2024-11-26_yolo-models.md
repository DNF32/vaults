---
aliases:
  - yolo-models
tags: []
title: yolo-models
---

# yolo-models
This i will summary the paper
- https://arxiv.org/abs/1506.02640

# IoU metric 
One of the key metrics in computer vision is intersection over union (IoU). 
$$
IoU = \frac{AreaOfIntersection}{AreaOfUnion}
$$
How it's used? To get perfomance evaluatio of a Object detection model one set's an iou nevel such that a prediciton is considered true relative to some ground truth. 

# Precision score
By prediciton we get a probability score and a class prediciton `(p, Clss)`. `p` reflect the probability of being a object detected of class `clss`, this parameter is the confidence score, `conf`. We associated a `gt` label and a `pred` by computing the IoU, and then if it is over a certain threshold `t`, it considered a match. Given this we have a Precison and Recall for threshold `t`.

Doing this over mutiple thresholds we get the Precison-recall curve. (Recall is decresing relative to threshold; the same isn't true for precision). We make we curve monotonic and compute the area below, this gives `AP@t`. 

Averaging over IoU threshold give `mAP`. We can further average over mutiple classes.

# Datasets 
COCO - Common Objects in Context.

# Struture layers
P3
P4
P5
# Code bases
https://github.com/open-mmlab
https://github.com/Deci-AI/super-gradients - yolo Nas can be an option
https://paperswithcode.com/paper/yolov3-an-incremental-improvement
https://arxiv.org/pdf/2408.13003v1
https://arxiv.org/pdf/2110.06864
https://patrick-llgc.github.io/Learning-Deep-Learning/paper_notes/fcos.html - blog post on focal loss
https://staff.fnwi.uva.nl/a.visser/research/nao/2024//Eindverslag_Maximum_Class_Separtion_Yolo8_Leren_en_Beslissen2024.pdf - paper where I learned to see the shape of the last layer. 
https://arxiv.org/pdf/2006.04388 - distributed focal loss and qualitative focal loss. 
