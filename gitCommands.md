# Git commands

 Commands You Should Know
- Set Up Your Username and Email

```bash
  $ git config --global user.name "Your name"
  $ git config --global user.email "your@email.com"
```

- Cache Your Login Credentials ( It helps to avoid re-typing the username and password every time you perform a commit)

```bash
  $ git config --global credential.helper cache
```

- Створити новий Git-репозиторій

```bash
  $ git init
```

- Додати до контролю нових файлів та індексувати змінених файлів

```bash
  $ git add somefile.js
  $ git add .
```

- Перевірити статус файлів

```bash
  $ git status
```

- Зафіксувати всі зміни(увійдуть усі проіндексовані файли)

```bash
  $ git commit
  $ git commit -m "Your short summary about the commit"
```

- View Commit History With Changes

```bash
  $ git log
```

- View a Particular Commit

```bash
  $ git show 1af17e73721dbe0c40011b82ed4bb1a7dbe3ce29
  $ git show 1af17e
```

- View Changes Before Committing

```bash
  $ git diff
```
If you want to view the staged changes, you can add the --staged flag.
```bash
  $ git diff --staged
```
You can also provide a filename as a parameter to only view the changes of a specific file.
```bash
  $ git diff somefile.js
```
- Remove Tracked Files From The Current Working Tree (This action will also remove the files from the index.)
```bash
  $ git rm dirname/somefile.js
  $ git rm dirname/*.html
```

- Rename Files
```bash
  $ git mv dir1/somefile.js dir2
```
- Вилучити файл(-и) з індексу(що були додані до індексу командою add та не були закомічені)
```bash
  $ git reset HEAD somefile.js
  $ git reset HEAD
```
- Revert Unstaged and Staged Changes
```bash
  $ git checkout somefile.js
```
- Amend The Most Recent Commit (Alert !!! Don’t amend public commits.)

```bash
  $ git commit --amend -m "Updated message for the previous commit"
```
-  Rollback Last Commit

```bash
  $ git revert HEAD
```
- Rollback a Particular Commit
```bash
  $ git revert 1af17e
```
- Create and Switch To a New Branch
```bash
  $ git branch new_branch_name
  $ git checkout -b new_branch_name
```
- List All Branches (list all remote branches by using the -a flag)
```bash
  $ git branch
  $ git branch -a
```

- Видалення гілок
```bash
  $ git branch -d <name-of-branch-to-be-deleted>
  $ git branch --delete <name-of-branch-to-be-deleted>
```
- Видалення гілок з віддаленого сховища
```bash
  $ git push <remote-name-given-to-repository> --delete <name-of-branch>
```
- Merge Two Branches
```bash
  $ git merge existing_branch_name
```
- Show Commit Log as Graph For Current or All Branches.  The --graph option will draw an ASCII graph, which represents the branch structure of the commit history. When it used in association with the --oneline and --decorate flags, it makes it easier to identify which commit belongs to which branch.
```bash
  $ git log --graph --oneline --decorate
  $ git log --all --graph --oneline --decorate
```
- Abort a Conflicting Merge
```bash
  $ git merge --abort
  $ git reset
```
- Додати віддалене сховище
```bash
  $ git remote add <shortname> <url>
```
- Подивиться на віддалені сервера
```bash
  $ git remote
  origin
```
-v, покаже посилання, які Git зберігає та використовує при читанні та записі до цього сховища
```bash
  $ git remote -v
  origin	https://github.com/schacon/ticgit (fetch)
  origin	https://github.com/schacon/ticgit (push)
```
- Змінити посилання віддалених сховищ
```bash
  $ git remote set-url <an-existing-remote-name> <url>
```
- Get Additional Information About a Remote Repository
```bash
  $ git remote show origin
```
- Надсилати зміни до віддаленого сховища origin на гілку main
```bash
  $ git push origin main
```
- Надсилати зміни до віддаленого сховища origin на гілку main, яка ще не створена на віддаленому сховищу. Створити її та зв'язати з локальною гілкою main
```bash
  $ git push -u origin main
```
- Отримати всі нові дані з віддаленного середовища поточної гілки та зберігти їх у локальному репозиторії. Однак не зливати їх у поточну гілку
```bash
  $ git fetch
```
- Отримати всі нові дані з віддаленного середовища поточної гілки та злити їх у поточну гілку (git fetch + git merge)
```bash
  $ git pull
  $ git pull --verbose
```
- Merge Remote Repository With Local Repository
```bash
  $ git merge origin
```
- Push a New Branch To Remote Repository
```bash
  $ git push -u origin new_branch
```
- Use Rebase
```bash
  $ git rebase branch_name
```
[Source](https://levelup.gitconnected.com/top-30-git-commands-you-should-know-to-master-git-cli-f04e041779bc)
