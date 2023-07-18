# Домашнее задание к занятию "`Система мониторинга Zabbix. Часть 2`" - `Викулов Александр`

### Задание 1

Процесс выполнения

1. Будем продолжать использовать две ВМ, созданные в предыдущем задании по Zabbix.
   Это два хоста, созданные на Yandex.Cloud. 
   
   * Первый хост: vikulov-vm-for-zabbix-server
     На этом хосте установлен Zabbix сервер и агент
   * Второй хост: vikulov-vm-for-zabbix-agent
     На этом хосте установлен Zabbix агент

   Обе машины с абсолютно одинаковыми конфигурациями, на борту Debian 11, находятся в одной подсети
  
   Внутренние IP адреса присвоены облаком Яндекс автоматически:
  
   * `vikulov-vm-for-zabbix-server: 192.168.0.3`
   * `vikulov-vm-for-zabbix-agent-linux: 192.168.0.34`
  
   Мониторинг для этих машин уже был настроен.
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img01-1.png">
   </kbd>
   <p></p> 
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img01-2.png">
   </kbd>
   <p></p> 

2. Перейдем на вкладку:
  
   <p></p>
   
   `Configuration -> Templates`
   
   <p></p>
   
   Нажмем на кпонку `Create template` в правом верхнем углу экрана и создадим новый шаблон, задав его описание.
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img02.png">
   </kbd>
   <p></p>
   
3. Видим, что шаблон появился в общем списке.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img03.png">
   </kbd>
   <p></p>


4. Теперь дополним наш шаблон элементами. 
   Эту задачу можно решить двумя способами: выбрать существующие item'ы, которые удоблетворяют нашим требованиям или создать собственные.
   С целью более глубже и шире разобраться в материале решим задачу обоими способами.
      
   <p></p>
   
   Для начала будем использовать уже существующие item'ы.
   
   <p></p>
   
   Выберем существующий шаблон, например `Linux CPU by Zabbix agent`, перейдем в раздел `Items` и выберем из списка те элементы, которые связаны с загрузкой CPU: 
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img04.png">
   </kbd>
   <p></p>
   

5. Нажмем на кнопку `Copy` и в откывшемся меню выберем наш шаблон `CPU-RAM monitroing`, в который будем копировать выбранные item'ы.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img05.png">
   </kbd>
   <p></p> 

6. Убедимся, что item'ы попали в наш template.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img06.png">
   </kbd>
   <p></p> 

7. Аналогичным образом добавим item'ы для мониторинга оперативной памяти.

   <p></p>
   
   Выберем шаблон `Linux memory by Zabbix agent` выберем нужные item'ы и скопируем в наш шаблон `CPU-RAM monitoring`.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img07-1.png">
   </kbd>
   <p></p>

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img07-2.png">
   </kbd>
   <p></p> 

8. Убедимся, что выбранные item'ы скопировались и дополнили наш template.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img08.png">
   </kbd>
   <p></p> 

9. Теперь, как было описано в пункте 4, решим эту же задачу, создав собственные item'ы.

   <p></p>
   
   Создадим item для CPU используя соответствущий ключ из списка доступных.
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img09-1.png">
   </kbd>
   <p></p>

   Создадим item для RAM используя соответствущий ключ из списка доступных.
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img09-2.png">
   </kbd>
   <p></p>


10. Убедимся, что требуемые item'ы были добавлены в наш шаблон (предыдущей стандартные были предварительно удалены).

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task01-img10.png">
   </kbd>
   <p></p>

---

### Задание 2

Процесс выполнения

1. Создам в Yandex.Cloud две новые виртуальные машины.

   * Хост `vikulovan-1`
   * Хост `vikulovan-2`
   
   Конфигурация машин будет аналогична машинам в задании 1.
   
   Внутренние IP адреса присвоены облаком Яндекс автоматически:
  
   * `vikulovan-1: 192.168.0.4`
   * `vikulovan-2: 192.168.0.20`

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img01.png">
   </kbd>
   <p></p>
   
