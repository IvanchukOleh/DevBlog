---
layout: post
title:  "How to use Tournaman 2.0"
visible: 0
permalink: /tournaman/
categories: []
tags: []
author: Matanist
---

* content
{:toc}

## Передісторія
До основної тематики блогу написане нижче не має ніякого стосунку, але мене часто просять допомогти із проведенням дебатних турнірів, на які не завжди є час. 
Тому вирішив описати те, чим зазвичай на турнірах займаюсь, щоб людина, яка з цим раніше не стикалася, але має більше вільного часу, могла мене замінити.  
Що таке дебати і як вони проходять описувати не буду. Припускаю, що людина, яка це читає, має якесь уявлення про те, що то за дебати і як вони проходять. 
Якщо і ні — за цією інструкцією можна буде виконати роботу тебмайстра не розбираючись до кінця в самих дебатах.

## Суть роботи тебмайстра
Тебмайстер — це людина, яка на дебатному турнірі опрацьовує результати, отримані від суддів. На основі цих даних формує турнірну сітку.  
Оскільки зараз вже XXI століття, значна частина цього процесу є автоматизованою, тебмайстру залишається лише вводити результати, отримані від суддів, та показувати їх учасникам.  
Для формування турнірної сітки досить часто використовується програма Tournaman (є інші, але з ними особисто я не працював, тому детальніше розглянемо саме турнаман).  
В базовий набір тебмайстра входять прямі руки, свіжий розум, комп’ютер із встановленою ОС Windows, встановлений PowerPoint. Доступ до мережі є дуже бажаним, але якщо із цим геть туго, то можна обійтися і без нього. Навички роботи із електронними таблицями вітаються, але не є обов’язковими, оскільки в цій інструкції буде описано все, що може знадобитися.

## Підготовка до турніру
Робота тебмайстра зазвичай починається за день до турніру (якщо раніше, то це можна вважати дивом організованості, але із таким ще не стикався. Якщо вже є досвід, то все можна зробити в день турніру за пів години до його початку, але краще все протестувати ввечері попереднього дня, щоб не було казусів. Всяке буває, а лажати — це не круто).  
Що варто зробити **до** початку турніру:
* **з’ясувати, що то за турнір;**  
цей пункт можна проігнорувати, але, думаю, варто виявити хоч трохи поваги до організаторів. Вони старалися, придумуючи назву (і не тільки)  
* **отримати доступ до суддівського чату;**  
доступ до чату потрібен для того, щоб мати канал зв’язку із суддями (ага, я знаю, що це здається очевидним, та все ж)  
* **отримати запрошення до спільноти турніру;**  
якщо тебмайстер має скидати тему і сітку раунді в спільноту, то треба мати ще й достатній рівень доступу для цього (якщо публікуванням теми і сітки займається інша людина — достатньо мати контакти тієї людини).  
Додатковим бонусом цього пункту є можливість уникнути незручних питань до організаторів, якщо вже погодилися, минув якийсь час, а спитати хоч що то за турнір забули (а взагалі не треба так)  
* **отримати список суддів і їх ранкінг;**  
звичайний перелік імен із прізвищами, а також цифрою від 0 до 9, де 9 — найвищий рівень досвіду судді (або довіри до судді), 0 — найнижчий. Цей список отримується від організаторів турніру або головного судді (гс). Ранкінг зазвичай визначає гс  
* **отримати _актуальний_ список команд;**  
список учасників — це табличка із рядками ```Назва команди | учасник1 | учасник2```. Зазвичай отримується від організаторів турніру. Може змінюватися безпосередньо перед початком турніру, тому **не варто** поспішати із формуванням сітки для першого раунду  
* **спробувати дізнатися теми на кожен раунд, або домовитися про спосіб їх отримання;**  
якщо гс скине всі теми до початку турніру — можна сміливо відмічати цей день в календарі. Це означатиме, що попався надзвичайно організований гс _(він точно людина?)_, який ще й виявив майже небачений акт довіри до тебмайстра _(за 3 роки зі мною таке сталося аж 1 раз)_  
* **домовитися про те, яким чином будуть передаватися результати від суддів;**  
практика показала, що найкращим для тебмайстра способом взаємодії із суддями є гугл форми в комбінації із телеграмом (або будь-яким іншим зручним месенджером, але телеграм використовується найчастіше. Принаймні поки мені інші не траплялися на турнірах)  
* **домовитися про те, яким чином будуть отримуватися фітбеки на суддів від учасників;**  
фітбеки на суддів теж досить зручно отримувати через гугл форми  
* **створити проект в Tournaman і підготувати дані для початку першого раунду.**  
процес створення проекту в турнамані буде описано нижче.  

