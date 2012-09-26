---
id: reserved-instances-on-ec2
tags: TODO
title: Reserved Instances on EC2
---

In exchange for an upfront payment, EC2 offer reserved instances with significantly lower hourly rates than "on demand" ones. For example, looking at `hi1.4xlarge` instances in the `us-east-1` region:

```python
pricing = [['On-Demand',  0,     3.1],
           ['Light/1yr',  2576,  1.477],
           ['Light/3yr',  3884,  1.15],
           ['Medium/1yr', 5973,  0.909],
           ['Medium/3yr', 9133,  0.705],
           ['Heavy/1yr',  7280,  0.621],
           ['Heavy/3yr',  10960, 0.482]]
```