2. Установим Zabbix-агент на машине `vikulovan-1`

  * Скачиваем пакет с репозиторием Zabbix

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img02-1.png">
   </kbd>
   <p></p>

  * Распаковываем
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img02-2.png">
   </kbd>
   <p></p>
   
  * Обновляем менеджер пакетов
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img02-3.png">
   </kbd>
   <p></p>

  * Устанавливаем Zabbix агент
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img02-4.png">
   </kbd>
   <p></p>

  * Добавляем в конфигурационный файл IP-адрес хоста, на котором расположен Zabbix сервер, чтобы разрешить подключение.
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img02-5.png">
   </kbd>
   <p></p>

  * Запускаем Zabbix агент и добавляем его в автозагрузку хоста
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img02-6.png">
   </kbd>
   <p></p>
   
  * Добавляем новый хост в админке Zabbix, указывая для подключения соответствующий IP адрес машины `vikulovan-1`.
    Для мониторинга выбираем шаблон `Linux by Zabbix agent`
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img02-7.png">
   </kbd>
   <p></p>
   
  * Видим, что хост подцепился.
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img02-8.png">
   </kbd>
   <p></p>

  * Видим, что данные приходят в разделе Latest Data
  
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img02-9.png">
   </kbd>
   <p></p>

3. Аналогичным будет процесс установки Zabbix агента на хост `vikulovan-2`.
   Не будем расписывать процесс так подробно. Покажем, что хост подцепился, и данные приходят в раздел Latest Data.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img03-1.png">
   </kbd>
   <p></p>
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task02-img03-2.png">
   </kbd>
   <p></p>

---

### Задание 3

Процесс выполнения

1. Добавим наш шаблон, созданный в задании 1, к новым хостам `vikulovan-1` и `vikulovan-2`.

   <p></p>
   
   Для начала перейдем по пути: `Configuration -> Templates`
   
   <p></p>
   
   Здесь можно увидеть какие шаблоны уже применены к хостам. 
   Видим, что они мониторятся с помощью шаблона `Linux by Zabbix agent`, который мы добавили в задании 2.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task03-img01.png">
   </kbd>
   <p></p>

2. Выберем машину `vikulovan-1` и в меню редактирования добавим созданный нами template `CPU-RAM monitoring`.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task03-img02.png">
   </kbd>
   <p></p>

3. Аналогично для машины `vikulovan-2`.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task03-img03.png">
   </kbd>
   <p></p>

4. Видим, что шаблон применился к двум нашим хостам.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task03-img04.png">
   </kbd>
   <p></p>

5. Проверяем через Latest Data, что наши item'ы по CPU и RAM пишутся.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task03-img05-1.png">
   </kbd>
   <p></p>

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task03-img05-2.png">
   </kbd>
   <p></p>
   
---

### Задание 4

Процесс выполнения

1. Через админку Zabbix создадим новый дашборд

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task04-img01.png">
   </kbd>
   <p></p>

2. Будем выводить информацию о скачках нагрузки на всех четырех хостах.
   Создадим сперва новый виджет с CPU jumps для Zabbix сервера.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task04-img02.png">
   </kbd>
   <p></p> 
    
3. Аналогичный график выведем для остальных хостов.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task04-img03.png">
   </kbd>
   <p></p>

4. Дашборд создан

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task04-img04.png">
   </kbd>
   <p></p>

---
## Дополнительные задания (со звездочкой*)

Эти задания дополнительные (не обязательные к выполнению) и никак не повлияют на получение вами зачета по этому домашнему заданию. Вы можете их выполнить, если хотите глубже и/или шире разобраться в материале.

### Задание 5* со звездочкой

1. Первым делом добавим изображение для нашей карты.
   
   <p></p>
   
   Перейдем по следующему пути в меню в админке Zabbix:
   
   <p></p>
   
   `Administration -> General -> Imagies`
   
   <p></p>
   
   Далее в правом верхнем углу сменим тип на `background` и нажмем кпонку `Create background`.
   
   <p></p>
   
   Выберем файл с картой из локальной папки и добавим её.
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img01.png">
   </kbd>
   <p></p>

2. Далее создадим карту.

   <p></p>
   
   Перейдем по следующему пути в меню в админке Zabbix:
   
   <p></p>
   
   `Monitoring -> Maps`
   
   <p></p>
   
   Далее в правом верхнем углу нажмем кпонку `Create map`.
   
   <p></p>
   
   На экране создания введем название карты, выберем созданный бэкграунд. 
   Указываем длину и высоту карты согласно оригинальному изображению.
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img02.png">
   </kbd>
   <p></p>

3. Видим, что наша карта создалась и появилась в списке доступных.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img03.png">
   </kbd>
   <p></p>

4. Начнем располагать наши хосты на карте.

   <p></p>
   
   Согласно заданию надо расположить на карте только два хоста, но для закрепления навыка расположим все четыре.
   
   <p></p>
   
   Сначала установим Zabbix сервер в районе города Минас-Тирит.
   Свяжем хост с его изображением установкой соответствующих параметров.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img04.png">
   </kbd>
   <p></p>

