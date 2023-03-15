

### Part I

1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).

[**ссылка на репозиторий**](https://github.com/LatyshevBogdan/Lab2)

2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.

`cd Labs/`
`git clone https://github.com/LatyshevBogdan/Lab2.git`
`cd Lab2`
`mkdir sources`

3. Создайте файл `HelloWorld.cpp` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу **Hello world** на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку `using namespace std;`.

nano sources/HelloWorld.cpp

4. Добавьте этот файл в локальную копию репозитория.

`git add .`

5. Закоммитьте изменения с *осмысленным* сообщением.

`git commit -m "add HellowWorld.cpp"`
`git push origin main`

6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение `Hello world from @name`, где `@name` имя пользователя.

`nano  sources/HellowWorld.cpp`

7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно `git add`?

`git add .`
`git commit -m "удаление добавления всего пространства имен std; добавление возможности ввода имени пользователя с последующим выводом сообщения"`

8. Запуште изменения в удалёный репозиторий.

`git push origin main`

9. Проверьте, что история коммитов доступна в удалёный репозитории.

### Part II

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. В локальной копии репозитория создайте локальную ветку `patch1`.

`git checkout -b patch1`

2. Внесите изменения в ветке `patch1` по исправлению кода и избавления от `using namespace std;`.

`nano  sources/HelloWorld.cpp`
`git add .`

3. **commit**, **push** локальную ветку в удалённый репозиторий.

`git commit -m "add name"`
`git push origin patch1`

4. Проверьте, что ветка `patch1` доступна в удалёный репозитории.
5. Создайте pull-request `patch1 -> main`.
6. В локальной копии в ветке `patch1` добавьте в исходный код комментарии.
7. **commit**, **push**.
8. Проверьте, что новые изменения есть в созданном на **шаге 5** pull-request
9. В удалённый репозитории выполните  слияние PR `patch1 -> main` и удалите ветку `patch1` в удаленном репозитории.
10. Локально выполните **pull**.

`git pull`

11. С помощью команды **git log** просмотрите историю в локальной версии ветки `master`.

`git log`

12. Удалите локальную ветку `patch1`.

`git switch main`
`git branch -d patch1`


### Part III

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. Создайте новую локальную ветку `patch2`.

`git checkout -b patch2`

2. Измените *code style* с помощью утилиты [**clang-format**](http://clang.llvm.org/docs/ClangFormat.html). Например, используя опцию `-style=Mozilla`.

`clang-format -i -style=Mozilla sources/hello_world.cpp`

3. **commit**, **push**, создайте pull-request `patch2 -> master`.

`git add .`
`git commit -m "изменение code style в файле hello_world.cpp"`
`git push origin patch2`

4. В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
5. Убедитесь, что в pull-request появились *конфликтны*.
6. Для этого локально выполните **pull** + **rebase** (точную последовательность команд, следует узнать самостоятельно). **Исправьте конфликты**.

`git pull`
`nano edit sources/hello_world.cpp`
`git add .`
`git commit -m "внесение исправлений в конфликтующий файл"`
`git rebase main`
`nano soursec/HelloWorld.cpp`
`git add .`
`git rebase --continue`
`git pull origin main`
`git push -f origin patch2`

7. Сделайте *force push* в ветку `patch2`

`git push -f origin patch2`

8. Убедитеcь, что в pull-request пропали конфликтны. 
9. Вмержите pull-request `patch2 -> master`.

`git switch main`
`git merge patch2`
