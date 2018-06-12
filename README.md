
Номера страниц из задания с последовательностью команд

4.
```
mkdir practice-git
cd practice-git
git init
ls -la
.  ..  .git
```
5.
```
echo README.md >.gitignore
echo '*.sw[pon]' >>.gitignore
echo "My first line in project" > file.txt
git status
На ветке master

Начальный коммит

Неотслеживаемые файлы:
  (используйте «git add <файл>…», чтобы добавить в то, что будет включено в коммит)

	.gitignore
	file.txt

ничего не добавлено в коммит, но есть неотслеживаемые файлы (используйте «git add», чтобы отслеживать их)

git add .
git status
На ветке master

Начальный коммит

Изменения, которые будут включены в коммит:
  (используйте «git rm --cached <файл>…», чтобы убрать из индекса)

	новый файл:    .gitignore
	новый файл:    file.txt

git diff --cached 
diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..4c71257
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1,2 @@
+README.md
+*.sw[pon]
diff --git a/file.txt b/file.txt
new file mode 100644
index 0000000..ee2ae0c
--- /dev/null
+++ b/file.txt
@@ -0,0 +1 @@
+My first line in project
```
6.
```
git commit -m My\ first\ commit
[master 2e3cafa] My first commit
 Date: Wed Jun 13 00:35:51 2018 +0300
 2 files changed, 3 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 file.txt

git log
commit 2e3cafa1e8ab02a4aeee77694675acda8878086d
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:35:51 2018 +0300

    My first commit

git show 2e3cafa1e8ab02a4aeee77694675acda8878086d
commit 2e3cafa1e8ab02a4aeee77694675acda8878086d
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:35:51 2018 +0300

    My first commit

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..4c71257
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1,2 @@
+README.md
+*.sw[pon]
diff --git a/file.txt b/file.txt
new file mode 100644
index 0000000..ee2ae0c
--- /dev/null
+++ b/file.txt
@@ -0,0 +1 @@
+My first line in project
```
7.
```
echo London is a capital of UK >>file.txt

git diff
diff --git a/file.txt b/file.txt
index ee2ae0c..89e1f4b 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1,2 @@
 My first line in project
+London is a capital of UK

git diff --cached

git commit -am "Capital added"
[master f71d57c] Capital added
 1 file changed, 1 insertion(+)

git log
commit f71d57c2ef75f5973fabec6c89144b9c42bba215
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:39:02 2018 +0300

    Capital added

commit 2e3cafa1e8ab02a4aeee77694675acda8878086d
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:35:51 2018 +0300

    My first commit
```
8.
```
echo Moscow is the capital of Russia >>file.txt
git commit -am "Capitals added" --amend
[master 52e7037] Capitals added
 Date: Wed Jun 13 00:39:02 2018 +0300
 1 file changed, 2 insertions(+)
```
10.
```
git log
commit 52e7037cef30af16fc5d49958a295d07de4d2b00
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:39:02 2018 +0300

    Capitals added

commit 2e3cafa1e8ab02a4aeee77694675acda8878086d
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:35:51 2018 +0300

    My first commit
```
11.
```
git show
commit 52e7037cef30af16fc5d49958a295d07de4d2b00
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:39:02 2018 +0300

    Capitals added

diff --git a/file.txt b/file.txt
index ee2ae0c..586cb7c 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1,3 @@
 My first line in project
+London is a capital of UK
+Moscow is the capital of Russia
```
12.
```
echo Paris is the capital of France >>file.txt && git commit -am "Another capital was added"
[master b56a3e0] Another capital was added
 1 file changed, 1 insertion(+)
 git log
commit b56a3e092e0b278ff56d352dc0d846f22b826063
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:51:20 2018 +0300

    Another capital was added

commit 52e7037cef30af16fc5d49958a295d07de4d2b00
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:39:02 2018 +0300

    Capitals added

commit 2e3cafa1e8ab02a4aeee77694675acda8878086d
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:35:51 2018 +0300

    My first commit
git show
commit b56a3e092e0b278ff56d352dc0d846f22b826063
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:51:20 2018 +0300

    Another capital was added

diff --git a/file.txt b/file.txt
index 586cb7c..3fb5e2e 100644
--- a/file.txt
+++ b/file.txt
@@ -1,3 +1,4 @@
 My first line in project
 London is a capital of UK
 Moscow is the capital of Russia
+Paris is the capital of France
```
13.
```
git revert 52e7037cef30af16fc5d49958a295d07de4d2b00
error: не удалось возвратить коммит 52e7037… Capitals added
подсказка: после разрешения конфликтов, пометьте исправленные пути
подсказка: с помощью «git add <пути>» или «git rm <пути>»
подсказка: и сделайте коммит с помощью «git commit»
```
14.
```
git status
На ветке master
Вы сейчас возвращаете коммит 52e7037.
  (разрешите конфликты, затем запустите «git revert --continue»)
  (используйте «git revert --abort», чтобы отменить операцию возврата)

Не слитые пути:
  (используйте «git reset HEAD <файл>…», чтобы убрать из индекса)
  (используйте «git add <файл>…», чтобы пометить разрешение конфликта)

	оба измены:     file.txt

нет изменений добавленных для коммита
(используйте «git add» и/или «git commit -a»)
cat file.txt 
My first line in project
<<<<<<< HEAD
London is a capital of UK
Moscow is the capital of Russia
Paris is the capital of France
=======
>>>>>>> parent of 52e7037... Capitals added
```
15.
```
git show HEAD~1
commit 52e7037cef30af16fc5d49958a295d07de4d2b00
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:39:02 2018 +0300

    Capitals added

diff --git a/file.txt b/file.txt
index ee2ae0c..586cb7c 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1,3 @@
 My first line in project
+London is a capital of UK
+Moscow is the capital of Russia
```
16.
```
grep -v '^\(London\|Moscow\|=====\|<<<<<\|>>>>>\)' file.txt >/tmp/file.txt && mv -f /tmp/file.txt ./
cat file.txt 
My first line in project
Paris is the capital of France
```
17.
```
git add file.txt 
git revert --continue 
[master 9a8b74b] Revert "Capitals added"
 1 file changed, 2 deletions(-)
git log
commit 9a8b74bc82c9b23092942cf96515bfe0a7dbbda5
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 01:02:59 2018 +0300

    Revert "Capitals added"
    
    This reverts commit 52e7037cef30af16fc5d49958a295d07de4d2b00.
    
     Remove lines with the first added capitals (in the second commit)

commit b56a3e092e0b278ff56d352dc0d846f22b826063
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:51:20 2018 +0300

    Another capital was added

commit 52e7037cef30af16fc5d49958a295d07de4d2b00
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:39:02 2018 +0300

    Capitals added

commit 2e3cafa1e8ab02a4aeee77694675acda8878086d
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 00:35:51 2018 +0300

    My first commit
git show
commit 9a8b74bc82c9b23092942cf96515bfe0a7dbbda5
Author: Sergey Makeev <mac.798@mail.ru>
Date:   Wed Jun 13 01:02:59 2018 +0300

    Revert "Capitals added"
    
    This reverts commit 52e7037cef30af16fc5d49958a295d07de4d2b00.
    
     Remove lines with the first added capitals (in the second commit)

diff --git a/file.txt b/file.txt
index 3fb5e2e..2994147 100644
--- a/file.txt
+++ b/file.txt
@@ -1,4 +1,2 @@
 My first line in project
-London is a capital of UK
-Moscow is the capital of Russia
 Paris is the capital of France
```
18.
```
echo this is a garbage file | tee garbage1.tmp garbage2.tmp >/dev/null
git status
На ветке master
Неотслеживаемые файлы:
  (используйте «git add <файл>…», чтобы добавить в то, что будет включено в коммит)

	garbage1.tmp
	garbage2.tmp

ничего не добавлено в коммит, но есть неотслеживаемые файлы (используйте «git add», чтобы отслеживать их)
echo \*.tmp >>.gitignore
git status
На ветке master
Изменения, которые не в индексе для коммита:
  (используйте «git add <файл>…», чтобы добавить файл в индекс)
  (используйте «git checkout -- <файл>…», чтобы отменить изменения
   в рабочем каталоге)

	изменено:      .gitignore

нет изменений добавленных для коммита
(используйте «git add» и/или «git commit -a»)
git add .gitignore && git commit -m "Ignore .tmp files in git index"
[master 63a4732] Ignore .tmp files in git index
 1 file changed, 1 insertion(+)
xiaomi-nb% git status
На ветке master
нечего коммитить, нет изменений в рабочем каталоге
```
19.
```
echo First line for task on page 19 >> file.txt
git add file.txt
echo Second line for task on page 19 >> file.txt
git status
На ветке master
Изменения, которые будут включены в коммит:
  (используйте «git reset HEAD <файл>…», чтобы убрать из индекса)

	изменено:      file.txt

Изменения, которые не в индексе для коммита:
  (используйте «git add <файл>…», чтобы добавить файл в индекс)
  (используйте «git checkout -- <файл>…», чтобы отменить изменения
   в рабочем каталоге)

	изменено:      file.txt

git diff 
diff --git a/file.txt b/file.txt
index 7c8c3da..586d015 100644
--- a/file.txt
+++ b/file.txt
@@ -1,3 +1,4 @@
 My first line in project
 Paris is the capital of France
 First line for task on page 19
+Second line for task on page 19
git diff --cached 
diff --git a/file.txt b/file.txt
index 2994147..7c8c3da 100644
--- a/file.txt
+++ b/file.txt
@@ -1,2 +1,3 @@
 My first line in project
 Paris is the capital of France
+First line for task on page 19
```
20.
```
git commit -am "Commit for tark on page 19 (20)"
[master f6860b9] Commit for tark on page 19 (20)
 1 file changed, 2 insertions(+)
xiaomi-nb% git status 
На ветке master
нечего коммитить, нет изменений в рабочем каталоге
```
22.
```
git branch first
xiaomi-nb% git branch
  first
* master
git checkout first
Переключено на ветку «first»
```
23.
```
git checkout -b second
Переключено на новую ветку «second»
xiaomi-nb% git status
На ветке second
нечего коммитить, нет изменений в рабочем каталоге
xiaomi-nb% git branch
  first
  master
* second
```
24.
```
echo Let\'s change the branch >branch.txt
git add branch.txt && git commit -m "Branch was changed"
[second 31cb0bc] Branch was changed
 1 file changed, 1 insertion(+)
 create mode 100644 branch.txt
```
25.
```
git checkout first 
Переключено на ветку «first»
echo first branch specific content >first.txt
git add first.txt && git commit -m "Branch 'first' was changed"
[first 2bdcf79] Branch 'first' was changed
 1 file changed, 1 insertion(+)
 create mode 100644 first.txt
```
27.
```
git config --global alias.grlog 'log --all --decorate --oneline --graph'
git grlog
* 2bdcf79 (HEAD -> first) Branch 'first' was changed
| * 31cb0bc (second) Branch was changed
|/  
* f6860b9 (master) Commit for tark on page 19 (20)
* 63a4732 Ignore .tmp files in git index
* 9a8b74b Revert "Capitals added"
* b56a3e0 Another capital was added
* 52e7037 Capitals added
* 2e3cafa My first commit
```
28.
```
git checkout master 
Переключено на ветку «master»
ls
file.txt  garbage1.tmp	garbage2.tmp  README.md
git merge first 
Обновление f6860b9..2bdcf79
Fast-forward
 first.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 first.txt
ls
file.txt  first.txt  garbage1.tmp  garbage2.tmp  README.md
```
29.
Такой тип слияния называется fast-forward (быстрая перемотка).

30.
```
git checkout second
Переключено на ветку «second»
git rebase master
Сначала перематываем указатель текущего коммита, чтобы применить ваши изменения поверх него…
Применение: Branch was changed
```
31.
```
git grlog
* faa1e85 (HEAD -> second) Branch was changed
* 2bdcf79 (master, first) Branch 'first' was changed
* f6860b9 Commit for tark on page 19 (20)
* 63a4732 Ignore .tmp files in git index
* 9a8b74b Revert "Capitals added"
* b56a3e0 Another capital was added
* 52e7037 Capitals added
* 2e3cafa My first commit
```
32.
```
git branch -d first
Ветка first удалена (была 2bdcf79).
xiaomi-nb% git branch 
  master
* second
```