5. Далее расположем остальные сервера.

   * Хост `vikulov-vm-for-zabbix-agent` установим в Эдорасе.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img05-1.png">
   </kbd>
   <p></p>

   * Хост `vikulovan-1` установим у эльфов в Ривенделле.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img05-2.png">
   </kbd>
   <p></p>
   
   * Хост `vikulovan-2` установим у гномов Одинокой горы.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img05-3.png">
   </kbd>
   <p></p>

6. Создадим линки между Zabbix сервером и хостами с агентами.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img06.png">
   </kbd>
   <p></p>

7. Для каждой из связей зададим триггер на отсутствие связи с агентом.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img07.png">
   </kbd>
   <p></p>

8. Остановим Zabbix агенты на серверах

   * На хосте `vikulov-vm-for-zabbix-agent`

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img08-1.png">
   </kbd>
   <p></p>

   * На хосте `vikulovan-1`

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img08-2.png">
   </kbd>
   <p></p>
   
   * На хосте `vikulovan-2`

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img08-3.png">
   </kbd>
   <p></p>

9. Проверим карту, и увидим, что триггер на связях сработал.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task05-img09.png">
   </kbd>
   <p></p>

---

### Задание 6* со звездочкой

1. Напишем скрипт на bash согласно заданию.
   
   <p></p>

   ```
   #!/bin/bash

   if [[ $1 == 1 ]]; then
	echo "Vikulov Aleksandr Nikolaevich"
   fi

   if [[ $1 == 2 ]]; then
	date
   fi
   ```
   
   <p></p>

2. Зайдем на Zabbix сервер и создадим файл с этим скриптом в директории
   `/etc/zabbix/zabbix_agentd.d`
    
    <p></p>
    
    Назовем файл `name-date.sh`.
    
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task06-img02.png">
   </kbd>
   <p></p>

3. В этой же папке создадим дополнительный файл конфигурации `user_parameters.conf`.
   По аналогии с лекцией пропишем в этом файле три юзер параметра в зависимости от использования скрипта:
   
   * Параметр `name_check`, где сразу подаем 1 в скрипт, чтобы он вернул ФИО
   * Параметр `date_check`, где сразу подаем 2 в скрипт, чтобы он вернул текущую дату
   * Параметр `name_date[*]`, на вход которого будем подавать параметры вручную
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task06-img03.png">
   </kbd>
   <p></p>

4. Теперь идем в админку Zabbix.

   <p></p>
   
   Проходим в основном меню в `Configuration -> Templates`.
   Находим созданный нами шаблон `CPU-RAM monitoring`.
   Переходим в `Items` этого шаблона.
   В правом верхнем углу щелкаем `Create item`.

5. Далее создаем четыре разных item'а, используя наши UserParameters.

   * Item `Name check`, который использует юзер параметр `name_check`
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task06-img05-1.png">
   </kbd>
   <p></p>
   
   * Item `Date check`, который использует юзер параметр `date_check`
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task06-img05-2.png">
   </kbd>
   <p></p>
   
   * Item `Name-date script 1`, который использует юзер параметр `name_date` c 1 на входе
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task06-img05-3.png">
   </kbd>
   <p></p>
   
   * Item `Name-date script 2`, который использует юзер параметр `name_date` c 2 на входе
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task06-img05-4.png">
   </kbd>
   <p></p>

6. Добавим к Zabbix серверу наш шаблон `CPU-RAM Monitoring`

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task06-img06.png">
   </kbd>
   <p></p>

7. И посмотрим в `Latest Data` наши созданные UserParameters

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task06-img07-1.png">
   </kbd>
   <p></p>
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task06-img07-2.png">
   </kbd>
   <p></p>

   Как видим всё работает корректно.
   Item'ы `Name check` и `Name-date script 1` возвращают ФИО.
   Item'ы `Date check` и `Name-date script 2` возвращают дату.

---

### Задание 7* со звездочкой

1. Дополним python скрипт из лекции согласно заданию.

<p></p>

```
import sys
import os
import re
from datetime import date

if (sys.argv[1] == '-ping'):
    result = os.popen("ping -c 1 " + sys.argv[2]).read()
    result = re.findall(r"time=(.*) ms", result)
    print(result[0])
elif (sys.argv[1] == '-simple_print'):
    print(sys.argv[2])
elif (sys.argv[1] == '1'):
    print("Vikulov Aleksandr Nikolaevich")
elif (sys.argv[1] == '2'):
    print(date.today())
else:
    print(f"unknown input: {sys.argv[1]}")
```

