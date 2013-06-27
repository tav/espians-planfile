---
id: ec2-reserved-instances
tags: #ops, +tav, TODO
title: EC2 Reserved Instances
---

In exchange for an upfront payment, EC2 offer reserved instances with
significantly lower hourly rates than "on demand" ones. For example, looking
at `hi1.4xlarge` instances in the `us-east-1` region:

```python
pricing = [['On-Demand',  0,     3.1],
           ['Light/1yr',  2576,  1.477],
           ['Light/3yr',  3884,  1.15],
           ['Medium/1yr', 5973,  0.909],
           ['Medium/3yr', 9133,  0.705],
           ['Heavy/1yr',  7280,  0.621],
           ['Heavy/3yr',  10960, 0.482]]
```

And by using a little helper function:

```python

def display_costs(months):
    for type, upfront, hourly_rate in pricing:
        total = upfront + (months * hourly_rate * 730)
        print "%s\t%9.2f\t%9.2f" % (type, total, total/months)
```

We can see that, at least for the first two months, on demand pricing starts
out being the cheapest for us:

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

But by month 9, the `Heavy/1yr` — which corresponds to the [Heavy Utilisation
Reserved Instance for a 1-year
Term]((http://aws.amazon.com/ec2/pricing/#heavyUtilizationRI) — has become the
cheapest and costs us just 56% of the on demand pricing:

```pycon
>>> display_costs(9)
On-Demand	 20367.00	  2263.00
Light/1yr	 12279.89	  1364.43
Light/3yr	 11439.50	  1271.06
Medium/1yr	 11945.13	  1327.24
Medium/3yr	 13764.85	  1529.43
Heavy/1yr	 11359.97	  1262.22
Heavy/3yr	 14126.74	  1569.64
```

By month 18, this decreases to 38% and by month 36, it's less than 29% of what
on demand instances would have cost us. Surprisingly, even at 36 months, the
`Heavy/1yr` is still cheaper than the `Heavy/3yr` making it the best option
overall:

```pycon
>>> display_costs(36)
On-Demand	 81468.00	  2263.00
Light/1yr	 41391.56	  1149.77
Light/3yr	 34106.00	   947.39
Medium/1yr	 29861.52	   829.49
Medium/3yr	 27660.40	   768.34
Heavy/1yr	 23599.88	   655.55
Heavy/3yr	 23626.96	   656.30
```

Unfortunately we don't yet have the capitalisation to invest in reserved
instances. So we need to come up with an algorithm that tells us when we can
do so — both initially and on an ongoing basis. The algorithm should consider
all the following factors:

* Revenue + Cash Flow
* Growth Rate
* Churn
* EC2 Instance Usage

It should also factor in the possibility that we might want to move away from EC2. The Amazon-supported [EC2 Reserved Instance Marketplace](http://aws.typepad.com/aws/2012/09/amazon-ec2-reserved-instance-marketplace.html) would help with this, but there would still be a cost to us.