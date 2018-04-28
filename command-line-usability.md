I've been thinking about command-line terminal usability a lot recently.

People seem as inclined to ask [why the terminal exists][why-cli], as how to optimise it. I've also had it suggested to me that the discipline of User Experience (UX) has little to offer the Command-Line Interface (CLI), because the habits of terminal users are too inherent or instinctive to be defined and optimised by usability experts.

So as an experienced terminal user with a keen interest in usability, I'm going to try to lay out some of the patterns of thinking and behaviour that define my use of the CLI.

## Steps to learn a new CLI tool

New CLI tools I've learned recently include [snap][snap], [kubectl][kube] and [nghttp2][nh2], and I've also [dabbled][runscript] in writing command-line tools myself.

Below I'll map out an example of the steps I might go through when discovering a new command-line tool, as a basis for exploring how these tools could be optimised for CLI users.

1. Install the tool
    - First, I might try `apt install {tool}` (or `brew install {tool}` on a mac)
    - If that fails, I'll probably search the internet for "Install {tool}" and hope to find the official documentation
2. Check it is installed, and if tab-complete works
    - Type the first few characters of the command name (`sna` for `snap`) followed by `<tab> <tab>`, to see if the command name auto-completes, signifying that the system is aware of its existence
    - Hit space, and then `<tab> <tab>` again, to see if it shows me a list of available sub-commands, indicating that tab completion is set up correctly for the tool
3.  Try my first command
    - I'm probably following some documentation at this point, which will be telling me the first command to run (e.g. `snap install {something}`), so I'll try that out and expect prompt succinct feedback to show me that it's working
    - For basic tools, this may completes my initial interaction with the tool for now. For more complex tools like `kubectl` or `git` I may continue playing with it
4. Try to do something more complex
    - Now I'm likely no longer following a tutorial, instead I'm experimenting on my own, trying to discover more about the tool
    - If what I want to do seems complex, I'll straight away search the internet for how to do it
    - If it seems more simple, I'll start looking for a list of subcommands to achieve my goal
    - I start with `{tool} <tab> <tab>` to see if it gives me a list of subcommands, in case it will be obvious what to do next from that list
    - If that fails I'll try, in order, `{tool} <enter>`, `{tool} -h`, `{tool} --help`, `{tool} help` or `{tool} /?`
    - If none of those work then I'll try `man {tool}`, looking for a Unix manual entry
    - If that fails then I'll fall back to searching the internet again

## UX recommendations

From considering my own experience of CLI tools, I am reasonably confident the following recommendations make good general practice guidelines:

- Always implement a `--help` option on the main command and all subcommands, and if appropriate print out some help when no options are provided (`{tool} <enter>`)
- Provide both short- (e.g. `-h`) and long- (e.g. `--help`) form options, and make them guessable
- Carefully consider the naming of all subcommands and options, use familiar words where possible (e.g. `help`, `clean`, `create`)
- Be consistent with your naming - have a clear philosophy behind your use of subcommands vs options, verbs vs nouns etc.
- Provide helpful, readable output at all times - especially when there's an error (`npm` I'm looking at you)
- Use long-form options in documentation, to make commands more self-explanatory
- Make the tool easy to install with common software management systems (`snap`, `apt`, `brew`, or sometimes `npm` or `pip`)
- Provide [autocompletion][autocpl]. If it can't be installed with the tool, make it easy to install and document how to set it up in your installation guide
- Command outputs should be as user-friends and succinct as possible, and ideally make user of colours

Although I believe all of the above to be good general advice, I would very much welcome research to highlight the relative importance of addressing each concern.

### Outstanding questions

There are a number of further questions for which the answers don't seem obvious to me, but I'd love to somehow find out the answers:

- Once users have learned the short-form options (e.g. `-h`) do they ever use the long-form (e.g. `--help`)?
- For multi-level commands, do users prefer `{tool} {object} {verb}` (e.g. `git remote rm {remote_name}`), or `{tool} {verb} {object}` (e.g. `kubectl get pod {pod_name}`), or perhaps `{tool} {verb}-{object}` (e.g. `juju remove-application {app_name}`)
- What patterns exist for formatting command output? What's the optimal length for users, and what format do users find easiest to understand?

I'll try to write a more in-depth follow-up to this post when I've read a bit further on some of these topics.

[why-cli]: https://ux.stackexchange.com/questions/101990/why-are-terminal-consoles-still-used
[autocpl]: https://unix.stackexchange.com/questions/4738/an-easy-bash-completion-tutorial
[snap]: https://snapcraft.io/docs/core/usage
[kube]: https://kubernetes.io/docs/user-guide/kubectl-overview/
[nh2]: https://nghttp2.org/
[runscript]: https://github.com/canonical-webteam/practices/blob/master/local-development/the-run-script.md
[notusable]: http://gandre.ws/blog/blog/2015/04/07/why-the-command-line-is-not-usable/comment-page-1/
[patterns]: https://stackoverflow.com/questions/762724/cli-patterns-antipatterns-for-usability
[alive]: https://uxmag.com/articles/command-lines-alive-kicking
[programming]: http://blog.opalang.org/2012/03/programming-tools-ux-experience-how-we.html
[design]: https://trevorsullivan.net/2016/07/11/designing-command-line-tools/
[hacker]: https://news.ycombinator.com/item?id=3771000
[cliux]: https://ayende.com/blog/177762/command-line-usability
[skinning]: http://www.mi.fu-berlin.de/wiki/pub/SE/ThesisCommandLine/Skinning_the_Command_Line.pdf
