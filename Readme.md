# Mission 2 
## Part 0
https://drive.google.com/drive/folders/1eUBtxBaIp0B0nfk-pl70XIxxEBH2uLlj?usp=sharing
## Part1
Вопрос 1.
SSH – это сетевой протокол, который обеспечивает безопасное подключение к операционным системам удаленно. 
Обычно используется для управления данными на сервере удаленно.

Вопрос 2.
Ключ можно добавить через текстовый редактор nano в командной строке. Нужно открыть файл authorized_keys в папке home/user1/.ssh с помощью 
команды nano и вставить ключ.

Вопрос 3.
При использовании long polling нужно периодически отправлять запросы к серверу Telegram для проверки новых сообщений.
По умолчанию запрос удерживается 30 секунд, затем его нужно повторить. Webhooks более эффективен, так как сервер сам отправляет сообщение на заранее заданный URL, без необходимости постоянных запросов. Недостаток: нужен публичный URL.

Вопрос 4.
Issues на GitHub используются для отслеживания ошибок, предложений по улучшению и других задач в проекте. 
Каждый issue представляет собой обсуждение, где разработчики могут разбивать задачу на подзадачи. 
Issues помогают командам улучшать взаимодействие и ускорять работу.

Вопрос 5.
Для отслеживания пустой директории в ней нуно создать пустой файл, чтобы Git начал её отслеживать.

# Mission 3 
## Part 1-3
https://drive.google.com/file/d/1ROaKYf2hpYycgn-ONvYfX5toKrmC7JxL/view?usp=sharing

## Part 3
1. получить список юзернеймов пользователей
  ```sql
select username from users
```

2. получить кол-во отправленных сообщений каждым пользователем: username - number of sent messages
```sql
select u.username, COUNT(m.text) as number_of_sent_messages 
from messages m
JOIN users u ON m.from = u.id
group by m.from, u.username
```

3. Получить пользователя с самым большим кол-вом полученных сообщений и само количество username - number of received messages
```sql
select u.username, COUNT(m.text) as number_of_recieved_messages
from messages m
join users u on m.to = u.id
group by u.username
order by number_of_recieved_messages DESC
limit 1;
```

4. Получить среднее кол-во сообщений, отправленное каждым пользователем
```sql
select avg(number_of_sent_messages) 
from  
(select u.username, COUNT(m.text) as number_of_sent_messages 
  from messages m
  join users u on m.from = u.id
  group by u.username
) as subquery;
```
