---
aliases:
  - actemize feature
tags: []
title: actemize-feature
---

---azure
aliases:

- actemize feature
  tags: []
  title: actemize-feature

---

# actemize feature

Ter em conta as horas para fazer a nova feature.

I need to filter the texts block by uniqueness of bbox using an iou threshold `das`

- [ ] ````python
          import numpy as np
          ```
      ````

def compute_iou(box1, box2):
"""Compute IoU (Intersection over Union) between two bounding boxes."""
x1 = max(box1["x0"], box2["x0"])
y1 = max(box1["y0"], box2["y0"])
x2 = min(box1["x1"], box2["x1"])
y2 = min(box1["y1"], box2["y1"])

    intersection = max(0, x2 - x1) * max(0, y2 - y1)

    area1 = (box1["x1"] - box1["x0"]) * (box1["y1"] - box1["y0"])
    area2 = (box2["x1"] - box2["x0"]) * (box2["y1"] - box2["y0"])

    union = area1 + area2 - intersection
    return intersection / union if union > 0 else 0

def non_maximum_suppression(text_blocks, iou_threshold=0.95):
"""Apply Non-Maximum Suppression to remove overlapping text blocks."""
if not text_blocks:
return []

    # Sort by area (larger boxes first)
    text_blocks = sorted(text_blocks, key=lambda b: (b["x1"] - b["x0"]) * (b["y1"] - b["y0"]), reverse=True)

    keep = []
    while text_blocks:
        best = text_blocks.pop(0)
        keep.append(best)
        text_blocks = [b for b in text_blocks if compute_iou(best, b) < iou_threshold]

    return keep

```

```
