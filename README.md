# Оглавление:
1. [Инструкция по работе в GitHub](#инструкция-по-работе-в-github)
2. [Предварительная настройка](#предварительная-настройка)
3. [Создание аккаунта в Github](#создание-аккаунта-в-github)
4. [Взаимодействие с GitHub](#взаимодействие-с-github)
    * [GitHub Issues](#github-issues)
    * [Запросы на вытягивание](#запросы-на-вытягивание)
    * [GitHub Discussions](#github-discussions)
    * [Обсуждения в команде](#обсуждения-в-команде)
5. [Создание репозитория](#создание-репозитория)
1. [Проект в Гитхабе](#проект-в-гитхабе)
1. [Изменение файлов и коммиты](#изменение-файлов-и-коммиты)
1. [Внесение и фиксация изменений](#внесение-и-фиксация-изменений)
    * [Создание запросов слияния (Pull Request) в Github](#создание-запросов-слияния-pull-request-в-github)
    * [Пулл реквест](#пулл-реквест)
1. [Что такое origin](#что-такое-origin)
1. [GitHub это еще и соцсеть!](#github-это-еще-и-соцсеть)
1. [Что такое токен](#что-такое-токен)
1. [Отчеты об ошибках](#отчеты-об-ошибках)
1. [Заключение](#заключение)



# Инструкция по работе в GitHub
---

Веб-сервис GitHub востребован для хостинга IT-проектов и совместной разработки. Разработчики системы называют ее «социальной сетью» для программистов. Здесь они объединяют репозитории, комментируют примеры «чужого» кода и используют платформу в качестве облачного хранилища с возможностью быстрой передачи заказчику.

### Предварительная настройка <div id='start' />
Для начала [зарегистрируйтесь на GitHub:](https://github.com/) задайте логин, почту и придумайте пароль. После «Создать аккаунт» не забудьте проверить почту и подтвердить её (опрос от Github после подтверждения почты можно пропустить).

![Начало](https://i.postimg.cc/z35QVtJ7/1.png)

Для того чтобы сервис определил, кто вы и имеете ли право работать с тем или иным репозиторием, нужно представиться — пройти процесс аутентификации.

При подключении используется пара ключей — открытый (публичный, public) и закрытый (приватный, private). Пользователь создаёт пару ключей при помощи специальной команды и сохраняет закрытый ключ у себя, а открытый кладёт на сервер (в нашем случае на GitHub). А работает это всё благодаря асимметричному шифрованию.

Чтобы создать пару ключей, в терминале нужно ввести команду, задать путь для хранения ключей и указать пароль к ключу (необязательно).

Далее будем опираться на то, что путь для ключей дефолтный и пароль на ключи не установлен.

Пароль для ключей нужен как дополнительная мера безопасности, если вдруг ваш приватный ключ попадёт не в те руки.

~~~
$ ssh-keygen
Generating public/private rsa key pair.
# путь до ключей, в скобках путь по умолчанию
Enter file in which to save the key (/Users/ifireice/.ssh/id_rsa):  
# пароль для ключей, при задании пароля в консоли не отображается ничего, даже звёздочки
# если нажать Enter, ничего не вводя, пароль будет пустым
Enter passphrase (empty for no passphrase):
# повторите пароль
Enter same passphrase again:
# после появится сообщение такого вида
Your identification has been saved in /Users/ifireice/.ssh/id_rsa
Your public key has been saved in /Users/ifireice/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:Zu+HkZPC4ZP0veRmVjuKgylVvljHBNO8mHs+ieFFPvs ifireice@ifireice-osx
The key's randomart image is:
+---[RSA 3072]----+
|           o     |
|          o o    |
|           = .   |
|        o + +    |
|       +S* X     |
|       oB.@ X .  |
|       . O.# * . |
|      . +.*.% o  |
|       .  o*.+E. |
+----[SHA256]-----+
~~~

Бинго, ключи сгенерированы: в заданной директории появятся два файла, id_rsa и id_rsa.pub.

Теперь надо добавить публичный ключ в аккаунт на GitHub:

~~~
# выведите содержимое публичного ключа в консоль
$ cat ~/.ssh/id_rsa.pub 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDDJfHIi73sKd6cqm3RwKuY1zl46aAaE6X9Gp
/6zJiY3BiJj95oJjPdpfpPhVFWLIbmT8zFAtOLbX9N4C3b0enHUzgMacP/Kl4AbrAkhLqaua9iD
VNxxiTVxADG1M5525oc/eAvx7y0pXIb9ouWdYJSKa8/TUYFhWlCzV2quY9SA0FaMs7eY41+KWYpG.....
tA0oGxv+7WmXQmQzleLIRG13KQ+VAbL2vabdPcRoGuZavh0smOr/GtVSnLdspZ5RgONMSPWlF2I1YHMR
Q7CIKPs= ifireice@ifireice-osx
$
~~~

Скопируйте ключ от символов ssh-rsa и до конца файла и вставьте его в ваш аккаунт на GitHub.

![ssh](https://i.postimg.cc/18gCLbHm/2.png)

![ssh](https://i.postimg.cc/XpYDgrBy/3.png)

![ssh](https://i.postimg.cc/jL333Ry3/4.png)


## Создание аккаунта в Github

Первый шаг к использованию сервиса GitHub заключается в регистрации нового пользователя. В процедуре нет ничего сложного – достаточно зайти на официальный сайт <https://github.com> и создать новую учетную запись. Система запросит рабочую электронную почту.

Пароль вводится на выбор пользователя, но с учетом правил. Так, рекомендуется комбинация размером в 15 символов или 8, но с использованием хотя бы одной цифры и строчной буквы. Имя пользователя, как и email, проверяется на занятость, и придется выбирать тот, с которым платформа позволит продолжать регистрацию.

Далее нужно указать, хочется ли получать новости об обновлениях продуктов и самой системы. Последним шагом становится подтверждение – пользователю предлагается собрать паззл, после чего станет активной кнопка ***«Зарегистрироваться»*** .

Вход на платформу будет открыт только после подтверждения электронной почты, поэтому зайти анонимно не получится. Это своеобразная защита сервера от многочисленных ботов и гарантия для пользователей, что они будут общаться с реальными людьми. Теперь можно приступать к управлению настройками внутри личного кабинета.

## **Взаимодействие с GitHub**
---

GitHub предоставляет встроенные средства общения для совместной работы, чтобы вы могли взаимодействовать с сообществом. В этом кратком руководстве показано, как выбрать подходящее средство для ваших потребностей.

Вы можете создавать проблемы, запросы на вытягивание, GitHub Discussions и обсуждения в команде, а также участвовать в них, в зависимости от требуемого типа обсуждения.

### GitHub Issues
* удобны для обсуждения конкретных сведений о проекте, например для отчетов об ошибках, сведений о запланированных улучшениях и отзывов;
* относятся к конкретному репозиторию и обычно имеют конкретного владельца;
* часто называются системой отслеживания ошибок GitHub.
### Запросы на вытягивание
* позволяют предлагать конкретные изменения;
* позволяют напрямую комментировать предложенные другими пользователями изменения;
* относятся к конкретному репозиторию.
### GitHub Discussions
* выполняют роль форума, который лучше всего подходит для обсуждения в свободной форме идей и планов, требующих общего участия;
* могут охватывать множество репозиториев;
* предоставляют возможность совместной работы без привязки к базе кода, например для мозгового штурма идей и наработки базы знаний сообщества;
* часто не имеют конкретного владельца;
* часто используются не для создания конкретной задачи.
### Обсуждения в команде
* могут создаваться на странице обсуждения в команде, и могут охватывать несколько проектов без привязки к определенной проблеме или запросу на вытягивание. Вместо того, чтобы открыть вопрос в репозитории для обсуждения идеи, вы можете привлечь к беседе всю команду, проведя обсуждение в команде.
* позволяют проводить с командой обсуждения для планирования, анализа, проектирования, изучения реакции пользователей и принятия решений общего характера по проекту;

## Создание репозитория

Важно отметить, что сервис англоязычный, и пользоваться им без знания языка получится только при использовании обновленных версий браузеров типа Google Chrome, где есть встроенные функции по переводу страниц. В любом случае работа начинается с создания собственного репозитория – в бесплатном режиме доступны публичные, частные откроются только при активации платного тарифа.

## Последовательность действий:

1. В правом верхнем углу любой страницы откройте раскрывающееся меню  и выберите Новый репозиторий.
В поле Имя репозитория введите hello-world.

2. В поле Описание напишите краткое описание.

3. Выберите параметр Добавить файл сведений.

4. Выберите, будет ли репозиторий общедоступным или частным.

5. Выбрать нужный тип лицензии и нажать на кнопку *«Create project».*
Тип лицензии (приватная или публичная) допускается заменить после, в процессе использования платформы. Единственная настройка, которую пользователи делают сразу, – это создание нескольких веток для размещения разных проектов. Например, для тестового кода и финальных релизов, чтобы не путать их при разработке и общении с другими кодерами.

6. Щелкните Создать репозиторий.
## Проект в Гитхабе

Подобный подход часто используют создатели продуктов, которыми пользуются «массы». Им передается ссылка на проверенные стабильные версии, в то время как команда продолжает работу над таким же комплектом файлов без опасения нарушить функциональность системы в целом. При использовании платформы следует ориентироваться на отметку *«Branch».*

Данная отметка обозначает текущую ветку. Создание новой инициируется просто – достаточно в списке начать набирать еще несуществующее название, и система выдаст сообщение «Create branch». Сразу после этого пользователь перекидывается в новую ветку (это стоит учитывать при работе, чтобы случайно не начать редактирование «не тех файлов»).

## Изменение файлов и коммиты
Корректировка файлов на GitHub выполняется при помощи коммитов. Это непосредственно само исправление и краткое описание изменений. Такой подход позволяет «внешним» пользователям ориентироваться в нововведениях кода и упрощает контроль командной работы, когда один и тот же файл может редактироваться разными исполнителями.

Система сохранения информации о корректировках удобна, когда они вносятся в различные участки кода, но связаны с определенной задачей. Фактически текстовый файл с описанием «связывает» разрозненные изменения и объясняет непосвященному программисту их суть, назначение. Чтобы запустить редактирование README, нужно в правой панели нажать на «кисточку».

После этого откроется текстовый редактор, где вносятся исправления. По завершении заполняется поле *«Commit»* внизу страницы (кратко, что изменилось) и нажимается кнопка *«Commit changes»*. Сохраненные корректировки будут внесены в текущую (активную) ветку проекта, поэтому перед их внесением следует убедиться в правильном выборе.

# Внесение и фиксация изменений
После создания ветви на предыдущем шаге в GitHub открылась страница кода для новой ветви readme-edits, которая является копией ветви main.

Вы можете вносить изменения в файлы в репозитории и сохранять их. В GitHub сохраненные изменения называются фиксациями. С каждой фиксацией связано сообщение о фиксации, в котором объясняется, почему было внесено данное изменение. В сообщениях о фиксациях ведется история изменений, чтобы другие участники могли понять, что вы сделали и почему.

* В созданной ветви readme-edits щелкните файл README.md.

* Щелкните , чтобы изменить файл.

* В редакторе напишите немного о себе. Попробуйте использовать различные элементы Markdown.

* В поле Фиксация изменений напишите сообщение о фиксации с описанием изменений.

* Щелкните Зафиксировать изменения.

## Создание запросов слияния (Pull Request) в Github

При подключении к работе сторонних специалистов может понадобиться функция запроса слияния *(Pull Request).* Инструмент для работы в таком формате называется DIFF. Он подчеркивает любые «чужие» изменения, чтобы владелец программы сразу видел, где код писал не он. Пометки будут доступны только после создания коммита.
## Пулл реквест

Последовательность действий:

Открыть вкладку «Pull Request».
Нажать на кнопку «Create Pull Request».
Выбрать ветку, которую следует слить с основной.
Просмотреть внесенные кодером изменения.
После изучения информации созданный запрос на слияние подтверждается нажатием «Merge Pull Request». Новый код будет импортирован в основную ветку, а созданная сторонним исполнителем может спокойно удаляться.


---
### Что такое origin 
Нашел [статью](https://www.atlassian.com/ru/git/tutorials/syncing#:~:text=%D0%92%20%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81%D0%B5%20%D0%BA%D0%BB%D0%BE%D0%BD%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E,%D0%B8%D0%B7%D0%BC%D0%B5%D0%BD%D0%B5%D0%BD%D0%B8%D1%8F%20%D0%B8%D0%BB%D0%B8%20%D0%BF%D1%83%D0%B1%D0%BB%D0%B8%D0%BA%D0%BE%D0%B2%D0%B0%D1%82%D1%8C%20%D0%BB%D0%BE%D0%BA%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B5%20%D0%BA%D0%BE%D0%BC%D0%BC%D0%B8%D1%82%D1%8B.), в которой говорится следующее: 
> В процессе клонирования с помощью команды ```git clone``` автоматически создается удаленное подключение к исходному репозиторию (такое соединение называется origin). Это позволяет разработчикам, создающим локальную копию центрального репозитория, легко загружать вышестоящие изменения или публиковать локальные коммиты. Именно поэтому большинство проектов на основе Git называют свой центральный репозиторий origin.

Вызвав команду в терминале: ```git remove -v```, мы увидим наменование удаленного репозитория и его адрес.

---
### GitHub это еще и соцсеть!

Используя кнопку ```follow``` под фотографией пользователя, можно подписаться на пользователя на GitHub. Также будете получать уведомления о его общедоступной активности. Если тот, на кого вы подписаны, создает новый репозиторий, помечает репозиторий или подписывается на другого пользователя, это действие будет отображаться на панели мониторинга.  
Таким же способом, можно подписаться на организацию на GitHub.

Еще на GitHub Вы можете общаться с разработчиками по всему миру. 

---
### Что такое токен

Это альтернатива использованию паролей для аутентификации на GitHub. Создать его очень просто, вверху справа нажать на фото своего профиля, и зайти в меню ```settings```, далее меню ```<> Developer settings```, после заходим в меню ```Personal access tokens``` и открываем ```Tokens (classic)```. В открывшемся меню следует нажать кнопку ```Generate new token```. 

[Полная инструкция](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) по созданию токена. 

---

## Отчеты об ошибках
Платформа GitHub используется не только для совместной разработки, а еще и для получения обратной связи с пользователями продуктов. Так, на вкладке «Issue» любой «тестировщик» может оставить сообщение о проблемах, с которыми ему пришлось столкнуться при использовании ПО. Чтобы сделать это, нужно нажать кнопку «New issue».

После этого вносится заголовок и текст сообщения. «Проблема» отправляется нажатием на кнопку «Create new issue». Владелец ветки получает уведомления в личном кабинете или на электронную почту, указанную при регистрации.

## Заключение

Финалом разработки обычно становится выпуск определенного релиза программного продукта. Это отражается на вкладке «Releases». Здесь следует нажать на кнопку «Create New Release», указать номер версии в поле «Tag Version», внести ее название и небольшое описание. Здесь же прикрепляются архивы с компилированными файлами.

Остается нажать на «Create Release» и убедиться в публикации релиза. Ссылки на исходный код в tar.gz и zip создаются автоматически. Остальные файлы понадобится добавлять вручную.