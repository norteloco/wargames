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