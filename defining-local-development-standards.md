# The ./run executable: Simplifying local development

There are 9 full-time developers in Canonical's webteam (part of the [Design team][team]), yet we manage [over 18 websites][sites-blog] as well as [many supporting projects][gh-webteam] and [frameworks][vf]. These projects may depend on any combination of [Python][python], [Ruby][ruby], [NodeJS][https://nodejs.org/en/], [Go][https://golang.org/], or none of them.

Most devs will touch most of these projects at some point, and some may work on a few of them in any given day. And before we can start a new piece of work, we need to get the projects running on our computers. These computers may be running any flavour of Linux or macOs (thankfully we haven't yet needed to build support for Windows).

## A focus on tooling

If you've ever tried to get up and running on a new software project, you'll certainly appreciate how difficult that can be. Given the diversity of projects we work on, and how often we switch between them, this is a delay we simply cannot afford.

![Will it work?](https://imgs.xkcd.com/comics/will_it_work_2x.png)

This is why we've invested a lot of time into refining and standardising the local development tooling, making it as easy as possible for any of our devs, or any contributors, to get up and running as simply as possible.

## The interface

The first consideration for us was the interface - a standard set of commands that developers can run on all projects to achieve predictable results:

``` bash
./run        # An alias for "./run serve"
./run serve  # Prepare the project and run the local server
./run build  # Build the project, ready for distribution or release
./run watch  # Watch local files for changes and rebuild as necessary
./run clean  # Remove any temporary or built files or local databases
```

We only recently decided on using [a single `run` executable][run-script] as our single entry-point into all our projects. We previously tried and eventually rejected a few alternative options for our standard interface:

- [A Makefile][makefile]: The syntax can be confusing. Makefiles are really made for compiling system binaries, which doesn't apply to us.
- [gulp][gulp], or [NPM scripts][npm-scripts]: Not all our projects need NodeJS, and NodeJS isn't always installed always locally installed.
- [docker-compose][docker-compose]: Although we ultimately use Docker for everything (see below), the `docker-compose` entrypoint alone doesn't let us do all the operations we need to successfully run all our projects.

With the `run` script, we are free to perform whatever actions we need. Furthermore, we can use any available interpreter that's available on the local system - we currently use [Bash][bash] because it's universally available on all the systems we care about (Linux and macOs). As a small bonus, `./run` is quicker to type than the other options, saving our devs [crucial nanoseconds][nanoseconds].

Knowing we can run or build our projects through this standard interface is not only useful for our developers, but also for supporting services - e.g. like our CI jobs. We can write general solutions, and know they'll be able to work with any of our projects.

## Encapsulation and virtualisation

Although we strive to keep our projects as simple as possible, every software project relies on dependent libraries and programs. These dependencies pose 2 problems for us:

- We need to install and run these dependencies in a predictable way - which may be difficult in some operating systems
- We must keep these dependencies from effecting the developer's wider system

For a while now, developers have been solving this problem by running applications within [virtual machines][vms] running Linux (e.g. with [VirtualBox][vb] and [Vagrant][vagrant]).

## Docker containers

More recently, [containers][lxc] have entered the scene. A container is a part of the existing system with carefully controlled permissions and an encapsulated filesystem, to make it appear and behave like a separate operating system. Containers are much lighter and quicker to run than a full virtual machine, and yet provide similar benefits, at least for our purposes.

![containers](https://assets.ubuntu.com/v1/f581fd89-containers.png)

The most direct and easy to use way to run containers is probably [LXD][lxd], but unfortunately there's no easy way to run LXD on macOs. By contrast, [Docker CE][docker-ce] is trivial to install and use on macOs, and so this became our container manager of choice. When it becomes easier to run LXD on macOs, we'll revisit this decision.

![docker cat](https://assets.ubuntu.com/v1/52a306c7-docker-cat.png)

Running containers through Docker help us to carefully manage our projects' dependencies, by:

- Keeping all our software, from Python modules to databases, from affecting the wider system
- Logically grouping our dependencies into separate light-weight containers: one for the database, and a separate one for each technology stack (e.g.: Python, Ruby, Node etc.)
- Easily cleaning up a project by simply deleting its associated containers

So each of our `./run` script runs

[team]: https://design.canonical.com/team "The design team at Canonical"
[sites-blog]: https://design.canonical.com/?p=40483 "Our open source websites | Ubuntu Design blog"
[gh-webteam]: https://github.com/canonical-webteam/ "Our GitHub organisation: Canonical Webteam"
[vf]: https://github.com/vanilla-framework/ "Our GitHub organisation: Vanilla Framework"
[run-script]: https://github.com/nottrobin/practices/blob/run-script/local-development/the-run-script.md "Webteam practices: The run script"
[makefile]: https://en.wikipedia.org/wiki/Makefile "Wikipedia: Makefile"
[gulp]: http://gulpjs.com/ "GulpJS"
[docker-compose]: https://docs.docker.com/compose/ "Docker compose"
[bash]: https://en.wikipedia.org/wiki/Bash_(Unix_shell) "Wikipedia: Bash (Unix shell)"
[npm-scripts]: https://docs.npmjs.com/cli/run-script "NPM: The run-script command"
[nanoseconds]: https://www.youtube.com/watch?v=JEpsKnWZrJ8 "Admiral Grace Hopper on nanoseconds"
[vagrant]: https://www.vagrantup.com/ "Vagrant: Scripting virtualisation for development"
[lxc]: https://linuxcontainers.org/ "Linux containers"
[vb]: https://www.virtualbox.org/ "VirtualBox"
[vms]: https://en.wikipedia.org/wiki/Virtual_machine "Wikipedia: Virtual machine"
[lxd]: https://linuxcontainers.org/lxd/getting-started-cli/ "Getting started with LXD: A container hypervisor and a new user experience for LXC"
[docker-ce]: https://www.docker.com/community-edition "Docker Community Edition"
