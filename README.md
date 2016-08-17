Simple script to setup a git repo. It looks for `~/.config/git/work-settings`
or `~/.config/git/personal-settings` based on the value of `git remote`'s `origin`.

`git-validate-my-config` should be placed in your path before the real git-*
commands. Install it like so:

    install -m 755 git-validate-my-config ~/bin
    cd ~/bin
    ln -s git-validate-my-config git-review

I set up my `~/.gitconfig` like so:

    [init]
        templatedir = ~/.git-templates

And in there I have a `hooks/pre-commit` that is simply:

    #!/bin/sh
    git validate-my-config || setup-git

Now whenever I clone a repo the hook is in place and whenever I commit the hook ensures
the configuration is correct and current. `git init` run on a repo that was cloned previously
will safely re-apply the templates.
