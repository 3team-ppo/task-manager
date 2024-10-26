# Labs ППО

## Lab 1

- **Краткое описание Task Manager**

  Мы создаем систему управления задачами. В нашей системе только два типа пользователей - авторизованный (который прошел регистрацию и аутентифицировался) и гость. Единственное, что может гость - зарегистрироваться и стать авторизованным пользователем.

  Пользователи (авторизованные) могут создать проект, обозначив его название. При этом пользователь-создатель проекта становится участником этого проекта и может добавлять новых пользователей-участников проекта. Любые участники могут добавлять новых участников.

  Участники проекта могут создавать задачи внутри этого проекта, обозначая имя для задачи. В дальнейшем имя задачи может быть изменено на иное любым другим участником проекта.

  Кроме этого, любой из участников проекта может назначать других участников проекта исполнителями задачи. У задачи может быть 0 или более исполнителей.

  Задачу можно отметить как выполненную. Это тоже может сделать любой участник проекта. Если что-то пошло не так и задачу отметили как выполненную по ошибке, то можно вернуть задачу в работу.

- **Вопросы**
    1. Какие данные пользователя используются для регистрации
        1. Никнейм, пароль
    2. Если пользователь с таким никнеймом уже существует, как должна вести себя система?
        1. Отклонить запрос о регистрации, выдать информативное сообщение (формулировку сообщения можете выбрать по своему усмотрению)
    3. Тогда, вероятно, стоит добавить функцию проверки, существует ли пользователь с таким никнеймом?
        1. Да, стоит
    4. Как происходит процесс входа в систему (аутентификации)
        1. На данный момент мы не хотим реализовывать никакие механизмы аутентификации и авторизации. Необходимо будет реализовать только добавление пользователей в систему.
    5. Чтобы добавить в проект нового участника нужна возможность искать пользователя. Вероятно, проще всего искать будет по его имени и никнейму?
        1. Да, стоит добавить в пользователя атрибут “имя” и указывать его при регистрации. В это поле мы помещаем ФИО пользователя.
        2. Да, стоит реализовать функцию поиска участника. Давайте искать по полному совпадению или вхождению искомой строки в никнейм или имя пользователя
    6. Могут ли пользователи видеть проекты, участниками которых они не являются
        1. Да, для реализации минимального продукта мы не делаем никаких механизмов разграничения доступа (авторизации).
    7. Что предполагается показывать пользователю (какую страницу) после успешной аутентификации?
        1. Хотим показывать ему страницу со списком проектов, участником которых он является и кнопку "создать проект".
    8. Как сам проект должен отображаться в списке?
    9. Как в системе должна отображаться задача? Каким образом пользователь может может ее просмотреть? Могут ли видеть задачу пользователи, которые не являются участниками проекта, к которому относится задача? Могут ли видеть задачу пользователи, которые не являются ее создателем или исполнителем?
    10. Можно ли изменять название проекта?
    11. Чтобы назначить пользователя исполнителем задачи необходимо реализовать поиск так же как это было решено реализовать для добавления в проект нового участника(см. 5 вопрос)? То есть реализовать функцию поиска участника полному совпадению или вхождению искомой строки в никнейм или имя пользователя?
    12. Из ответов на предыдущие вопросы мы можем сделать вывод, что пользователя можно уникально идентифицировать по его никнейму? Или уникальным идентификатором пользователя в системе должно являться отдельное поле по типу ID?
    13. Как должно происходить изменение статуса задач? Пользователь может ввести статус вручную или выбрать из списка?
    14. Можно ли создавать проекты и задачи с одинаковыми названиями? Могут ли в рамках одного проекта существовать задачи с одинаковыми названиями? Если да, то каким образом задачи и проекты должны уникально идентифицироваться в системе?
    15. Можно ли удалять исполнителя/исполнителей задачи?
    16. Можно ли назначить себя на задачу?
    17. Можно ли удалять участников проекта? Можно ли в таком случае удалить всех участников в том числе и пользователя-создателя? Что в таком случае должно происходить с проектом?

