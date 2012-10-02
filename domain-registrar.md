---
id: domain-registrar
tags: #ops, TODO
title: Domain Registrar
---

Our domains have historically been registered at [BulkRegister](http://www.bulkregister.com/) and [gandi.net](http://www.gandi.net/). These registrars have served us well over the years but, as we move forward, we need to find a more security conscious one that would protect us from [the](http://www.domainnamenews.com/registrars/chinas-baiducom-sues-registercom-attack/6931) [very](http://www.secretgeek.net/sg_hijack_1.asp) [real](http://css-tricks.com/this-sites-domain-is-now-safe/) [threat](http://www.darknet.org.uk/2006/09/domain-stealing-or-how-to-hijack-a-domain/) of [domain hijacking](http://en.wikipedia.org/wiki/Domain_hijacking).

Very few registrars seem to actively publicise their security measures. Of the few that do:

* [Dynadot](http://www.dynadot.com/) provide [multiple two-factor authentication services](http://www.dynadot.com/domain/security.html) via either a mobile app or over SMS in order to protect access to the account. In addition, they provide an [Account Lock feature](http://www.dynadot.com/community/blog/2012/07/domain-security-account-lock-feature.html) so that attackers who get in would have to guess a date before they can unlock the account.

* [Fabulous](http://fabulous.com/) provide an [executive lock feature](http://fabulous.com/informationcenter/index.htm?formdata%5Bqid%5D=115) that freezes a domain's registry settings. Since it can only be removed by Fabulous management after custom conditions specified by us have been fulfilled, we should be able to secure it reasonably well. Unfortunately, Fabulous seems to be available to only those with a portfolio of 750+ domains.

* [Go Daddy](http://www.godaddy.com/) provide a Deadbolt Transfer Protection as part of their [Protected Registration service](http://www.godaddy.com/domainaddon/protected-registration.aspx). Unfortunately, they are elephant killing, SOPA supporting scum who can't even [keep their services running properly](http://www.forbes.com/sites/kellyclay/2012/09/10/5-reasons-you-should-leave-godaddy-and-how/) and [take over 3 days to just respond to a hijacking](http://hubsacademy.com/933/godaddy-fails-on-howardforum-domain-theft/).

* [MarkMonitor](https://www.markmonitor.com/) are the registrar used by Apple, Google, Facebook, Microsoft, Wikipedia, &c. They seem to take security seriously — it's even the first item mentioned in their [domain management offering](https://www.markmonitor.com/services/domain-management.php). However they are also several magnitudes more expensive than what we can currently afford.

* [Moniker](https://www.moniker.com/) provide an affordable and seemingly robust [MaxLock domain protection service](https://www.moniker.com/domainnames/domainsecurity.jsp) which requires offline verification before changes can be initiated. Unfortunately, it sounds like their [service and support has been deteriorating](http://morganlinton.com/throwing-in-the-towel-with-moniker-lack-of-support-leaves-domainers-hanging/) in recent times and that they've been experiencing a number of [system-wide outages](http://domaingang.com/tag/moniker-outage/).

* [Name](http://www.name.com/) provide the [NameSafe two-factor authentication service](http://www.name.com/services/namesafe) to provide an additional layer of security in protecting access to their account. But it's not clear what offline verification mechanisms they provide in case an attacker gets in.

In addition to standard registrar locks, Verisign introduced a [registry lock service](http://www.verisigninc.com/en_US/products-and-services/domain-name-services/grow-your-domain-name-business/registry-lock/index.xhtml?loc=en_US) in 2009 that registrars could use to enable server-level protection for `.com` and `.net` domains. But it's not immediately obvious which registrars support this or how much they charge for it or even how exactly it works.

According to [this article](http://www.circleid.com/posts/domain_registry_locking_why_not_use_it/), the following [EPP status codes](http://www.wdbc.com/domain/status-codes.cfm) should be set for a domain to be considered "locked" at the registry:

    Status: clientDeleteProhibited
    Status: clientTransferProhibited
    Status: clientUpdateProhibited
    Status: serverDeleteProhibited
    Status: serverTransferProhibited
    Status: serverUpdateProhibited

We need to decide on an appropriate registrar.

For the sake of completeness, we should also update the records, enable registrar locking and use new passwords on our existing ones.