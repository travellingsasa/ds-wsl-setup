
# TOC
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [TOC](#toc)
- [1. Some definitions](#1-some-definitions)
- [2. Installing windows linux subsystem and a linux distribution](#2-installing-windows-linux-subsystem-and-a-linux-distribution)
  - [2.1 Changing the default wsl user](#21-changing-the-default-wsl-user)
  - [2.1 Add linux distribution as network drive](#21-add-linux-distribution-as-network-drive)
  - [2.2 Changing the default home directory Windows Terminal](#22-changing-the-default-home-directory-windows-terminal)
  - [2.3 Changing the default home directory VS Code](#23-changing-the-default-home-directory-vs-code)
- [3. Installing windows terminal, zsh, oh-my-zsh and zsh themes](#3-installing-windows-terminal-zsh-oh-my-zsh-and-zsh-themes)
- [Upgrade python on wls](#upgrade-python-on-wls)
- [Python, pyenv and the wonderful world of virtual environments](#python-pyenv-and-the-wonderful-world-of-virtual-environments)
  - [1. Install pyenv](#1-a-nameinstallpyenvainstall-pyenv)
  - [2. Install Python versions](#2-a-nameinstallpythonversionsainstall-python-versions)
    - [2.1. Creating virtual environments with pyenv and venv](#21-a-namecreatingvirtualenvironmentswithpyenvandvenvhttpsdocspythonorg3tutorialvenvhtmlacreating-virtual-environments-with-pyenv-and-venvhttpsdocspythonorg3tutorialvenvhtml)
- [Install Homebrew (optional or when needed)](#install-homebrew-optional-or-when-needed)
  - [3. Install pyenv via homebrew](#3-a-nameinstallpyenvviahomebrewainstall-pyenv-via-homebrew)
- [Add alias to zsh config file](#add-alias-to-zsh-config-file)
- [Running jupyter lab after installation](#running-jupyter-lab-after-installation)
  - [4. Install vscode or vscode-insiders](#4-a-nameinstallvscodeorvscode-insidersainstall-vscode-or-vscode-insiders)

<!-- /code_chunk_output -->



# 1. Some definitions
The terminal usually refers to a [terminal emulator program](https://www.ttwin.com/blog/333-terminal-emulator), which provides the window that displays the shell and allows you to interact with it. Usually a blinking courser marks the input line. This line is called the "prompt" or the "command line".   The shell is a program which interprets the user input. Also called a "command line interpreter".

# 2. Installing windows linux subsystem and a linux distribution
<img src="https://docs.microsoft.com/en-us/windows/images/windows-linux-dev-env.png" alt="wsl" width="400" height="263">

Since Windows 10, Windows comes with a linux subsystem (wls) which allows you to run linux on your windows machine. This subsystem was upgraded 2021 for performance enhancements and is called wls2. It is up to you which version you want to install. The following link shows you how to install wls and upgrade to wls2.
[Follow these steps.](https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-3---enable-virtual-machine-feature)


If you installed wls2, you might want to check if the right version is active. You can do this following this link. 
[Check wls version.](https://askubuntu.com/questions/1177729/wsl-am-i-running-version-1-or-version-2)


## 2.1 Changing the default wsl user
Depending on how you installed wsl you might want to change the default user from root to your username.

```bash
ubuntu config --default-user new_user_name
```

## 2.1 Add linux distribution as network drive
Open the file explorer and serch for 
```
\\wsl$
```
this will open the linux distribution path from windows.

Right click on your distro directory icon and choose "Connect network drive". Choose a drive letter and press ok. You should see a new network icon. You can rename it to Linux or something.

## 2.2 Changing the default home directory Windows Terminal
You should change your home directory if it is located on the windows system and looks like this.
```
/mnt/c/Users/username
```

Open the JSON file via the Windows Terminal settings and search for 
```
"source": "Windows.Terminal.Wsl 
```

 then add this line below
```
,"startingDirectory":"\\\\wsl$\\Ubuntu\\home\\your_username"
```

## 2.3 Changing the default home directory VS Code
Open the VS Code settings and search for 
```vscode
Terminal:integrated:cwd
```
and enter your new network path to the box

```vscode
U:\home\username
```


# 3. Installing windows terminal, zsh, oh-my-zsh and zsh themes
<img src="https://user-images.githubusercontent.com/21205508/118002859-5204de00-b348-11eb-8ff7-714cf530a656.png" alt="alt text" width="400" height="263">


In the previous step we've installed a linux distribution. This distro comes with it's own linux terminal and shell. You can either work with this setup or install new terminals and shells with additional features. We will install here the "Windows Terminal". This terminal has a nice "tab" functionality which let's you choose if you want to start the ubuntu terminal, the powershell or other installed terminals. 
Most linux distros come with the bash shell preinstalled. But what is bash?

Akiva Amit, Software Developer and Network Manager
Answered August 26, 2018 on https://www.quora.com/Why-is-it-important-that-GNU-Linux-distros-have-a-BASH-shell?share=1

"There are different shell programs available for Linux (Bash, Dash, Tcsh, Ksh, Zsh, Fish, csh, and others) and they all do pretty much the same thing in terms of executing user commands. However, a Linux shell is also a scripting programming language and the different shells don’t all have the same syntax and ways of setting variables and keeping defaults. Since many scripts included in a LInux distribution are written for Bash it important to have a Bash executable (or compatible equivalent) available to properly process them.

Oh yeah. Bash stands for Bourne Again Shell, so saying “Bash shell” is wrong. It is just Bash. Stephen Bourne (not Jason) designed one of the popular shells available in original Unix and his shell program was just called “sh”, as were others at that time. Bash is supposed to be an improved free version of that shell."

So bash is just another shell :)

Here we will install the zsh 'z shell' and the oh-my-zsh. oh-my-zsh is a zsh framework that let's you configure your zsh. It comes with zsh plugings i.e. syntax highlighting and it let's you add colored themes. 

---
**NOTE**: You can change themes in zsh, bash and the windows terminal itself. This might lead to some confusion here, so always check if what you are doing is what you want to do :) **Please read read the whole section up to 'Installing python on wls' before executing any commands!**


Here are 4 links which you can follow. The first two show you how to install Windows Terminal, zsh and oh-my-zsh. But they diverge when it comes to fonts and the zsh themes. The third link shows you how to install themes in the windows therminal (not zsh). And the last link shows you how to install the cross- shell starship theme.

**NOTE**: Changing themes in wls or mac os is different. When you change a theme in mac os, the changes are applied to everything you see in the terminal. This is different in windows. The changes here are mostly for the prompt. Command specific outputs like the output of "ls" might be unchanged. 
Link 2 shows you how to change these dircolors too.

1. [Nerd font and powerlevel10k theme](https://www.the-digital-life.com/awesome-wsl-wsl2-terminal/)  
Additionally the post shows you how to install or enable plugins in zsh

2. [Powerline font, angnoster theme from oh-my-zsh and dircolors](https://blog.joaograssi.com/windows-subsystem-for-linux-with-oh-my-zsh-conemu/)  
Agnoster ist just one of many different themes which come preinstalled in oh-my-zsh. Check out the others in  this directory ~/.oh-my-zsh/themes.

3. [Windows terminal theme without zsh](https://dev.to/nicole/windows-terminal-port-a-scheme-from-iterm2-customise-your-own-scheme-and-use-a-custom-font-fga)  
Uses popular themes from mac os iterm2 terminal.

4. [Starship theme](https://starship.rs/guide/#%F0%9F%9A%80-installation) 🚀



I personally use the windows terminal, with the firamono nerd font and starship. Do whatever you like. If this is overwhelming stick to number one, two or use my routine:


Update packages
```
sudo apt update
```

Install zsh
```
sudo apt install zsh -y
```

Make zsh the default shell. Enter 
```
chsh -s /bin/zsh
```
and follow the prompt.




Install oh-my-zsh
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Check if the correct shell is active 
```
echo $Shell
```
It should say something like "/usr/bin/zsh".

Install or enable plugins in zsh. Firs clone the plugins and then add them to your zsh config file.

Auto-suggestion plugin
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Syntax-highlighting plugin
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
my-zsh/custom}/plugins/zsh-autosuggestions
```
Add plugins to zsh config file:

```
vim ~/.zshrc
```
Find plugins=(git) and change it to.
```
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```
Then activate the new changes with
```
source ~/.zshrc 
or
exec $SHELL
```
Don't forget to do this everytime you change something in zsh. Similarly, do source ~/.bashrc or source ~/.profile if you change something in these files.


Install starship
```
sh -c "$(curl -fsSL https://starship.rs/install.sh)"
```

Add starship to zsh config file. By adding this at the end of ~/.zshrc.  
Some people also recommend to comment out this line ZSH_THEME="theme name"

``` 
export eval "$(starship init zsh)" >> ~/.zshrc
```

[Troubleshooting starship install](https://denysdovhan.com/spaceship-prompt/docs/Troubleshooting.html)

Change system commands color scheme. 
1. Copy pretty schemes from another terminal (iterm) from [here](https://github.com/mbadolato/iTerm2-Color-Schemes)
2. Unzip dir
3. Go to "iTerm2-Color-Schemes-master/windowsterminal"
4. Here are json file which we can copy and add to windows terminal.
5. Open one of these files in any text editor and copy the content.
6. Open the preference menue of the Windows Terminal.
7. Select the "open JSON file" button on the bottom left of the preference window.
8. If you have to choose, select any text editor that opens JSON files.
9. Search for "schemes": and paste your copied color scheme here.
10. Save the file.
11. Go back to the Windows Terminal preference window.
12. Select the ubuntu terminal on the left side.
13. Choose style from the context menue and just added color scheme.

Fine tuning.

I choose Atom.json from the iterm color schemes. But now the autosuggestion color is too dark.
![ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE](https://user-images.githubusercontent.com/21205508/117886960-42d25180-b2b0-11eb-9783-07dc644ec550.PNG)
 
14. We can fix this by tweaking the zsh-autosuggest-highlight plugin. Open the zsh config file ~/.zshrc and add this line under the plugin line.
```
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=244'
```
The default is set to fg=8. You can play around with other [colors](https://coderwall.com/p/pb1uzq/z-shell-colors).

This looks better.  
![fixed_ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE](https://user-images.githubusercontent.com/21205508/117890479-854a5d00-b2b5-11eb-955f-bd23b3fa4dee.PNG)

Now, some programs still use the deafualt linux bash color scheme. This is very annoying after all these changes. Say we want to list the contents of a directory with ls. This would look like this. Just unreadable.  
![ls_colors](https://user-images.githubusercontent.com/21205508/117890670-ea9e4e00-b2b5-11eb-97b1-d44c4a14c103.PNG)


15. Change default bash colors 
Print default dircolors as table and save it as dir_colors. Then open ~/.dir_colors to see the color schemes.
```
dircolors --print-database > ~/.dir_colors
```
Printing it with the database option is nice because the actual colors are shown. We see that we have to change the STICKY_OTHER_VARIABLE. 
![dir_colors](https://user-images.githubusercontent.com/21205508/117891015-7912cf80-b2b6-11eb-8243-5a06729b1db9.PNG)

I will change a couple of colors. Like so.  
![dir_colors](https://user-images.githubusercontent.com/21205508/117896447-e297db80-b2c0-11eb-8574-eb17a1273d5d.PNG)


You can find more information about the dircolors [here](https://askubuntu.com/questions/466198/how-do-i-change-the-color-for-directories-with-ls-in-the-console), [here](https://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-ls), [here]( https://www.howtogeek.com/307899/how-to-change-the-colors-of-directories-and-files-in-the-ls-command/ ), [here](https://github.com/romkatv/powerlevel10k/issues/805) and [here](https://bbs.archlinux.org/viewtopic.php?id=259958)

To activate the changes add this to the ~/.zshrc file. The command checks if /usr/bin/dircolors exists and is executable (-x) then checks if ~/.dir_colors exists and is readable (-r). If it is readable it will use the dir_colors file else the system dircolors file.
```
# config bash color scheme
if [ -x /usr/bin/dircolors ]; then
        [ -r ~/.dir_colors ] && eval "$(dircolors -b ~/.dir_colors)" || eval "$(dircolors -b)"
fi
```
Better.    
![fixed_ls_colors](https://user-images.githubusercontent.com/21205508/117896540-0fe48980-b2c1-11eb-9e88-80402adf5924.PNG)


Alternatively use somebody [else's](https://github.com/seebi/dircolors-solarized) color scheme.

---

# Upgrade python on wls
Python2 is preinstalled on the windows linux subsystem. If we would update all packages, the promp would tell us that we can upgrade python2 to python3.

Type the following into your prompt:
```
sudo apt update && upgrade
sudo apt install python3-pip
```

The last line installs python's package manager "pip".

Without creating an alias, you need to specify which python and pip version you want to execute i.e. python3 and pip3. An alias is essentially nothing more than a keyboard shortcut to a sequence of commands that ist saved in the bash profile or the zsh config file. We will make one later.

Check with python version if the new packages are installed:
```
python3 --version
pip3 --version
```

# Python, pyenv and the wonderful world of virtual environments

##  1. <a name='Installpyenv'></a>Install pyenv
We will use pyenv and virtual environments to install, organize and manage different versions of Python (and other libraries) on your computer.  
~~Install instructions copied from the pyenv github [page] https://github.com/pyenv/pyenv#installation)~~
~~1. Check out pyenv where you want it installed. A good place to choose is $HOME/.pyenv (but you can install it somewhere else).~~

We will use the Pyenv-installer instead.
[This will install pyenv along with a few plugins that are useful:](https://realpython.com/intro-to-pyenv/#installing-pyenv)
```diff
- git clone https://github.com/pyenv/pyenv.git ~/.pyenv
+ curl https://pyenv.run | bash
```

This will add additional functionalities.

pyenv: The actual pyenv application   
pyenv-virtualenv: Plugin for pyenv and virtual environments  
pyenv-update: Plugin for updating pyenv  
pyenv-doctor: Plugin to verify that pyenv and build dependencies are installed  
pyenv-which-ext: Plugin to automatically lookup system commands  
[source](https://realpython.com/intro-to-pyenv/#installing-pyenv)

~~Optionally, try to compile dynamic bash extension to speed up pyenv. Don't worry if it fails; pyenv will still work normally:~~
```diff
-cd ~/.pyenv && src/configure && make -C src
```


2. Define environment variable PYENV_ROOT to point to the path where pyenv repo is cloned and add $PYENV_ROOT/bin to your $PATH for access to the pyenv command-line utility.
For bash/Zsh:
```diff
- echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
- echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
- echo 'eval "$(pyenv init --path)"' >> ~/.profile

+ export PATH="$HOME/.pyenv/bin:$PATH" >> ~/.zshrc
+ eval "$(pyenv init -)" >> ~/.zshrc
+ eval "$(pyenv virtualenv-init -)" >> ~/.zshrc
```

3. Add pyenv init to your shell to enable shims and autocompletion. Please make sure eval "$(pyenv init -)" is placed toward the end of the shell configuration file since it manipulates PATH during the initialization.

For bash:
```
echo 'export PATH="$HOME/.pyenv/bin:$PATH"'
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.profile
```
For Zsh:
```
echo 'export PATH="$HOME/.pyenv/bin:$PATH"'
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
```
General warning: There are some systems where the BASH_ENV variable is configured to point to .bashrc. On such systems you should almost certainly put the above mentioned line eval "$(pyenv init -)" into .bash_profile, and not into .bashrc. Otherwise you may observe strange behaviour, such as pyenv getting into an infinite loop. See #264 for details.

Suggested build environment for pyenv on [Ubuntu](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)
```
sudo apt-get update; sudo apt-get install make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```
[](#)
##  2. <a name='InstallPythonversions'></a>Install Python versions

After you installed pyenv you can easily install different Python versions. If you want to see a list of all available versions and flavors you can use the following command:

```
pyenv install --list
```

We will use Python 3.8.5 mainly here. You can install it with:

```
pyenv install 3.8.5     
```

To set a specific version as the local (inside a directory) or global (everywhere) Python version you can use:

```
pyenv local 3.8.5
pyenv global 3.8.5
```
[](#)
###  2.1. <a name='Creatingvirtualenvironmentswithpyenvandvenvhttps:docs.python.org3tutorialvenv.html'></a>Creating virtual environments with pyenv and [venv](https://docs.python.org/3/tutorial/venv.html) 

Another way of creating virtual environments is tu use the module `venv`. First of all move to the directory for which you want to create the virtual environment. Make sure you use the desired Python version either locally in this directory or globally (you can check the Python version either with `python --version` or `which python`). To set the local Python version and create a new environment you can use the following commands:

```BASH 
$ pyenv local 3.8.5
$ python -m venv .venv
```

It will create a new hidden folder called `.venv` to store all  necessary files inside the directory. You could also replace .venv with a whole path where you want to save your environment. But we want to create our virtual environments inside our project folders. 
You can now activate the environment with: 

```BASH 
$ source .venv/bin/activate
```

If you want to deactivate it run:

```BASH 
$ deactivate
```

In order to use the real power of virtual environments we need to know how to install packages inside a specific environment. We can use a package installer for Python packages called Pip. The good news is: its already installed. We can simply run the command 

```BASH 
$ pip install <package_name>
```

and Pip will look for the latest version of the package in the Python Package Index (PyPI), calculate the dependencies and install all of them to ensure the new package will work flawlessly. 

There is another way of installing packages inside an environment. Let's asume you want to create the same environment as someone else is using with exactly the same package versions. In this case you don't need to install them by hand. You can also use a `requirements.txt` file. Make sure the file is located in the directory where you want to create your environment. The steps for creating and activating the environment are the same as shown above, but for installing the packages you can run: 

```BASH 
$ pip install -r requirements.txt
``` 

Of course, you can also create a requirements.txt file yourself. Activate an environment where you have installed some packages. With the following commands, you can either print a list of packages and their version numbers or write the output directly to a file named `requirements.txt`.

```BASH
# shows list of packages
$ pip freeze   
# writes list to file 
$ pip freeze > requirements.txt     
```
[](#)
# Install Homebrew (optional or when needed)
[Homebrew](https://brew.sh/) is a package manager that installs the stuff you need that your Linux distro didn’t. We need homebrew to install pyenv. Run this from the command line.
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
Then add homebrew to the path:
```
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/USERNAME/.profile
```

```
eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)

```

Install the Homebrew dependencies if you have sudo access:
```
sudo apt-get install build-essential
```
Homebrew recommends that we install GCC
```
 brew install gcc
```
Follow any other instructions given by Homebrew.


> You may wonder what the difference is between using `brew` and `pip`. They are both package installers, but brew, which is based on Ruby and Git, can be used to install all kinds of software packages, while pip, which is written in Python, can only be used to install Python packages. The main difference, however, is that brew installs packages globally and it cannot be used to install something only in a specific virtual environment. To install a package only locally in an environment you have to use pip!
[](#)
##  3. <a name='Installpyenvviahomebrew'></a>Install pyenv via homebrew

[Pyenv](https://github.com/pyenv/pyenv) is a simple Python version management tool you can download for free using homebrew. 

```
brew update
brew install openssl readline sqlite3 xz zlib
brew install pyenv
```

After you installed pyenv you need to add another line to the .zshrc file. Open the file and add the second line somewhere nearly at the bottom of the file: 

```
vim ~/.zshrc
eval "$(pyenv init -)"
```

[](#)
# Add alias to zsh config file
```
alias setup_python385="pyenv local 3.8.5 &&  
python3 -m venv .venv &&
source .venv/bin/activate &&
python3 -m pip install --upgrade pip setuptools wheel &&
python3 -m pip install -r requirements.txt"

alias setup_python395="pyenv local 3.9.5 &&
python3 -m venv .venv &&
source .venv/bin/activate &&
python3 -m pip install --upgrade pip setuptools wheel &&
python3 -m pip install -r requirements.txt"
```
For more useful aliases [see](https://opensource.com/article/19/7/bash-aliases)


[](#)
# Running jupyter lab after installation
We will run jupyter lab without the browser window because this doesn't work in wls. After running the command, follow the prompt and copy paste the address into your browser.

```
jupyter lab --no-browser
```
[](#)
##  4. <a name='Installvscodeorvscode-insiders'></a>Install vscode or vscode-insiders
vscode is a cross language IDE. Many people like it so let's have a try. Download the windows version of vscode from [here](https://code.visualstudio.com/download) and install it.

Once installed we need to set the default terminal to zsh and add the nerd font to it. To do this open the "Command Palette" by pressing

```
ctrl + shift + P   or   F1
```

and search for 

```
Terminal:Select default profile
```

 and select zsh.
This will set the zsh as default shell. Now we have to add the nerd font so that all the icons are displayed correctly.

Open a new terminal under 

```
Terminal > New Terminal
```
A new terminal should open that looks like this



On the top right of the terminal zsh should be automatically selected. 

![vscode terminal!](Inkedvscode_terminal_LI.jpg  "ALT")


Next to it is a plus sign and a arrow down sign. To add the FiraMono as font press
```
arrow > Configure Terminal Settings and search for @feature:terminal font

Under Terminal> Integrated:Font Family add you font "FiraMono NF"
```
