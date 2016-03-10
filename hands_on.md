class: center, middle

# Bachelor PO - RIOT in the Internet of Things

### Hands On

![:scale 70%](img/riot.png)

Hochschule für Angewandte Wissenschaften Hamburg

---

# Important Links

1. Code: [https://github.com/RIOT-OS/RIOT](https://github.com/RIOT-OS/RIOT)
2. Wiki: [https://github.com/RIOT-OS/RIOT/wiki](https://github.com/RIOT-OS/RIOT/wiki)
3. Mailing List: devel@riot-os.org
4. IRC: irc.freenode.org #riot-os

---

# First Steps

* Get a [GitHub](https://github.com) account
* [Fork](https://help.github.com/articles/fork-a-repo/) the [RIOT](https://github.com/riot-os/riot) repository
* Create a [branch](https://help.github.com/articles/creating-and-deleting-branches-within-your-repository/) for your work through the GitHub UI

---

# Development Environment

* Use a PC in the LAB
* **OR** setup your own development environment
  * [Git](https://git-scm.com/downloads)
  * [VirtualBox + Extensions](https://www.virtualbox.org)
  * [Vagrant](https://www.vagrantup.com)

*The vagrant image created by RIOT already includes most compilers and tools for flashing.*

---

# Try an Example

* Open a terminal
* Get the code & switch to your branch

```sh
$ git clone https://github.com/USERNAME/RIOT.git
$ cd RIOT
$ git checkout <working_branch>
```

* Start vagrant

```sh
$ vagrant up
$ vagrant ssh
```

* Compile and flash an example

```sh
$ cd RIOT/examples/hello-world
$ # Connect a Atmel SAM R21 Xplained Pro board via USB
$ BOARD=samr21-xpro make all flash term
```

---

# Application Output

* Press the reset button on the board
* You should see a `Hello World!` message
* Congratulations, you just flashed your first RIOT application! :-)

---

# Create Your Own Project

* Copy the `hello-world` files to your project folder
* Sync your project folder using the VirtualBox UI
* OR sync it via the `Vagrantfile` in RIOT

```sh
...
config.vm.synced_folder ".", "/home/vagrant/RIOT"
# Add this line, syncing your PROJECT folder
# to /home/vagrant/PROJECT
config.vm.synced_folder "/path/to/PROJECT", "/home/vagrant/PROJECT"
...
```

---

# Add a Blinking LED

* Edit `main.c` and add new includes ...

```C
#include "board.h"
#include "xtimer.h"
```

* ... and code for the LEDs

```C
for(int i = 0; i < 10; i++) {
    puts("LED on");
    LED_RED_ON;
    xtimer_sleep(1);
    puts("LED off");
    LED_RED_OFF;
    xtimer_sleep(1);
}
```

---

# Adjust the Makefile

* Rename you application

```sh
APPLICATION = my_project
```

* Include the xtimer module

```sh
USEMODULE += xtimer
```

---

# Flash and start your project

* Reload and connect to vagrant

```sh
$ cd /path/to/RIOT/
$ vagrant reload
$ vagrant ssh
```

* Compile and flash your project

```sh
$ cd your/project
$ BOARD=samr21-xpro make all flash term
```

* Press the reset button
* In addition to the message, you should see a blining LED

---

# HOWTO: Track Changes with Git

* Set your name and email

```sh
$ git config --global user.email "you@example.com"
$ git config --global user.name "Your Name"
```

* Look at your changes

```sh
$ git status
```

* Add, commit and push files

```sh
$ git add FILE_1 FILE_2
$ git commit
$ git push
```

* Reset an uncommited file to the upstream

```sh
$ git checkout FILE
```

---

# HOWTO: Update Your Fork

* RIOT regularly receives updates in form of pull requests.
* To update your fork:
  * update your master branch
  * rebase your working branch to your master.

```sh
$ git checkout master
$ git pull https://github.com/RIOT-OS/RIOT.git
$ git checkout <working_branch>
$ git rebase master
```

---

# Git Help

There are various sites online that explain git. Here are a few we like:

* [https://git-scm.com/doc](https://git-scm.com/doc)
* [http://githowto.com/](http://githowto.com/)
* [https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
* [http://www.learnenough.com/git-tutorial](http://www.learnenough.com/git-tutorial)

---

class: center, middle
![:scale 100%](img/riot.png)
# www.riot-os.org
