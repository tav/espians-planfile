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

We can see that, at least for the first two months, on demand pricing starts out being the cheapest for us:

```pycon
>>> display_costs(2)
On-Demand	  4526.00	  2263.00
Light/1yr	  4732.42	  2366.21
Light/3yr	  5563.00	  2781.50
Medium/1yr	  7300.14	  3650.07
Medium/3yr	 10162.30	  5081.15
Heavy/1yr	  8186.66	  4093.33
Heavy/3yr	 11663.72	  5831.86
```
