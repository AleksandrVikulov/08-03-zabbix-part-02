# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Викулов Александр`

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
   
   Нажмем на кпонку `Create template' в правом верхнем углу экрана и создадим новый шаблон, задав его описание.
   
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
   
   Для начала будем использоваться уже существующие item'ы.
   
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

1. 

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

---

### Задание 3

Процесс выполнения

1. 

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

---

### Задание 4

Процесс выполнения

1. 

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

---
## Дополнительные задания (со звездочкой*)

Эти задания дополнительные (не обязательные к выполнению) и никак не повлияют на получение вами зачета по этому домашнему заданию. Вы можете их выполнить, если хотите глубже и/или шире разобраться в материале.

### Задание 5*

1. 

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

---

### Задание 6*

Процесс выполнения

1. 

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

---

### Задание 7*

Процесс выполнения

1. 

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

---

### Задание 8*

Процесс выполнения

1. 

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

---

### Задание 9*

Процесс выполнения

1. 

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

