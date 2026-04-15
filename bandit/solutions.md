> [!CAUTION]
>
> ### СПОЙЛЕРЫ
> Данный репозиторий содержит решения мини-игр с сайта [owerthewire.org](https://overthewire.org/)  
> Если вы решили испытать себя и пройти эти задачи самостоятельно, то я рекомендую  
> не читать далее этого предупреждения! 

# Решения

Несмотря на предупреждения в [readme.md](../readme.md), Я дополнительно повторю, что самостоятельно решил не все задачи. Те задачи, которые не были решены мной будут отмечены.

## Level 0

**Описание:**  
`Цель этого уровня — войти в игру по протоколу SSH. Хост, к которому нужно подключиться, — bandit.labs.overthewire.org, порт 2220. Имя пользователя — bandit0, пароль — bandit0. После входа в систему перейдите на страницу первого уровня, чтобы узнать, как его пройти.`

<details>
    <summary>Решение</summary>  

```
ssh bandit0@bandit.labs.overthewire.org -p 2220 / пароль: bandit0
```
</details>

## Level 1

**Описание:**  
`Цель этого уровня — войти в игру по протоколу SSH. Хост, к которому нужно подключиться, — bandit.labs.overthewire.org, порт 2220. Имя пользователя — bandit0, пароль — bandit0. После входа в систему перейдите на страницу первого уровня, чтобы узнать, как его пройти.`

<details>
    <summary>Решение</summary>  

```
head readme
```  
**Результат**:  
`Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!
The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`


</details>  


## Level 2

**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле с именем -, расположенном в домашнем каталоге.`

<details>
    <summary>Решение</summary>  

```
head ./-
```  
**Результат**:  
`263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

</details>  

## Level 3

**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле с именем --spaces in this filename--, расположенном в домашнем каталоге.`

<details>
    <summary>Решение</summary>  

```
head ./--spaces\ in\ this\ filename--
или же
head ./'--spaces in this filename--'
```  

**Результат**:  
`MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

</details>  

## Level 4

**Описание:**  
`Пароль для перехода на следующий уровень хранится в скрытом файле в папке inhere.`

<details>
    <summary>Решение</summary>  

```
ls -la inhere/
head inhere/...Hiding-From-You 
```  

**Результат**:  
`2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

</details>  


## Level 5

**Описание:**  
`Пароль для перехода на следующий уровень хранится в единственном доступном для чтения файле в каталоге inhere. Совет: если ваш терминал завис, попробуйте команду reset.`

<details>
    <summary>Решение</summary>  

```
find inhere/ -type f -exec file '{}' \;
cat inhere/-file05
```  

**Результат**:  
`4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

</details>  


## Level 6

**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле, который находится где-то в каталоге inhere, и обладает всеми следующими свойствами:`  
- `удобочитаемый`  
- `размер 1033 байта`  
- `неисполняемый`  

<details>
    <summary>Решение</summary>  

```
find inhere/ \! -executable -type f -size 1033c -exec head {} \;
```  

**Результат**:  
`HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

</details>  

## Level 7


**Описание:**  
`Пароль для перехода на следующий уровень хранится где-то на сервере и обладает всеми следующими свойствами:`  

- `принадлежит пользователю bandit7`  
- `принадлежит группе bandit6`  
- `размер 33 байта`  

<details>
    <summary>Решение</summary>  

```
find / -type f -size 33c -group bandit6 -user bandit7 -exec head '{}' \; 2>&1 | grep -v "find"
```  

**Результат**:  
`morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

</details> 

## Level 8


**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле data.txt рядом со словом millionth`  

<details>
    <summary>Решение</summary>  

```
cat data.txt | grep -e "millionth" | awk '{print $2}'
```  

**Результат**:  
`dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

</details> 

## Level 9


**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле data.txt и представляет собой единственную строку текста, которая встречается только один раз.`  

<details>
    <summary>Решение</summary>  

```
awk '{print $1}' data.txt | sort | uniq -c | sort -nk 1 | head -n 1 | awk '{print $2}'
```  

**Результат**:  
`4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

</details> 

## Level 10


**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле data.txt в одной из нескольких удобочитаемых строк, перед которыми стоит несколько символов «=».`  

<details>
    <summary>Решение</summary>  

```
strings -d data.txt | grep == | awk '{print $2}' | tail -n 1
```  

**Результат**:  
`FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

</details> 

## Level 11


**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле data.txt, который содержит данные в кодировке base64.`  

<details>
    <summary>Решение</summary>  

```
cat data.txt | base64 -d | awk '{print $4}'
```  

**Результат**:  
`dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

</details> 

## Level 12 👀


**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле data.txt, где все строчные (a-z) и прописные (A-Z) буквы сдвинуты на 13 позиций.`  

*Я ни разу не пользовался утилитой tr и потому подглядел ответ для данного уровня.*  
*Расстроился потому что он оказался довольно простым.*

<details>
    <summary>Решение</summary>  

```
cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
```  

**Результат**:  
`7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

</details> 

## Level 13


**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле data.txt, который представляет собой шестнадцатеричный дамп файла, многократно сжатого. Для этого уровня может быть полезно создать в /tmp каталог, в котором вы сможете работать. Используйте команду mkdir, присвоив ей трудно угадываемое имя. А еще лучше используйте команду mktemp -d. Затем скопируйте файл datafile с помощью cp и переименуйте его с помощью mv (прочитайте справочные страницы!).`  

*В какой-то момент я думал, что иду по второму кругу. Нужно было выбирать именя для файлов получше.*

<details>
    <summary>Решение</summary>  

```
    cd $(mktemp -d)    
    cp ~/data.txt .
    head data.txt
    xxd -r data.txt > output
    file output
    mv output output.gz
    gunzip output.gz
    file output
    bunzip output
    file output.out
    mv output.out output.gz
    gunzip output.gz
    mv output output.tar
    tar -xvf output.tar
    file data5.bin
    mv data5.bin output.tar
    tar -xvf output.tar
    mv  data6.bin output.bz2
    bunzip2 output.bz2
    file output
    mv output output.tar
    tar -xvf output.tar
    mv data8.bin output.gz
    gunzip output.gz
    file output
    cat output
```  

**Результат**:  
`FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

</details> 

## Level 14

**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле /etc/bandit_pass/bandit14 и доступен только пользователю bandit14. На этом уровне вы не получите следующий пароль, но получите закрытый SSH-ключ, который можно использовать для входа на следующий уровень. Посмотрите, какие команды использовались для входа на предыдущие уровни Bandit, и узнайте, как использовать ключ для входа на этот уровень.`  

<details>
    <summary>Решение</summary>  

```
cat sshkey.private
```  
`Копируем пароль в файл, задаем права 600 или на Windows доступ только текущему пользователю.`
`Подключаемся с использованием полученного приватного ключа.`

```
ssh bandit14@bandit.labs.overthewire.org -p 2220 -i sshkey.private
```

**Результат**:  
```
RSA PRIVATE KEY
```

</details> 

## Level 15

**Описание:**  
`Пароль для перехода на следующий уровень можно получить, отправив пароль текущего уровня на порт 30000 на локальном хосте.`  

<details>
    <summary>Решение</summary>  

```
nc localhost 30000 < /etc/bandit_pass/bandit14
```  

**Результат**:  
`8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`

</details> 

## Level 16

**Описание:**  
`Пароль для перехода на следующий уровень можно получить, отправив пароль текущего уровня на порт 30001 на локальном хосте с использованием шифрования SSL/TLS.`  

<details>
    <summary>Решение</summary>  

```
openssl s_client -connect localhost:30001
<password>
```  

**Результат**:  
`kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`

</details> 

## Level 17

**Описание:**  
`Учетные данные для следующего уровня можно получить, отправив пароль текущего уровня на порт localhost в диапазоне от 31000 до 32000. Сначала выясните, на каких из этих портов работает сервер. Затем определите, какие из них поддерживают протокол SSL/TLS, а какие нет. Только один сервер выдаст вам следующие учетные данные, остальные просто отправят вам то, что вы им отправили.`  

<details>
    <summary>Решение</summary>  

```
nc -zv localhost 31000-32000 2>&1 | grep succeeded | awk '{print $5}'
  
openssl s_client -nocommands -connect localhost:31046
openssl s_client -nocommands -connect localhost:31518
openssl s_client -nocommands -connect localhost:31691
openssl s_client -nocommands -connect localhost:31790
openssl s_client -nocommands -connect localhost:31960
```  

**Результат**:  
```
RSA PRIVATE KEY
```

</details> 

## Level 18

**Описание:**  
`В домашней директории есть два файла: passwords.old и passwords.new. Пароль для следующего уровня находится в файле passwords.new, и это единственная строка, которая была изменена в файле passwords.old по сравнению с passwords.new`  

<details>
    <summary>Решение</summary>  

```
diff passwords.old passwords.new | tail -n 1 | awk '{print $2}'
```  

**Результат**:  
`x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

</details> 

## Level 19

**Описание:**  
`Пароль для перехода на следующий уровень хранится в файле readme в домашней директории. К сожалению, кто-то изменил файл .bashrc, чтобы вы выходили из системы при входе через SSH.`  


<details>
    <summary>Решение</summary>  

```
ssh bandit18@bandit.labs.overthewire.org -p 2220 'head readme'
```  

**Результат**:  
`cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`

</details> 

## Level 20

**Описание:**  
`Чтобы получить доступ к следующему уровню, вам нужно использовать бинарный файл setuid в домашней директории. Запустите его без аргументов, чтобы узнать, как им пользоваться. Пароль для этого уровня можно найти в обычном месте (/etc/bandit_pass) после запуска бинарного файла setuid.`  


<details>
    <summary>Решение</summary>  

```
./bandit20-do cat /etc/bandit_pass/bandit20
```  

**Результат**:  
`0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`

</details> 

## Level 21

**Описание:**  
`В домашней директории есть бинарный файл с установленным бинарно-зависимым модулем, который выполняет следующие действия: устанавливает соединение с локальным хостом через порт, указанный в качестве аргумента командной строки. Затем считывает строку текста из соединения и сравнивает ее с паролем предыдущего уровня (bandit20). Если пароль верный, он передает пароль для следующего уровня (bandit21).`  


<details>
    <summary>Решение</summary>  

```
cat /etc/bandit_pass/bandit20 | nc -lvp 3000 & ./suconnect 3000
```  

**Результат**:  
`EeoULMCra2q0dSkYj561DX7s1CpBuOBt`

</details> 

## Level 22

**Описание:**  
`Программа автоматически запускается через равные промежутки времени с помощью cron — планировщика заданий по расписанию. Найдите в /etc/cron.d/ конфигурацию и посмотрите, какая команда выполняется.`  


<details>
    <summary>Решение</summary>  

```
head /etc/cron.d/cronjob_bandit22
head /usr/bin/cronjob_bandit22.sh 
head /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```  

**Результат**:  
`tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q`

</details> 

## Level 23

**Описание:**  
`Программа автоматически запускается через равные промежутки времени с помощью cron — планировщика заданий по расписанию. Найдите в /etc/cron.d/ конфигурацию и посмотрите, какая команда выполняется.`  


<details>
    <summary>Решение</summary>  

```
head /etc/cron.d/cronjob_bandit23
cat /usr/bin/cronjob_bandit23.sh 
cat /tmp/$(echo I am user bandit23 | md5sum | cut -d ' ' -f 1)
```  

**Результат**:  
`0Zf11ioIjMVN551jX3CmStKLYqjk54Ga`

</details> 

## Level 24

**Описание:**  
`Программа автоматически запускается через равные промежутки времени с помощью cron — планировщика заданий по расписанию. Найдите в /etc/cron.d/ конфигурацию и посмотрите, какая команда выполняется.`  

`ПРИМЕЧАНИЕ. На этом уровне вам нужно создать свой первый скрипт. Это очень важный шаг, и вы должны гордиться собой, когда пройдете этот уровень!`  

`ПРИМЕЧАНИЕ 2. Помните, что после выполнения скрипт удаляется, поэтому лучше сохранить его копию…`

<details>
    <summary>Решение</summary>  

```
head /etc/cron.d/cronjob_bandit24
cat /usr/bin/cronjob_bandit24.sh 
cd $(mktemp -d)
vim script.sh
chmod +x script.sh
chmod -R 777 $PWD
cp script.sh /var/spool/bandit24/foo/script.sh
cat bandit24
```  

***script.sh:***
```
#!/bin/bash
echo "$(cat /etc/bandit_pass/bandit24)" > /tmp/<tempdir>/bandit24
chmod 777 /tmp/<tempdir>/bandit24
```

**Результат**:  
`gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8`

</details> 

## Level 25

**Описание:**  
`Демон-сервер прослушивает порт 30002 и выдаст вам пароль для bandit25, если вы сообщите ему пароль для bandit24 и секретный четырехзначный пин-код. Пин-код можно узнать, только перебрав все 10 000 комбинаций, то есть методом полного перебора.`
`Вам не нужно каждый раз создавать новые соединения`

<details>
    <summary>Решение</summary>  

```
echo "$(seq -f "$(cat /etc/bandit_pass/bandit24) %04g" 0 9999)" | nc localhost 30002 | grep -v Please
```  
*Примечание: `grep -v Please` указано т.к. слово **Please** встречается в 2-х типах сообщений из 3-х: Сообщении о прослушивании и сообщении об ошибке.*

**Результат**:  
`iCi86ttT4KSNe1armKiwbQNmB3YJP3q4`

</details> 

## Level 26 & Level 27

**Описание:**  
`Войти в систему под пользователем bandit26 из системы под пользователем bandit25 должно быть довольно просто… Оболочка пользователя bandit26 — это не /bin/bash, а что-то другое. Узнайте, что это за оболочка, как она работает и как из нее выйти.`

*Примечание: Я не догадался до решения самостоятельно. То ли привык использовать VS Code для подключения по SSH, то ли просто не хватило извилин мозга, но этот уровень я запомню навсегда.*

<details>
    <summary>Решение</summary>  

```
cat bandit26.sshkey

Уменьшаем размер консоли до 1-2 строк и подключаемся по ssh
ssh bandit26@bandit.labs.overthewire.org -p 2220 -i bandit26.sshkey
Видим <--- MORE --->
Открываем vim по нажатию на v
:set shell=/bin/bash
:sh
```  

*Далее мы выполняем часть уровня 27*

```
ls -la
./bandit27-do cat /etc/bandit_pass/bandit27
```

**Результат**:  
`upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB`

</details> 