- **Функциональные требования**

  *Пользователь должен иметь возможность…*

    1. “Гость” может направить запрос в систему, существует ли уже пользователь с переданным никнеймом и получить ответ в формате “true”/”false”
    2. Пройти регистрацию в системе, сменив статус “гостя” на “пользователя” системы, передав никнейм, имя и пароль.
        1. Операция отклоняется с информативным сообщением, если пользователь с таким ником уже существует.
    3. Создать проект, передав название проекта и никнейм пользователя-создателя проекта.
    4. Создать задачу в проекте, передав название проекта и название задачи. Задача создается в статусе “не выполнено”.
    5. Изменять список пользователя(-ей) исполнителей задачи: добавить или удалить исполнителя, передав название задачи и никнем(-ы) пользователя(-ей), если задача в статусе “не выполнено”.
    6. Найти пользователя в поиске при добавлении нового участника в проект. Поиск должен происходить по полному совпадению или вхождению искомой строки в никнейм или имя пользователя.
    7. Изменить статус задачи, передав ее название и новый статус.
    8. Изменить название уже существующей задачи, передав текущее название задачи и новое название.
    9. Добавлять новых участников проекта, выбрав их из списка, где можно найти нужного пользователя по имени или никнейму, передав название проекта и никнеймы пользователей.

## Lab2

| Термин  | Краткое пояснение | Атрибуты                                                                                                                                                         | Ассоциированные термины                                                                                                                                                                             | Действия над предметом                                                                                                                                                                                                                                                                                                                                                                                           |
| :---- | :---- |:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Пользователь (User) | существующий (зарегистрированный) в системе пользователь | - ID<br/> - Имя<br/> - Никнейм <br/>- Пароль                                                                                                                     | - Гость <br/>- Участник <br/>- Исполнитель <br/><br/>Авторизовавшись или пройдя регистрацию гость становится пользователем. Пользователь может становится исполнителем задачи и участником проекта. | - Добавление в проект (участник проекта → *добавляет в проект* → пользователя (пользователь становится участником)). <br/><br/>- Поиск участника для добавления в проект или задачу (участник проекта → *ищет* → *участника по никнейму или имени*). <br/><br/>- Назначить исполнителем задачи(участник проекта → *назначает исполнителем задачи* → пользователя (пользователь становится исполнителем задачи)). |
| Гость (Guest) | Посетитель сайта, который не аутентифицирован. Ему нужно пройти регистрацию или ввести свои данные (никнейм и пароль). Не имеет идентичности все гости одинаковы |                                                                                                                                                                  | - Пользователь <br/><br/>Авторизовавшись или пройдя регистрацию гость становится пользователем.                                                                                                     | - Регистрация в системе(гость → *регистрируется* (гость становится пользователем)) <br/><br/>- Авторизация в системе(гость → *авторизируется* (гость становится пользователем))                                                                                                                                                                                                                                            |
| Проект (Project) | Логическая сущность, которая объединяет в себе некоторое количество *участников* проекта (они являются *пользователями*), которые могут создавать *задачи внутри* этого проекта, а также задачи проекта. Соответственно, только участники проекта могут просматривать его содержимое и изменять его. | - ID <br/>- Имя <br/>- Создатель <br/>- Дата создания <br/>- Дата последнего изменения <br/>- Участники                                                          | - Участник <br/>- Создатель  <br/> - Задача <br/><br/> В проекте есть участники и задачи, которые относятся к данному проекту                                                                       | - Создание (пользователь → *создает* → проект).  <br/><br/>- Изменение названия (пользователь создатель → *изменяет название* → проекта).  <br/><br/>- Удаление (пользователь создатель → *удаляет* → проект).  <br/><br/>- Просмотр (участник проекта → *просматривает* → проект).  <br/><br/>- Добавление участников (участник проекта → *добавляет участников* → в проект).                                   |
| Задача(Task) | Логическая сущность, содержащая информацию о конкретной задаче в рамках проекта. Содержит информацию для отслеживания выполнения данной задачи.  | - ID <br/>- Имя <br/>- Статус <br/>- Приоритет <br/>- Создатель <br/>- Дата создания <br/>- Дата последнего изменения <br/>- Оценка по времени <br/>-Исполнители | - Исполнитель <br/>- Создатель <br/>- Проект <br/><br/>Задача относится к определенному проекту. Исполнители относятся к определенной задаче.                                                       | \- Создание (участник проекта → *создает* → задачу).  <br/><br/>- Изменение (участник проекта → *изменяет* → задачу).  <br/><br/>- Удаление (участник проекта → *удаляет* → задачу).  <br/><br/>- Просмотр (участник проекта → *просматривает* → задачу).  <br/><br/>- Назначение исполнителя (участник проекта → *назначает исполнителя* → задачи).                                                             |
| Исполнитель(Assignee) | Пользователь, назначенный исполнителем на конкретную задачу.  |                                                                                                                                                                  | \- Задача <br/>- Пользователь <br/><br/>Исполнитель относится к определенной задаче. Исполнитель является пользователем.                                                                            | - Назначение исполнителя (участник проекта → *назначает* → исполнителя).                                                                                                                                                                                                                                                                                                                                         |
| Участник(Participant) | Пользователь добавленный в проект и способный производить внутри него действия с задачами и добавлять новых участников. |                                                                                                                                                                  | - Проект <br/>- Пользователь <br/><br/>Участник является пользователем. Участник относится к определенному проекту.                                                                                 | - Добавление участников (участник проекта → *добавляет* → участников).                                                                                                                                                                                                                                                                                                                                           |
| Создатель(Creator) | Пользователь, создавший проект или задачу в проекте. |                                                                                                                                                                  | - Проект <br/>- Пользователь <br/>- Задача <br/><br/>Создатель является пользователем, создавшим задачу или проект.                                                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                  || \- Прохождение (гость → *проходит*→ регистрацию).                                                                                                                                                                                                                                                                                                                                                                                                                                       |


