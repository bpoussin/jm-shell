# jm-shell #

My extensive, customized Bash shell.


## Features ##

### Divider / Status  Line ###

This is a dark grey line that divides the last command from the prompt. It also
shows some relevent info about the last command and the current environment.

* helpful colors and divider to separate commands
* time last command finished on the right
* shows error code of last command, if any
* shows total time of last command if over 4 seconds
* shows if inside Vim, Midnight Commander, or [Desk](https://github.com/jamesob/desk)
* shows current system load average if over 1
* shows a battery charge status if laptop battery is less than full

### Current Location / Status Line ###

* shows username@hostname:location
* shows number of items in current directory
* current directory is in grey if not writeable
* shows number of running background jobs on the left, if any
* gives info on source code repositories if current dir is in one

### Prompt ###

The Prompt is a simple, bold yellow dollar sign. When you are typing the
command text is standard grey. After you enter a command, it gets redrawn in
bold yellow to make it easy to pick out visually when you’re scrolling back.

### Background Jobs ###

It keeps history entries unique, up to date among all open shells and with most
recent commands last (at the bottom).

It also maintains a shell log file in `~/.local/share/bash/shell.log`

The regular bash history file has only unique commands for reverse history
searching. The shell log is a full history of your shell activity for
reference.

Shell log entries look like this:

    Sun Apr  8 06:48:19 EDT 2018	/home/jmcclare	nvim ~/.config/user-dirs.dirs 

Each entry lists the time the command was entered, the command’s current
working directory, and the command. The fields are tab separated.

Both the history and the shell log file omit logging commands that begin with a
space. This is the same as Bash’s `ignorespace` or `ignoreboth` options, but it
ignores spaced commands no matter how those are set.

### Other Included Prompt Styles ###


#### standard ####

The default Bash color prompt style. Setting this style also skips the
background jobs. It’s a bit better for performance on an overloaded system.

#### tweaked ####

A slight tweak of the default Bash color prompt style. Unlike the standard, it
also runs the background jobs.

#### extensive ####

The default style described above.

#### minimal ####

Nothing but a grey dollar sign prompt. Also doesn’t run the background jobs. A
bit better for performance on an overloaded system.

#### kirby ####

Turns your prompt into a dancing Kirby!

    <('.'<)
    ^('.')^
    (>'.')>
    ^('.')^

#### erection ####

Another not‐so‐useful prompt. I’ll let you guess what it looks like. Don’t use
it for too long or you’ll run out of screen space.

#### divider ####

A the line prompt similar to the extensive style, but it uses only standard
Bash prompt variables. A bit better for performance than the extensive style.


## Installation ##

Copy all files to `~/.local/lib/bash`

Add the following to your `~/.bashrc`

    source ~/local/lib/bash/ps1`

If you are using anything that adds something to your Bash `$PROMPT_COMMAND`
like [fzf](https://github.com/junegunn/fzf), make sure you source this before
you append anything else to it. This prompt command this PS1 adds must be the
first part of your `$PROMPT_COMMAND`.


## Configuration ##

You can set one of the other styles any time, or in your `~/.bashrc` by setting
`prompt_style`, like this:

    prompt_style=kirby

The default prompt style is `extensive`.

You can change the location of the shell log file by setting `$BASHSHELLLOGFILE`.

    BASHSHELLLOGFILE=~/.bash-shell.log

The history updater uses the standard Bash variables `HISTFILE`,
`HISTFILESIZE`, and `HISTSIZE`. It assumes `HISTCONTROL` is set to
`ignoreboth:erasedups` and it does a better job that both of those options
normally do.