# Our open source websites

Nowadays [open-source software][fsf] is everywhere - from [browsers][firefox] to [encryption software][openssl] to [operating systems][ubuntu-desktop]. Even so, it is still relatively rare for the code behind websites and services to be opened up.

## Stepping into the open

Three years ago we started to move our website projects to [Github][github], and we also took this opportunity to start making them public. We started with [the www.ubuntu.com codebase][github-ubuntu], and over the next couple of years all our team's other sites have followed suit.

![canonical-websites org](https://assets.ubuntu.com/v1/909ee411-canonical-websites.png)

At this point practically all the web team's sites are open source, and you can find the code for each site in our [canonical-websites organisation][github-cws].

| [www.ubuntu.com](https://github.com/canonical-websites/www.ubuntu.com) | [developer.ubuntu.com](https://github.com/canonical-websites/developer.ubuntu.com) | [www.canonical.com](https://github.com/canonical-websites/www.canonical.com) |
| [partners.ubuntu.com](https://github.com/canonical-websites/partners.ubuntu.com) | [design.ubuntu.com](https://github.com/canonical-websites/design.ubuntu.com) | [maas.io](https://github.com/canonical-websites/maas.io) |
| [tour.ubuntu.com](https://github.com/canonical-websites/tour.ubuntu.com) | [snapcraft.io](https://github.com/canonical-websites/snapcraft.io) | [build.snapcraft.io](https://github.com/canonical-websites/build.snapcraft.io) |
| [cn.ubuntu.com](https://github.com/canonical-websites/cn.ubuntu.com) | [jp.ubuntu.com](https://github.com/canonical-websites/jp.ubuntu.com) | [conjure-up.io](https://github.com/canonical-websites/conjure-up.io) |
| [docs.ubuntu.com](https://github.com/canonical-websites/docs.ubuntu.com) | [tutorials.ubuntu.com](https://github.com/canonical-websites/tutorials.ubuntu.com) | [cloud-init.io](https://github.com/canonical-websites/conjure-up.io) |
| [assets.ubuntu.com](https://github.com/canonical-websites/assets.ubuntu.com) | [manager.assets.ubuntu.com](https://github.com/canonical-websites/manager.assets.ubuntu.com) | [vanillaframework.io](https://github.com/canonical-websites/vanillaframework.io) |

We've tried to make it as easy as possible to get them up and running, with accurate and simple [README files](https://github.com/canonical-websites/www.ubuntu.com/blob/master/README.md). I'll try to write more about how set-up our projects soon.

![README example](https://assets.ubuntu.com/v1/29f6f52a-readme.png)

We also have many supporting projects - [Django][django] modules, [snap packages][snap], [Docker][docker] images etc. - which are all openly available in our [canonical-webteam organisation][github-cwt].

## Reaping the benefits

Opening up our sites in this way means that anyone can help out by making suggestions [in issues](https://github.com/ubuntudesign/www.ubuntu.com/issues/new) or directly submitting fixes as [pull requests](https://help.github.com/articles/creating-a-pull-request/). Both are hugely valuable to our team.

Another huge benefit of opening up our code is that it actually makes it much easier to manage: It's trivial to connect other services, like [Travis][travis] or [Waffle][waffle]. Similarly, our own systems, (e.g.: [Jenkins][jenkins] jobs) don't need special access to consume the codebase. And we don't need to worry so much about carefully managing user permissions for read access inside the organisation.

All in all, working in the open has saved us a ton of time.

## Designing in the open

Shortly after we opened up [www.ubuntu.com][ubuntu], the design team also started [designing in the open][open-design].

[fsf]: https://www.fsf.org/ "The free software foundation"
[github-cws]: https://github.com/canonical-websites "canonical-websites GitHub organisation: Our website projects"
[github-cwt]: https://github.com/canonical-webteam "canonical-webteam GitHub organisation: Our supporting projects"
[github-ubuntu]: https://github.com/canonical-websites/www.ubuntu.com "The www.ubuntu.com codebase"
[open-design]: https://design.canonical.com/2017/04/designing-in-the-open/ "Design blog: Designing in the open"
[github]: https://github.com "GitHub: A place for code"
[django]: https://www.djangoproject.com "Django: A web framework written in Python"
[docker]: https://www.docker.com/ "Docker: Application containers"
[snap]: https://snapcraft.io "Snap: A universal packaging and distribution system"
[ubuntu]: https://www.ubuntu.com "The official Ubuntu website"
[firefox]: https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Introduction "Firefox: Contributing to the Mozilla code base"
[openssl]: https://github.com/openssl/openssl/blob/master/CONTRIBUTING "OpenSSL: Contributing guidelines"
[ubuntu-desktop]: https://www.ubuntu.com/desktop "Ubuntu Desktop"
[travis]: https://travis-ci.org/ "Travis: A continuous integration service"
[waffle]: https://waffle.io/ "Waffle: A kanban board for your GitHub issues"
[jenkins]: https://jenkins.io/ "Jenkins: An automation server"
