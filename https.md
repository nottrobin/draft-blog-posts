# Moving our sites to HTTPS

We've been making an effort to secure all our websites with [HTTPS][https].
While some Canonical sites have enforced HTTPS for a while (e.g.: [landscape.canonical.com][landscape], [jujucharms.com][charms], [launchpad.net][launchpad]), it's been missing from our other sites until now.

## Why HTTPS?

The [HTTPS movement][movement] has been building for years to help secure internet users against [black-hat hackers][blackhat] and spies. The movement became more urgent after [Edward Snowden revealed][snowden] significant efforts by government agencies to [spy on the world population][spying].

[The EFF][eff] have helped create two projects:  [LetsEncrypt][letsencrypt] - which massively simplifies the free installation of HTTPS certificates; and [HTTPS Everywhere][everywhere] - a browser plugin to help you use HTTPS whenever it's available. The advent of [HTTP/2][https] has [helped negate performance concerns][http2-fast] when moving to HTTPS.

Google have also made efforts to encourage websites to enable HTTPS: First announcing in 2014 that they would [consider HTTPS support in their search ranking algorithm][ranking]; and last year, that [Google Chrome would start visually warning users][chrome] of "insecure" (non-HTTPS) websites.

## Our sites

We secured [https://www.ubuntu.com][ubuntucom] in October of last year, and have since added 10 more sites. We now enforce HTTPS on:

- <https://www.canonical.com>
- <https://insights.ubuntu.com>
- <https://jp.ubuntu.com>
- <https://tutorials.ubuntu.com>
- <https://docs.ubuntu.com/core>
- <https://maas.io>
- <https://snapcraft.io>
- <https://build.snapcraft.io>
- <https://cloud-init.io>
- <https://assets.ubuntu.com/>

We hope to enable HTTPS on our other sites in the coming months.

Enabling HTTPS on large websites within complex organisations can be challenging. I hope to write more about this in a follow-up post.

[movement]: https://encryptallthethings.net/ "EncryptAllTheThings: Security Starts Here"
[blackhat]: https://en.wikipedia.org/wiki/Black_hat "Wikipedia: Black-hat hackers"
[ranking]: https://googlewebmastercentral.blogspot.com/2014/08/https-as-ranking-signal.html "Google: HTTPS as a ranking signal"
[snowden]: https://en.wikipedia.org/wiki/Edward_Snowden#Revelations "Wikipedia: Edward Snowden revelations"
[chrome]: https://developers.google.com/web/updates/2016/10/avoid-not-secure-warn "Google: Not secure warnings in Google Chrome"
[ubuntucom]: https://www.ubuntu.com "Ubuntu: An open source operating system."
[eff]: https://www.eff.org "The Electronic Fronteer Foundation"
[letsencrypt]: https://letsencrypt.org "LetsEncrypt: A free, automated, and open Certificate Authority"
[everywhere]: https://www.eff.org/https-everywhere "The EFF: HTTPS Everywhere - a Firefox, Chrome, and Opera extension that encrypts your communications with supporting websites"
[http2-fast]: https://istlsfastyet.com/ "IsTLSFastYet? "
[http2]: https://http2.github.io/ "HTTP/2 official introduction"
[spying]: https://en.wikipedia.org/wiki/Global_surveillance_disclosures_(2013%E2%80%93present) "Wikipedia: Global surveillance disclosures"
[https]: https://www.eff.org/pages/https "The EFF: About HTTPS"
[landscape]: https://landscape.canonical.com/ "Landscape: The leading management tool to deploy, monitor and manage your Ubuntu servers"
[launchpad]: https://launchpad.net/ "Launchpad: A platform for developing and maintaining open-source software"
[charms]: https://jujucharms.com/ "Juju is an open source, application and service modelling tool from Ubuntu"