<p></p>

2. Зайдем на Zabbix сервер и создадим файл с этим скриптом в директории
   `/etc/zabbix/zabbix_agentd.d`
    
    <p></p>
    
    Назовем файл `param.py`.
    
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img02.png">
   </kbd>
   <p></p>

3. Откроем созданный в задании 6 файл `user_parameters.conf`, который лежит в этой же папке.
   Будем дополнять этот файл новыми параметрами, используя python скрипт.
   Прошпишем пять новых юзер параметров:
   
   * Параметр `custom_py_ping[*]`, где сразу пингуем какой-то хост, кототый подаем на вход
   * Параметр `custom_py_print[*]`, где сразу выводим на экран то, что подаем на вход
   * Параметр `custom_py_name`, где сразу подаем на вход скрипта 1, чтобы получить ФИО
   * Параметр `custom_py_date` где сразу подаем на вход скрипта 2, чтобы получить дату
   * Параметр `custom_py_script`, в котором скрипт используется в своей полной форме
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img03.png">
   </kbd> 

4. Теперь идем в админку Zabbix.

   <p></p>
   
   Проходим в основном меню в `Configuration -> Templates`.
   Находим созданный нами шаблон `CPU-RAM monitoring`.
   Переходим в `Items` этого шаблона.
   В правом верхнем углу щелкаем `Create item`.

5. Создадим восемь новых item'ов, используя новые юзер параметры.
   Первые четыре на основе параметров с настроенным скриптом, вторые четыре на основе параметра с полным скриптом.
   
   <p></p>
   
   Первые четыре item'а будут следующие:

   * Item `Py_ping_param`, который использует юзер параметр `custom_py_ping[*]`
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img05-1.png">
   </kbd>
   <p></p>
   
   * Item `Py_print_param`, который использует юзер параметр `custom_py_print[*]`
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img05-2.png">
   </kbd>
   <p></p>
   
   * Item `Py_name_param`, который использует юзер параметр `custom_py_name`
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img05-3.png">
   </kbd>
   <p></p>
   
   * Item `Py_date_param`, который использует юзер параметр `custom_py_date` c 2 на входе
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img05-4.png">
   </kbd>
   <p></p>
   
6. Item'ы на основе полного скрипта будут подовать на его вход разные параметры:

   * Item `Py_script_ping`, который использует юзер параметр `custom_py_script[*]` с параметрами для пинга
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img06-1.png">
   </kbd>
   <p></p>
   
   * Item `Py_script_print`, который использует юзер параметр `custom_py_script[*]` с параметрами для принта
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img06-2.png">
   </kbd>
   <p></p>
   
   * Item `Py_script_name`, который использует юзер параметр `custom_py_script[*]` с 1 для получения ФИО
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img06-3.png">
   </kbd>
   <p></p>
   
   * Item `Py_script_date`, который использует юзер параметр `custom_py_script[*]` с 2 для получения даты
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img06-4.png">
   </kbd>
   <p></p>

7. Зайдем в `Latest Data`.
   Увидим, что все item'ы приходят и значения соответствуют требуемым.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task07-img07.png">
   </kbd>
   <p></p>

---

### Задание 8* со звездочкой


1. Удалим все три хоста с Zabbix агентами

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task08-img01.png">
   </kbd>
   <p></p>

2. Создадим Discovery Action.
   Триггерами будут все работающие хосты с Zabbix агентами
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task08-img02.png">
   </kbd>
   <p></p>

3. Настроим в Discovery Action следующие операции:

   * Будем добавлять хост в группу `Linux servers`
   * Будем применять к хосту шаблон `Linux by Zabbix agent`
   * Будем применять к хосту наш собтсвенный созданный ранее в предыдущих задания шаблон `СPU-RAM monitoring`
   
   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task08-img03.png">
   </kbd>
   <p></p>

4. Настроим правило Discovery для локальной сети

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task08-img04.png">
   </kbd>
   <p></p>

5. Перейдем в раздел Discovery и удивим, что хосты были обнаружены

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task08-img05.png">
   </kbd>
   <p></p>

6. Перейдем в раздел Hosts и увидим, что хосты были добавлены, и к ним применены нужные шаблоны.

   <p></p>
   <kbd> 
     <img src="https://github.com/AleksandrVikulov/08-03-zabbix-part-02/blob/master/img/task08-img06.png">
   </kbd>
   <p></p>


