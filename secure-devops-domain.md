---
id: secure-devops-domain
tags: #ops, TODO
title: Secure DevOps Domain
---

We are dependent on an increasing number of third party service providers who use email as the fundamental method of authentication. If an attacker manages to access any of these admin email accounts, it would be possible for them to simply reset our logins at various providers and inflict significant damage to our operations.

The nature of such attacks have been on the rise in recent years and getting [increasingly](http://blog.cloudflare.com/post-mortem-todays-attack-apparent-google-app) [sophisticated](http://www.wired.com/gadgetlab/2012/08/apple-amazon-mat-honan-hacking/all/). In order to minimise our exposure to this vulnerability we must set up an independent `espians.net` domain for operations. This domain should be completely quarantined from the rest of our operations.

* Amazon Web Services
* Braintree Payments
* DNS Made Easy
* Google App Engine
* Google Maps
* Mailchimp
* Nexmo
* PayPal
* Twilio