### Google forms
Для передачі результатів від суддів до тебмайстра або ж фітбеків на суддів від команд можна використовувати древні методи (паперові бланки), але це завдає певних незручностей. Як мінімум, тебмайстру доведеться розбирати ті каракулі (а це не завжди просто. Особливо, коли суддя любить помалювати). Також дані доведеться вносити в якусь електронну табличку для спрощення подальшої обробки. Тому значно легшим і практичнішим способом збору необхідної інформації є використання гугл форм. Додатковим бонусом є те, що в гугл формах можна зробити певні поля обов’язковими до заповнення, тобто суддя просто не зможе надіслати результат, поки не заповнить все так, як треба.  
Створити власну гугл форму можна за [посиланням](https://docs.google.com/forms "Google forms").  
При створенні форми буде використано такі типи полів: 
* **спадний список;**  
список суддів та раунд, щоб суддям не доводилося набирати цей текст вручну. Та і легше потім працювати із даними, якщо прізвища та імена 100% написані однаково;  
* **таблиця з варіантами відповіді;**  
розстановка місць в кожному раунді. Суддям треба буде лише поставити позначки на перетині відповідних рядків (позиція команди) і стовпців (зайняте місце);  
* **питання з короткими відповідями.**  
для вписування імен та балів кожного гравця а також для поміток щодо промов російською мовою (за промови не українською знімаються бали в кінцевому результаті).  
  
Перш за все потрібно створити випадаючий список із суддями. Це має бути обов’язковим до заповнення полем. Виглядати це має якось так:  
![Tournaman](/assets/2020-02-08-tournaman_0_1.png)  
Наступним кроком є формування списку із раундами. Робиться аналогічно до списку суддів. Просто номери раундів. За потреби їх кількість може змінюватися. Це теж обов’язкове поле:  
![Tournaman](/assets/2020-02-08-tournaman_0_2.png)  
В таблиці із варіантами відповідей потрібно додати список позицій (1У - перший уряд, 1О — перша опозиція, 2У — другий уряд, 2О — друга опозиція) та місць (число від 1 до 4). Теж обов’язкове поле:  
![Tournaman](/assets/2020-02-08-tournaman_0_3.png)  
Наступним блоком є поля із іменами і балами дебатерів. Це поля із короткими відповідями, де суддям потрібно буде ввести дані вручну, не зі списку. Звертаю увагу, що обов’язковими є поля із балами та ім’ям першого гравця. Якщо суддя дуже поспішатиме, то в нього буде можливість упустити друге ім’я і даних все ж буде достатньо для визначення того, хто ким є і кому які бали поставили. Такий блок із 4 полів треба буде створити для кожної позиції (1У, 2О, 2У, 2О). Не рекомендую писати якісь довгі імена полів, бо потім в табличці на екран може не поміститися інформація про раунд цілком.  
![Tournaman](/assets/2020-02-08-tournaman_0_4.png)  
В останньому полі суддям потрібно буде вказати, чи були промови російською, оскільки за це знімаються бали у підсумковому підрахунку. Не рекомендую додавати таке поле до кожного гравця окремо, бо судді будуть проклинати купу "галочок" (оскільки результати зазвичай подаються із телефону, то чим менше полів — тим краще). Із часом дійшов до такого формулювання:  
```Промови російською були (так/ні)? Якщо так — напиши позицію та ім’я, напр. "1У Олег, 2О Оксана"```,  
а результат потрібно ввести в поле із короткою відповіддю:  
![Tournaman](/assets/2020-02-08-tournaman_0_5.png)  
  
  
*-----*  
*Про прив’язку до таблички, збір результатів і фітбеки на суддів напишу пізніше.*  
*-----*  

P. S. створені форми і таблички із відповідями зручно додавати в закладки браузера, створивши окрему папку із назвою турніру. Це значно економить час, якщо раптом дістанеться комп’ютер, який регулярно хвалиться "синім екраном смерті" (особистий рекорд - разів 6 за турнір. Тому ніколи не нехтуй цією порадою. Особливо, якщо працюєш не зі свого компа).

### Tournaman
Це програма, яка використовується для формування турнірної сітки та створення презентацій для кожного раунду із темою та, власне, сіткою.  
Саму програму можна знайти за [посиланням](http://tournaman.wikidot.com/download "Tournaman tabbing software").  
  
![Tournaman](/assets/2020-02-08-tournaman_0_0.png)  
  
Перше, що потрібно зробити в турнамані — це створити проект (турнір). З точки зору пересічного користувача — це просто купа різних, не завжди зрозумілих, файлів, тому будьте уважні і завжди створюйте проект в окремій, порожній папці (сам турнаман цього чомусь не робить).  
Щоб створити проект потрібно:  
* натиснути ```File→New```;  
* у вікні, що з’явилося, створити нову папку із назвою турніру;  
* не злякатися повідомлення, що такого файла не існує. Підтвердити створення файлу;  
* не злякатися повідомлення про успішне створення файлу. натиснути ```ОК```;  
* спокійно відреагувати на різнокольорове вікно налаштувань. Перейти на вкладку ```Debating venues```;  
* Додати необхідну кількість кімнат (по одній на кожну четвірку команд). Дати кімнатам осмислені імена;  
* Натиснути ```OK```.
Вітаю! На цьому етапі створено порожній проект. Ще потрібно додати команди і суддів.  
Список команд зазвичай скидають у вигляді таблички:  
  
![Tournaman](/assets/2020-02-08-tournaman_0_7.png)  
  
Потрібно виділити і скопіювати назви команд та імена гравців (виділити мишкою і натиснути CTRL+C).  
Після цього в головному вікні натиснути ```Edit teams```, внизу зліва натиснути ```Import data→Import from clipboard```. У вікні, яке з’явиться, підтвердити внесення змін на диск. Якщо все зроблено правильно, то буде вікно зі списком команд.  

![Tournaman](/assets/2020-02-08-tournaman_0_8.png)  
  
На всякий випадок краще переглянути все і внести зміни, якщо необхідно. Тоді натиснути OK.  
  
Щоб додати суддів треба в головному вікні турнаману натиснути ```Edit adjudicators```. Мені список суддів зазвичай скидають десь в телеграмі, тому їх вводжу вручну. Але можна і автоматично, як з командами.  
  
![Tournaman](/assets/2020-02-08-tournaman_0_6.png)  
  
Спочатку натискаєш ```Add adjudicator```, а тоді в поле ```Name``` вводиш ідентифікатор судді (не навпаки).  
Тоді встановлюєш ранкінг судді відповідно до наданих даних. Якщо потрібно, можна встановити конфлікти на певні пари <суддя-команда>, щоб виключити можливість не об’єктивної оцінки, наприклад, найкращим друзям або найзапеклішим ворогам.  


## Власне, турнір
перенесення даних із гугл таблиць в tournaman  
формування турнірної сітки  

## Підбиття підсумків
формування фінального тебу  
визначення найкращого судді  
визначення найкращого промовця  

