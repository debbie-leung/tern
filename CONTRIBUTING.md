# Contributing to the Tern project

Once again, we hope you have read our [code of conduct](/CODE_OF_CONDUCT.md) before starting.

We are excited to work with anyone at any level contributing their time and effort towards the project.

You can contribute in the following ways:

**Start a Discussion**

- Ask questions about the project goals, features, a specific use case, or clarification on documentation. Asking questions lead to issues being filed, eventually making the project more usable.

**File Issues**

- Run the code against any Docker image you are using, or any of the tests and submit bug reports when you find them.

**Contribute Documentation**

- Improve the documentation, project structure and workflow by creating a proposal.
- Contribute changes to documentation by [submitting pull requests](#submit-pr) to it.

**Contribute Code**

- [Resolve Issues](https://github.com/tern-tools/tern/issues)
- Improve the robustness of the project by:
  - [Adding to the Command Library](docs/adding-to-command-library.md)
  - [Adding a Custom Report Format](docs/creating-custom-templates.md)
  - [Adding an Extension](docs/creating-tool-extensions.md)

## Am I Qualified to Contribute?

The short answer is 'yes'!

The long answer is that there are some basic requirements that will help you contribute to any project on GitHub and this one in particular. Leveling up requires some extra knowledge:

**Beginner**

- English (not necessarily fluent but workable)
- The Python 3 Programming Language (Python is a very friendly community with plenty of tutorials you can search for)
- The Git version control system. Follow GitHub's setup guide [here](https://help.github.com/articles/set-up-git/). You can also practice submitting a pull request with no code [here](https://github.com/nishakm/puns).

**Intermediate**

- YAML (Tern uses yaml files heavily for data lookup. An overview of YAML can be found [here](http://yaml.org/))
- Object Oriented Programming in Python
- Python virtual environments
- Unix Command Line and shell scripts
- Linux System Administration
- [Docker Containers](https://docs.docker.com/)
- [Vagrant](https://www.vagrantup.com/docs/index.html)

**Advanced**

- [Container Images](https://docs.docker.com/v17.09/engine/userguide/storagedriver/imagesandcontainers/)
- [OverlayFS](https://wiki.archlinux.org/index.php/Overlay_filesystem)
- Advanced Python knowledge
- Linux Kernel knowledge would be nice

## Communicating through GitHub Issues

The fastest way you can get our attention is by filing an issue. We have some templates that help with organizing the information but if you don't think any of them are suitable, just file a regular GitHub issue. All issue templates are located in the .github/ISSUE_TEMPLATE folder in your local clone if you want to take a look at it before filing an issue.

You can:

- Ask a question
- Submit a proposal
- Submit a feature request
- File a bug report
- File a regular GitHub issue

Please do not submit a pull request without filing an issue. We will ask you to file one and refer to it in your commit message before we merge it.

**A note about maintainer's time**
Maintainers are people with lives of their own. The typical time to get a response to a question or a review on a PR is 3 business days but we take chunks of time off for other things as well so it could take longer.

**Project Maintainers**

- @nishakm
- @rnjudge

## Other Communication Channels

### Public forum

You can post a topic on the [public forum](https://groups.google.com/forum/#!forum/tern-discussion). You will need to apply to join the group before posting.

### Slack channel

If you would like to chat live, you can join the Slack channel. If you don't have an @vmware.com or @emc.com email, please [follow this link](https://code.vmware.com/join), enter your email address and click "Request Invite". If you are already a member of the slack channel, or if you have an @vmware.com or @emc.com email, you can simply [sign-in to the Slack channel](https://vmwarecode.slack.com/messages/tern).

## How Do I Start Contributing?

Look for issues without the label `assigned` on it. This indicates that someone is already working on it. Some labels that may be of interest are listed here:

- docs: Documentation changes
- good-first-issue: A good issue to start off with if this is your first time contributing to this project
- first-timers-only: A good issue to start off with if this is your first time contributing to any GitHub project
- tests: An issue regarding testing the project code
- tools: An issue regarding tools for developers or contributors
- bug: A bug in code functionality
- arch: An issue requiring some architectural change

To start, comment on the issue asking if you can work on it. A maintainer will tag your username to the issue and apply the `assigned` label on it.

## Setting up a Development Environment

For hassle-free code contribution, follow the steps below. NOTE: I mostly work in a Linux environment using a basic text editor (vim). Your set-up could be different. If it is, please feel free to submit an issue regarding your development environment and a pull request to add to this documentation.

### Visual Studio Code Development Container

Developing using Visual Studio Code development container lets you use a Docker container as a development environment. The Tern repository contains a definition for a pre-configured Docker container to simplify the setup process. To use it you need to download the following software on your host machine:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Docker](https://www.docker.com/get-started)
- [The Visual Studio Code Remote - Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

Once you have all that installed you can setup your dev enviornment:

1. Fork the main Tern repository using your GitHub account. Once forked, clone *your* fork (not the main Tern repo) on your local desktop.
2. Using the terminal, `cd` into the forked Tern directory on your local desktop and setup your git credentials:
```
    git config --global user.name "Your Name"
    git config --global user.email "your.email@address.com"
```
3. Open Visual Studio Code. Click the `><` icon in the lower lefthand corner. A search bar will come up at the top of the window. Type "Remote-Containers: Open Folder in Container" and click on it. In the window that pops up, navigate to the cloned `tern` folder on you desktop and click "Open". If you do not see the "Remote-Containers: Open Folder in Container" in your search bar, try clicking the `gear` icon in the lower lefthand corner and select "Command Palette", or use the `F1` key on your keyboard to go directly to it and search this way.
4. On the left-most side panel, click on the icon that looks like four squares with one detaching. This is the "Extensions" menu. A search bar will appear. Use this to install the Docker Extension. It might be suggested, but if not, you can type "Docker" to search for it.
5. If you are working on a Mac, there is a reported [bug](https://github.com/microsoft/vscode-remote-release/issues/3149) and [workaround](https://github.com/microsoft/vscode-remote-release/issues/3149#issuecomment-646588532) when using the Docker extension with a remote container. To change the Docker path once the Docker extension is installed, click on the `><` icon, type "Settings", click on "Remote-Containers: Settings" and update the `Remote > Containers: Docker Path` section to be `/usr/local/bin/docker`.
6. In the top menu bar, click on "Terminal" --> "New Terminal". You should see a terminal open at the bottom and if you type `ls` you should see the files in the Tern repository.
7. Run `pip3 install tern -e .[dev]` to install Tern and its dependencies.
8. Test that you can run Tern in your dev container by running: `tern report -i debian:buster`. You should see an SBOM printed to the console for the `debian:buster` container image.
9. To setup your branch for long-term contributions, follow the commands in step five under the "Setting up a Long Term Development Environment" section.
10. Create a new branch by running `git checkout -b <newbranch-name>`. You're now ready to start making changes to Tern, which you can do via the Terminal or using GUI editor provided by VS Code. Note that you will need to commit your changes with git using the Terminal command line.


### Setting up a Long Term Development Environment

You may have already cloned the project and started working on it. If you're reading this after the fact, I would highly recommend you save your work and set up a new development environment in this way.

1. Set up a Python virtual environment that has either the Python 3.6 or Python 3.7 executable. See [here](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments) for instructions on how to set this up using your host machine's Python3. There are also a guide to [managing virtual environments using pipenv](https://docs.python-guide.org/dev/virtualenvs/) but I haven't used it. Once done, you should have a folder created. Change to that folder.
2. Clone *your fork* of Tern in the virtual environment folder.
3. Activate your virtual environment `source bin/activate`. NOTE: This specific activate script only works for Bash and Mac ZSH shells. If you need to activate a Fish Shell or C Shell you should use `source/bin/activate.fish` or `source/bin/activate.csh`, respectively.
4. Change directory into the Tern clone.
5. Next, set up your project for long-term open source contribution, run these commands:

    **Note**: the following command will only work if you have a functioning ssh-key setup with GitHub
    ```
    $ git remote add upstream git@github.com:tern-tools/tern.git
    ```

    If you are not working with ssh keys, use the HTTPS link instead of running the above command:
    ```
    $ git remote add upstream https://github.com/tern-tools/tern.git
    ```

    In either case, continue with the following commands:
    ```
    $ git fetch upstream
    $ git checkout -b up upstream/main
    $ git push origin up:refs/heads/main
    ```

    Your `up` branch can now be used to keep track of changes on Tern's `main` branch and your other dev branches can stay separate.

6. Create a development branch. Assuming you are still on the `up` branch we just created (to verify, run `git branch` and make sure the `*` is next to `up`), run: `git checkout -b <new-dev-branch-name>`. If you are not currently on the `up` branch, first run `git checkout up` before creating your new dev branch.
7. Run `pip install wheel`. This is needed because some dependencies for development fail to build python wheels.
8. Run `pip install -e.[dev]`. This will install tern in development mode. This will install the project dependencies and [Prospector](https://github.com/PyCQA/prospector) which is a tool to check for style and linting errors. Every time you make functional changes to Tern, re-run this command to pick up the changes for local testing.
9. For more git tutorials, follow [these examples](https://github.com/nishakm/puns) or ask one of the maintainers for help :) 

### Setting up a development environment on Mac and Windows

1. [Install](https://github.com/tern-tools/tern#install) VirtualBox and Vagrant for Mac or Windows
2. Run `git clone https://github.com/tern-tools/tern.git`
3. Run `cd tern/vagrant`
4. Run `vagrant up`
5. Run `vagrant ssh`
6. Run `python3 -m venv ternenv`
7. Run `cd ternenv`
8. Run `source bin/activate`
9. Run `cp -r /tern .`
10. Run `cd tern`
11. Run `pip3 install wheel`
12. Run `pip3 install -e.[dev]`
This will install tern at the tip of master on Windows and Mac.

### After making changes

1. Install your changes in the development virtual environment `pip3 install -e.[dev]`
2. Run prospector from the project's root directory `prospector .`
3. Fix any issues prospector brings up.
4. Run bandit from the project's root directory `bandit -r .`
5. Fix any issues bandit brings up.
6. Test your changes.

### Testing you changes

After you make the changes just run `tox`. This will run a set tests and inform you if anything is wrong.

### Setting up a development environment for use with extensions

To learn more about how Tern can be used with external tools as extensions, see [these instructions](https://github.com/tern-tools/tern#extensions).

Tern will be able to find the absolute path of the command line tool which will be used as an extension if it is available on the system. For instance, to make Tern work with Scancode, you can install Scancode in your development environment such that it is available when you run `which scancode`.

Note that you do not need to do this if you are using a Python library as an extension.

#### Development with Tern and Scancode

If you are developing on Tern and Scancode together, you will need to install both packages in your python virtual environment before running Tern. Eg:

```sh
$ python3 -m venv devenv
$ cd devenv
$ git clone git@github.com:tern-tools/tern.git
$ git clone git@github.com:nexB/scancode-toolkit.git
$ cd tern
$ pip install -e.[dev] .
$ cd ../scancode-toolkit
$ pip install .
$ cd ..
$ tern report -x scancode -i debian:buster
```

## Coding Style

Tern follows general [PEP8](https://www.python.org/dev/peps/pep-0008/) style guidelines. Apart from that, these specific rules apply:

- Indents for .py files are 4 spaces long
- Indents for .yml files are 2 spaces long
- Modules are listed as external dependencies, followed by a space, followed by internal dependencies, listed individually and in alphabetical order. For example:

```python
# external dependencies not part of Tern
# possibly part of the python package or installed via pip
import os
import sys

# internal dependencies that are part of Tern
import common
from utils import rootfs
```

- Minimize [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity). Most python style checkers also come with McCabe complexity checkers. A good rule of thumb is to limit the number of if-then-else statements to 3 and return once in a module.

## Commit message format

The commit message of your PR should be able to communicate what problem/opportunity the PR addresses without any reference to forum messages or discussions on slack or IRL. You may make a reference to a github issue number using the github format (eg: Resolves: #1). Here is an overview of what is needed in a good commit message taken from [this blog](https://chris.beams.io/posts/git-commit/)

- Separate subject from body with a blank line
- Limit the subject line to 50 characters
- Capitalize the subject line
- Do not end the subject line with a period
- Use the imperative mood in the subject line
- Wrap the body at 72 characters
- Use the body to explain what and why vs. how

The commit message should be done with git and for that run the following command in your terminal:

```sh
$ git commit
```

Once this command is executed, you will be able to add the commit message (follow the guidelines given below for this). 
When you are done, save the message and push the changes.

In addition to this, we would like you to sign off on your commit. You can configure git to automatically do this for you when you run 'git commit -s'.

```sh
$ git config --global user.name "Some Dev"
$ git config --global user.email somedev@example.com
```

You should see a footer in your commit message like this:

```sh
Signed-off-by: Some Dev <somedev@example.com>
```

Please use a name you would like to be identified with and an email address that you monitor.

Example:

```diff
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789

Signed-off-by: Some Dev <somedev@example.com>
```

To make any changes to your existing git commit message, make sure you are on your development branch and run the following command in your terminal:

```sh
$ git commit --amend
```

Once you are done editing your commit message, save it like you did previously.


## Learn about Tern

- [FAQ](/docs/faq.md)
- [Glossary](/docs/glossary.md)
- [Architecture](/docs/architecture.md)
- [Navigating the Code](/docs/navigating-the-code.md)

## Troubleshooting

- Unable to find module 'yaml': make sure to activate the python virtualenv first and then run `pip install .`
- Cannot find bdist_wheel: This usually happens when there is a mismatch between the python version and the virtualenv version. Make sure the symlinks you are using point to the right versions in `/usr/bin/python`.
