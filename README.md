# rmbr

## Browser

- [Bubbling and capturing](https://javascript.info/bubbling-and-capturing)

## Git

- [Delete local Git branches after deleting them on the remote repo](https://stackoverflow.com/questions/17983068/delete-local-git-branches-after-deleting-them-on-the-remote-repo)
- [Syncing a fork](https://help.github.com/articles/syncing-a-fork/)

### Add Git repo from local to an online service

[This approach is also good, if you want to use an existing Git repo,
but you don't want to fork it, but yout want keep the Git history
(tested with GitHub)]

- Create Git repo at the online service
- Init a new Git project or clone an existing repo locally
- Set online service: `git remote (add|set-url*) origin <url-remote>`
- Add to online service: `git push -u origin master`

\*Use `set-url` for cloned Git repos

## Shell

- [Writing to a file from the shell](https://ubuntuforums.org/showthread.php?t=1623835&s=6d8ff5a066c767992033be9ed7913ba1&p=10127051#post10127051)

## Remove all pip packages

```bash
pip freeze | xargs pip uninstall -y
```

## Convert EOL in all files from CRLF to LF:

[dos2unix](http://dos2unix.sourceforge.net/) has to be installed for this!

- Basic usage:

```bash
find . -type f | xargs dos2unix
```

- Advanced usage (ingore some paths):

```bash
find . -type f ! -path "./venv/*" ! -path "./.git/*" ! -path "./node_modules/*" | xargs dos2unix
```
