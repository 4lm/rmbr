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

### Add an existing Git repo to GitHub

```sh
cd <path-to>/<git-repo>
git remote remove origin
gh repo create <user-or-org-name>/<repo-name> -y --private
git remote set-url origin git@github.com:<user-or-org-name>/<repo-name>.git
git push
```

## Shell

- [Writing to a file from the shell](https://ubuntuforums.org/showthread.php?t=1623835&s=6d8ff5a066c767992033be9ed7913ba1&p=10127051#post10127051)

## Remove all pip packages

```bash
pip freeze | xargs pip uninstall -y
```

## Find cmd use cases:

- Convert EOL in all files from CRLF to LF:

[dos2unix](http://dos2unix.sourceforge.net/) has to be installed for this!

```bash
find . -type f | xargs dos2unix
```

- Convert EOL in all files from CRLF to LF (ignore some paths):

```bash
find . -type f ! -path "./venv/*" ! -path "./.git/*" ! -path "./node_modules/*" | xargs dos2unix
```

- Change file chmod, ignore folder: 

```bash
find . -type f ! -path "./.git/*" -exec chmod 644 {} \;
```

# How to list all locally linked npm packages?

To view a list of all locally linked npm packages, you can use the following approaches:

## 1. Check Global `node_modules` Directory

Linked packages are stored in the global `node_modules` directory. You can list them by navigating to this directory and listing its contents.

### For npm:

#### 1.1 Find the Global `node_modules` Directory

Run:

```bash
npm root -g
```

This command will show you the path to the global `node_modules` directory.

#### 1.2. List the Contents:

Navigate to the directory provided by the previous command and list its contents. In most systems, you can do this with:

```bash
ls `npm root -g`
```

### For Windows Users:

If you're on Windows, use the equivalent command in Command Prompt or PowerShell to list the contents of the directory.

## 2. Use `npm ls -g --depth=0 --link=true`

You can also use an npm command to list globally linked packages.

Run:

```bash
npm ls -g --depth=0 --link=true
```

This command lists all globally installed packages and highlights which ones are linked. The `--depth=0` option limits the output to top-level packages, making it easier to see just the linked ones.

## Note:

- Locally linked packages are essentially global packages that are symlinked into your project. That's why you look at the global `node_modules` directory to find them.
- Remember that the appearance and location of the global `node_modules` directory can vary based on your operating system and npm configuration.
