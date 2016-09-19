class: center, middle, riot

# RIOT im Internet of Things

## Github Introduction

Cenk Gündogan, Peter Kietzmann, [Sebastian Meiling](mailto:sebastian.meiling@haw-hamburg.de), Thomas C. Schmidt

![:scale 50%](img/riot.png)

[iNET](http://www.inet.haw-hamburg.de), Department Informatik, HAW Hamburg

---

## Getting Started

### Configure GIT

* Get a [GitHub](https://github.com) account, and sign in

* Install GIT on your Laptop, Mac, or PC
    * on Windows use [scm-git](https://git-scm.com/download/win)
    * on Linux use package manager: `apt`, `pacman`, `yum`, `zypper`
    * on macOS `git` preinstalled, or use: `macports`, `brew`

* Configure GIT environment with your name and email:

```Shell
$ git config --global user.email "you@example.com"
$ git config --global user.name "Your Name"
```

---

## Getting Started

### Important Links

* Code: [https://github.com/RIOT-OS/RIOT](https://github.com/RIOT-OS/RIOT)
* Wiki: [https://github.com/RIOT-OS/RIOT/wiki](https://github.com/RIOT-OS/RIOT/wiki)
* Mailing List: devel@riot-os.org
* IRC: irc.freenode.org #riot-os

### Git Help

* [https://help.github.com/articles/set-up-git/](https://help.github.com/articles/set-up-git/)
* [https://git-scm.com/doc](https://git-scm.com/doc)
* [http://githowto.com/](http://githowto.com/)
* [https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
* [http://www.learnenough.com/git-tutorial](http://www.learnenough.com/git-tutorial)

---

## Contribute to RIOT

* Fork RIOT into your own account via [Github](https://github.com/RIOT-OS/RIOT)

* Clone your RIOT fork, and create a branch for development

```Shell
$ git clone https://github.com/USERNAME/RIOT.git
$ cd RIOT
$ git checkout -b <develop branch>
```

* make your patches, changes, additions to RIOT

* Example: fixing typos
    * `dist/tools/vagrant/REAMDE.md`: ~~reproducable~~ : reproducible
    * `dist/tools/tunslip/README.md`: ~~unnessarily~~ : unnecessarily

---

## Verify and publish your changes

* build and test your code

* commit everything and push to Github

```Shell
git status
git add <changed files>
git commit
git push
git push --set-upstream origin <devel branch>
```

* make a pull request, wait for CI okay, and someone to merge

---

## Update Your Fork

* RIOT regularly receives updates in form of pull requests.

* To update your fork:
  * update your master branch with RIOT master
  * rebase your working branch to your master.

```Shell
$ git checkout master
$ git pull --rebase https://github.com/RIOT-OS/RIOT.git
$ git checkout <working_branch>
$ git rebase master
```

---

## Build a RIOT application

### Init and clone code repository
* Create your own project repository on [Github](https://github.com/smartuni/)
    * choose a license, and
    * add a README file

* Clone the repository

```Shell
$ git clone https://github.com/USERNAME/hello-riot
$ cd REPO
```

---

### Add some code
* create a simple Makefile

```Make
APPLICATION = hello-riot
BOARD ?= native
include $(RIOTBASE)/Makefile.include
```

* add your application code

```C
#include <stdio.h>

int main(void)
{
    puts("Hello RIOT!");

    printf("You are running RIOT on a(n) %s board.\n", RIOT_BOARD);
    printf("This board features a(n) %s MCU.\n", RIOT_MCU);

    return 0;
}
```

---

### Test your application
* build and run your code with RIOT-OS

```Shell
$ RIOTBASE=/path/to/RIOT make
$ ./bin/native/hello-riot.elf
```

* application output:

```Shell
RIOT native interrupts/signals initialized.
LED_RED_OFF
LED_GREEN_ON
RIOT native board initialized.
RIOT native hardware initialization complete.

main(): This is RIOT! (Version: 2016.10-devel-199-g0d901-ws-86-209.haw-1x.haw-hamburg.de)
Hello RIOT!
You are running RIOT on a(n) native board.
This board features a(n) native MCU.

```
---

## Github project environment

* provide a [README](https://github.com/smartuni/examples), showing how to use and build your project
    * simple, brief; for everything else use the Wiki

* use Github features such as Wiki, Issues, and Pull Request to collaborate
    * Wiki: collect further information
    * Issues: report problems, track todos
    * Pull Request: propose changes, fixes etc.  

* use Github [pages](https://pages.github.com/) to create project [website](http://smartuni.github.io/examples)
    * create simple webpage from README

* remember: it's recommended to choose a license (GPL, MIT, ...)

---

class: center, middle, riot
[![:scale 100%](img/riot.png)](http://www.riot-os.org)
## [www.riot-os.org](http://www.riot-os.org)
