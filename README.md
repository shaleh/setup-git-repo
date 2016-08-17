Simple script to setup a git repo. It looks for ~/.config/git/work-settings
or ~/.config/git/personal-settings based on where the repo was cloned.

git-validate-my-config should be placed in your path before the real git-*
commands. Install it like so:

install -m 755 git-validate-my-config ~/bin
cd ~/bin
ln -s git-validate-my-config git-review

I set up my ~/.gitconfig like so:

[init]
	templatedir = ~/.git-templates

And in there I have a hook/pre-commit that is simply:

git validate-my-config || setup-git

Now whenever I clone a repo the hook is in place and whenever I commit the hook ensures
the configuration is correct and current.