| Название контекста | Краткое пояснение | Язык контекста                                                                                                                                                                                          |
| :---- | :---- |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Контекст пользователей(UserContext) | Этот контекст отвечает за управление пользователями системы, их регистрацией.  | - Пользователь   <br/>- Гость   <br/>- Регистрация   <br/>- Авторизация                                                                                                                                 |
| Контекст Проектов (Project Context)  | Контекст, который управляет проектами, их созданием и участниками.  | \- Проект   <br/>- Создатель   <br/>- Участник   <br/>- Изменение названия   <br/>- Добавление участника   <br/>- Удаление проекта   <br/>- Поиск пользоватлей                                          |
| Контекст Задач (Task Context)  | Этот контекст управляет задачами в рамках проектов, включая их создание и изменение.  | \- Задача   <br/>- Создатель   <br/>- Исполнитель   <br/>- Назначение исполнителя    <br/>- Изменение задачи   <br/>- Удаление задачи   <br/>- Поиск пользоватлей                                                                   |
| Контекст Управления Задачами (Task Management Context)  | Контекст, который охватывает действия, связанные с управлением задачами, такими как назначение исполнителей и изменение статусов задач.  | - Исполнитель  <br/>- Задача  <br/>- Назначение исполнителей   <br/>- Изменение имени задачи   <br/>- Изменение статуса задачи   <br/>- Изменение приоритета задачи  <br/>- Изменение оценки по времени |

## Lab 5


### **Функциональные требования**

*Пользователь должен иметь возможность…*

1. 	“Гость” может направить запрос в систему, существует ли уже пользователь с переданным никнеймом и получить ответ в формате “true”/”false” (QUERY)

2. 	Пройти регистрацию в системе, сменив статус “гостя” на “пользователя” системы, передав никнейм, имя и пароль.  (COMMAND)
    1.	Операция отклоняется с информативным сообщением, если пользователь с таким ником уже существует.  (COMMAND)

3. 	Создать проект, передав название проекта и никнейм пользователя-создателя проекта.  (COMMAND)

4. 	Создать задачу в проекте, передав название проекта и название задачи. Задача создается в статусе по умолчанию "CREATED".  (COMMAND)

5. 	Изменять список пользователя(-ей)  исполнителей задачи: добавить или удалить исполнителя, передав ID задачи и ID пользователя(-ей), если задача в статусе “не выполнено”  (COMMAND)

6. 	Найти пользователя в поиске, написав имя или никнейм. (QUERY)

7. 	Изменить статус задачи, передав ее id и новый статус.  (COMMAND)

8. 	Изменить название уже существующей задачи, передав ID задачи и новое название.  (COMMAND)

9. 	Добавлять новых участников проекта, выбрав их из списка, где можно найти нужного пользователя по имени или никнейму, передав ID проекта и ID пользователей.  (COMMAND)

10.  Создать новый статус, передав ID проекта, название статуса и цвет для отображения в UI.  (COMMAND)

11.  Удалить статус, если он не присвоен ни одной задаче.  (COMMAND)


| Функциональное требование | Агрегат | Команда (вводные аргументы) | Порождаемые ивенты
| :---- | :---- | :---- |:-------------------------------------------------------------------------------------|
| Пройти регистрацию в системе, сменив статус “гостя” на “пользователя” системы, передав никнейм, имя и пароль. | User | Create user (username, password) | \- USER CREATED<br/>- USER STATUS CHANGED
| Создать проект, передав название проекта и логин пользователя-создателя проекта. | User, Project | Create project (User.login, project\_name) | \- PROJECT CREATED
| Создать задачу в проекте, передав id проекта и название задачи. Задача создается в статусе по умолчанию "CREATED" | Task, Project, Status | Create task in project (Project.id, task\_name) | \- TASK CREATED<br/>- TASK STATUS CHANGED
| Изменять список пользователя(-ей)  исполнителей задачи: добавить или удалить исполнителя, передав ID задачи и ID пользователя(-ей), если задача в статусе “не выполнено” | Task, User | Add assignee (Task.id, User.id) Delete assignee (Task.id, User.id) | \- ASSIGNEE SET FOR TASK<br/>-    	ASSIGNEE DELETED FOR TASK
| Изменить статус задачи, передав ее id и новый статус (пользователь может выбрать один из доступных статусов проекта, к которому относится задача) | Task, Status | Change task status (Task.id, new\_status) | \- TASK STATUS CHANGED
| Изменить название уже существующей задачи, передав ID задачи и новое название. | Task | Change task name (Task.id, new\_name) | \- TASK NAME CHANGED
| Добавлять новых участников проекта, выбрав их из списка, *где можно найти нужного пользователя по имени или никнейму, передав ID проекта и ID пользователей.* | User, Project | Add project user (User.id, Project.id) <br/>Add project users (List \<User.id\>, Project.id)   | \- USER ADDED TO PROJECT<br/>- USER FOUND
| Cоздать новый статус, передав ID проекта, название статуса и цвет для отображения в UI | Status | Add status (project.id, Status.name, color) | \- NEW STATUS WITH COLOR IN PROJECT
| Удалить статус, если он не присвоен ни одной задаче | Status | Delete Status (Status.Id) | \- STATUS IN PROJECT DELETED


Запросов на запись у нас больше, чем запросов на чтение.
Чтобы улучшить баланс между ними,можно добавить следующие операции чтения:

1. Получить информацию о проекте (по Project.Id)
2. Список всех проектов пользователя (по User.Id)
3. Получить информацию о задаче (по Task.Id)
4. Список всех задач в проекте (по Project.Id, с фильтром по статусу)
5. Список всех статусов проекта (по Project.Id)
