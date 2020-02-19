---
title: уценка
lastChanged: 14.09.2018
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/community/docmarkdown.md
translatedFrom: de
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
hash: nHQJvm435hzSoVxk8r0edx7VWed2QP55UFCl+8JsTW4=
---
# Markdown: Синтаксис
?> Для упрощения создания и чтения документации ioBroker в качестве упрощенного языка разметки был выбран Markdown. Следующее руководство поможет вам понять синтаксис и возможности Markdown и перевести его в отличные документы.

Технически система документации поддерживает только следующие функции:

- Заголовки
- столы
- Встроенный HTML
- списки
- Ссылки
- Изображения
- жирный текст
- Курсив

<div id="overview"></div>

## Обзор
<div id="philosophy"></div>

### Философия
Markdown был разработан с основной идеей, чтобы его было как можно проще читать и писать.

Разборчивость является конечной целью здесь. Документ в формате Markdown должен иметь возможность публиковаться в своей основной форме, не будучи помеченным или отформатированным (как в случае с HTML).

Соответственно, синтаксис Markdown состоит только из символов, которые были выбраны мудро, чтобы их внешний вид соответствовал их значению.
Например, звездочки вокруг слова на самом деле выглядят как \ *ударение \* Списки в Markdown выглядят как списки. Даже цитатные блоки выглядят как цитаты, как они известны из электронных писем.

<div id="html"></div>

### Встроенный HTML
Синтаксис Markdown имеет одну цель: он используется для *записи* в сети.

Уценка не заменяет HTML, даже не анзацвайз. Сфера синтаксиса очень мала и составляет лишь небольшую часть всех тегов HTML. Markdown не намерен облегчать вставку тегов HTML. HTML уже достаточно прост. Идея Markdown - читать, писать и редактировать текст как можно проще. HTML - это *формат публикации* Markdown - это *формат записи* Поэтому его синтаксис учитывает только контент, который может быть передан в виде простого текста.

Для любого форматирования, которое невозможно с Markdown, можно использовать просто HTML. Нет необходимости отмечать HTML, чтобы отличать его от остальных. Это просто написано в тексте.

Единственным ограничением являются блочные элементы, такие как, например, `<div>`, `<table>`, `<pre>`, `<p>` и так далее. Они должны быть отделены от окружающего содержимого пустыми строками, а начальный и конечный теги не должны иметь отступов в виде пробелов или табуляции. Markdown достаточно умен, чтобы не размещать никаких дополнительных (нежелательных) тегов `<p>` вокруг блоков HTML.

Например, создайте таблицу HTML в статье Markdown:

    Это нормальный абзац.

<table><tr><td> Foo </td></tr></table>

    Это все еще нормальный абзац.

Следует отметить, что синтаксис Markdown не интерпретируется в блоках HTML. Например, нельзя использовать *выделение* внутри блоков HTML.

Встроенные теги HTML, такие как `<span>`, `<cite>` или `<del>` могут использоваться в любом месте абзаца, маркера или заголовка уценки. HTML-теги могут даже использоваться вместо соответствующего форматирования уценки. Это не проблема, чтобы использовать вместо синтаксиса Markdows для ссылок или графики просто `<a>` или `<img>`.

В отличие от блочных тегов ** синтаксис уценки интерпретируется внутри встроенных тегов.

<a id="autoescape"></a>

### Автоматическая маскировка спецсимволов
В HTML есть два символа, которые требуют особого обращения: `<` и `&`. Левая угловая скобка используется для открытия тегов HTML, амперсанда и используется для описания именованных символов (сущностей). Если эти символы должны использоваться в документах HTML как «они сами», они должны быть замаскированы как сущности, то есть, как `&lt;` и `&amp;`.

Товар и особенно непрактичен для веб-разработчиков. Если вы хотите написать о «AT & T», вы должны написать «`AT&amp;T`». Торговая и даже должна быть замаскирована в URL. В ссылке на страницу

    `http://images.google.com/images?num=30&q=larry+bird`

URL должен быть закодирован следующим образом:

    `http://images.google.com/images?num=30&amp;q=larry+bird`

Это легко забыть и, вероятно, самая популярная ошибка при проверке правильных HTML-документов.

Уценка позволяет использовать эти символы как обычно. Он управляет самим кодированием. Если продавец-и используется в объекте, он не кодируется, иначе преобразуется в `&amp;`.

Так, например, если вы хотите ввести символ авторского права, вы можете легко

    & Копировать;

напишите, и Markdown не изменит это. Но вне

    AT & T

будет уценка

    AT & амп; Т

сделать. Поскольку Markdown Inline поддерживает HTML, угловые скобки обычно рассматриваются как HTML в соответствующем случае. Только из таких вещей, как

    4 <5

будет уценка

    4 &lt; 5

сделать. В блоках кода или интервала угловые скобки и амперсанд *всегда* кодируются. Это упрощает написание через HTML в Markdown (в отличие от необработанного HTML, где обычно кодировать каждый `<` и `&`) - кошмар

* * *

<div id="block"></div>

## Блочные элементы
<a id="p"></a>

### Абзацы и разрывы строк Абзац - это просто одна или несколько строк текста, разделенных одной или несколькими пустыми строками. (Пустая строка - это любая строка, которая выглядит *как* пустая строка - строка, которая не содержит ничего, кроме пробелов и табуляций, рассматривается как пустая.) Обычные абзацы не должны иметь отступы от пробелов или табуляции
Правило «одна или несколько строк» подразумевает одно: Markdown поддерживает абзацы с «жесткими переворотами». Это сильно отличается от большинства других форматеров преобразования текста в HTML (включая параметр «Преобразование разрывов строк» для подвижного типа), которые форматируют каждый разрыв строки в абзаце как `<br />`.

Если вы *хотите* иметь в качестве разрыва `<br />`, вы можете просто завершить строку двумя или более пробелами.

Хотя это создает небольшие накладные расходы на создание `<br />`, простое правило «любая новая строка - это `<br />`» не будет работать в Markdown.

Стиль электронной почты Markdown [quotes] [bq] и [list-entry] [l] работает лучше - и выглядит лучше - при форматировании с символами новой строки.

[bq]: #blockquote

[l]:  #list

<a id="header"></a>

### Заголовки Markdown здесь поддерживает только один вид форматирования заголовков: atx.
Подобные Atx заголовки используют 1-6 символов ромба в начале строки, соответствующих уровням 1-6. Например:

    # Это H1
    ## Это H2
    ###### Это Н6
<a id="blockquote"></a>

### Цитаты
Уценка использует - как электронные письма - символ `>` для блоков цитаты.
Если у вас есть опыт работы с цитатами в письмах, вы также знаете, как создавать цитаты в Markdown. Это выглядит лучше, если вы оберните текст в строку и поместите `>` перед каждой строкой:

> Это цитата из двух пунктов. Lorem Ipsum Dolor Sit Amet,> Ecu. Aliquam hendrerit mi posuere> lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet> vitae, risus.
>> Донец сижу амет нисл. Аликвам сэмпер ипсум сит амет велит.
> Suspendisse ID Sem Conceteteer Libero Lucus Adipiscing.

Markdown также позволяет вам быть ленивым и использовать `>` только в первой строке жесткого абзаца:

> Это цитата из двух пунктов. Lorem Ipsum Dolor Sit Amet, посвященный Aditiscing Elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Донец сижу амет нисл. Аликвам сэмпер ипсум сит амет велит.
Suspendisse ID Sem Conceteteer Libero Luctus Adipiscing.

Кавычки могут быть вложенными (т. Е. Кавычки в кавычках), используя больше `>`:

> Это первый уровень цитаты.
>>> Это вложенная цитата.
>> Вернуться на первый уровень.

Кавычки могут включать другие элементы уценки, включая заголовки, списки и блоки кода:

> ## Это заголовок.
>> 1. Это первая пуля.
> 2. Это второй пункт пули.
>> Вот пример кода: >> return shell_exec ("echo $ input | $ Markdown_script");

Любой разумный текстовый редактор должен облегчить цитирование по электронной почте. Например, в BBEdit вы можете сделать выбор и выбрать пункт `Increase Quote Level` из меню `Text`.

<a id="list"></a>

### Списки
Markdown поддерживает сортированные (нумерованные) и несортированные списки.

В несортированных списках в качестве маркеров списка используются звездочки, плюс и дефисы - взаимозаменяемы:

    * Красный
    * Зеленый
    * Синий

равен:

+ Красный + зеленый + синий

а также:

    - красный
    - зеленый
    - синий

В отсортированных списках используются числа со следующей точкой:

    1-я собака
    2. Кот
    3. Мышь

Важно понимать, что сами цифры не влияют на вывод уценки. Markdown создает следующий HTML-код из последнего списка:

<ol><li> собака </li><li> кот </li><li> мышь </li></ol>

Если вы напишите список вместо:

    1-я собака
    1-й кот
    1-я мышь

Или даже:

    3-я собака
    1-й кот
    8. Мышь

Тем не менее, тот же список выходит каждый раз. При желании можно правильно нумеровать его списки вручную. Но если вы хотите быть ленивым, вы можете уверенно использовать тот же номер.

Однако вам также следует начать список с номера 1. В будущем Markdown может захотеть установить начальную цифру для первой записи списка.

Записи списка обычно начинаются с левого края документа, но они могут иметь отступ до трех пробелов вправо.
Маркеры списка должны быть отделены одним или несколькими пробелами или табуляцией от следующего текста.

Для правильного форматирования списков отдельные записи могут быть дополнительно с отступом, как здесь:

    Lorem Ipsum Dolor Sit Amet, посвященный Aditiscing Elit.

Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

    * Донец сит амет нисл. Аликвам сэмпер ипсум сит амет велит.

        Suspendisse ID Sem Conceteteer Libero Luctus Adipiscing.

Следующий пример генерирует тот же код, но менее аккуратный:

    Lorem Ipsum Dolor Sit Amet, посвященный Aditiscing Elit.

Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

    * Донец сит амет нисл. Аликвам сэмпер ипсум сит амет велит.

    Suspendisse ID Sem Conceteteer Libero Luctus Adipiscing.

Если записи списка разделены пустыми строками, Markdown обернет записи списка с `<p>` и `</p>`.

Например, это будет:

    * Warsteiner
    * Король

в

<ul><li> Warsteiner </li><li> король </li></ul>

Но это:

    * Warsteiner

    * Король

становится слишком

<ul><li><p> Warsteiner </p></li><li><p> король </p></li></ul>

Элементы списка могут состоять из нескольких абзацев. Каждый следующий абзац в маркере должен содержать по крайней мере 4 пробела или табуляцию:

    1. Это пункт с двумя абзацами. Lorem Ipsum Dolor

сиди амет, послушай, элитируй. Aliquam hendrerit mi posuere lectus.

Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus. Донец сит амет нисл. Аликвам сэмпер ипсум сит амет велит.

    2. Suspendisse id sem consctetuer libero luctus adipiscing.

Это выглядит хорошо, если каждая строка следующего абзаца имеет отступ, но опять же Markdown позволяет ленивому отступать только в первую строку:

    * Это пункт с двумя абзацами

Это второй абзац в этом пункте списка. Только первая строка должна быть с отступом. Lorem Ipsum Dolor Sit Amet, посвященный Aditiscing Elit.

    * Еще один пункт в том же списке.

Чтобы использовать цитату в маркере, цитата должна иметь отступ:

    * Пуля с цитатой:

> Это цитата> В списке.

Чтобы использовать блок кода в маркере, он должен иметь отступ *дважды* - 8 пробелов или две вкладки:

    * Элемент списка с примером кода:

            <введите код здесь>

Возможно непреднамеренное создание списков, например,
следующее пишет:

    1986. Какой замечательный год.

Другими словами, последовательность *число-точка-пространство* в начале строки. Чтобы избежать этой проблемы, точка может быть замаскирована обратной косой чертой:

    1986 \. Какой замечательный год.

<h3 id="precode"> блоки кода </h3>

Предварительно отформатированные кодовые блоки используются для перезаписи исходного кода программы или разметки. Вместо формирования нормальных абзацев строки в блоке кода интерпретируются как найденные. Уценка включает в себя кодовые блоки с тегами `<pre>` и `<code>`.

Чтобы создать блок кода в Markdown, просто сделайте отступ в каждой строке блока как минимум с 4 рычагами или вкладкой. Со следующего входа ...

    Это нормальный абзац.

        Это блок кода.

... делает Markdown следующее:

<p> Это нормальный абзац. </p>

<pre><code>Dies ist ein Code-Block.
</code></pre>

Уровень отступа - 4 пробела или 1 табуляция - удаляются из каждой строки отступа. Следующее, например ...

    Пример в AppleScript:

сказать приложение "Foo" звуковой сигнал конец сказать

... становится слишком

<p> Пример в AppleScript: </p>

<pre><code>tell application "Foo" beep end tell </code></pre>

Блок кода заканчивается в первой строке, которая не имеет отступа (или в конце документа).

В блоке кода амперсанд (`&`) и угловые скобки (`<` и `>`) автоматически преобразуются в объекты HTML. Это значительно облегчает включение фрагментов HTML - просто скопируйте HTML в документ, сделайте отступ, а Markdown выполняет кодирование амперсанда и угловых скобок. Например:

<div class="footer"> © 2004 Foo Corporation </div>

будет выглядеть так:

<pre><code>&lt;div class="footer"&gt; &amp;copy; 2004 Foo Corporation &lt;/div&gt; </code></pre>

Обычный синтаксис уценки не обрабатывается в блоках кода. что
Звездочки - это просто звёздочки в блоке кода, а не сигнал для выделения текста. Следствием этого является то, что о Markdown легко говорить в Markdown *.

<a id="hr"></a>

### Горизонтальные линии Тег для горизонтальных линий (`<hr />`) можно сгенерировать, написав 3 или более дефиса или звездочки только в одной строке. Пробелы между символами также допускаются. Все следующие примеры будут генерировать горизонтальную линию:
    * * *

    ***

    *****

    - - -

    ---------------------------------------

* * *

<div id="span"></div>

## Span elements
<a id="link"></a>

### Ссылки
Markdown поддерживает два типа ссылок: *Inline* и *References*

В обоих стилях текст ссылки помечается [квадратными скобками].

Чтобы создать встроенную ссылку, напишите нормальные скобки сразу за закрывающей квадратной скобкой. В этих скобках URL-адрес написан так, чтобы быть связанным вместе с *необязательным* заголовком для ссылки в кавычках. Примеры:

Это [пример](http://example.com/ "Der Linktitel") для встроенной ссылки.

    [Эта ссылка](http://example.net/) не имеет атрибута заголовка.

Это становится:

<p> Это <a href="http://example.com/" title="название">пример</a> встроенной ссылки. </p>

<p> <a href="http://example.net/">Эта ссылка</a> не имеет атрибута заголовка. </p>

Если вы хотите сослаться на контент на том же сервере, вы можете использовать относительные пути:

    Дополнительную информацию можно найти на странице [Обо мне](/about/).

В ссылочных ссылках используется второй набор квадратных скобок, в котором записан произвольный идентификатор для ссылки:

    Это [пример] [id] для ссылки.

Вы также можете вставить пробел между скобками, как вы хотите:

    Это [пример] [id] для ссылки.

Затем где-то в документе ссылка определяется в отдельной строке следующим образом:

[id]: http://example.com/  "Optionalen Titel hier eintragen"

так:

* Квадратные скобки, содержащие идентификатор ссылки (опционально с

    с отступом до трех пробелов);

* сопровождается двоеточием;
* с последующим одним или несколькими пробелами (или символами табуляции);
* сопровождается URL для ссылки;
* необязательно сопровождается текстом для атрибута заголовка ссылки,

    в скобках, одинарные или двойные кавычки.

Следующие три определения идентичны:

[foo]: http://example.com/  "Optionaler Titel"

[foo]: http://example.com/  'Optionaler Titel'

[foo]: http://example.com/  (Optionaler Titel)

** Примечание: ** В Markdown 1.0.1 существует известная ошибка, которая затрудняет функцию одинарных кавычек в качестве разделителя для заголовков ссылок.

URL-адрес ссылки может быть заключен в угловые скобки:

[id]: <http://example.com/>  "Optionaler Titel hier"

Атрибут title также может быть установлен на следующую строку и иметь отступ с большим количеством пробелов или табуляций. Это выглядит лучше с длинными URL:

[id]: http://example.com/langer/pfad/zu/seite

        «Необязательный заголовок здесь»

Определения ссылок используются только для создания ссылок, пока Markdown обрабатывает документ и удаляется из документа до вывода HTML.

Идентификаторы для определений ссылок могут состоять из букв, цифр, пробелов и знаков препинания. Они не зависят от прописных и строчных букв:

[Текст ссылки] [a] [текст ссылки] [A]

Два определения ссылок эквивалентны.

* Подразумеваемый идентификатор ссылки * позволяет вам опустить идентификатор ссылки. В этом случае в качестве идентификатора используется текст ссылки. Пустой набор квадратных скобок просто добавляется к тексту ссылки:

[Google] []

Тогда ссылка определяется:

[Google]: http://google.com/

Поскольку идентификаторы ссылок могут содержать пробелы, эта аббревиатура работает даже для нескольких слов в тексте ссылки:

Посетите [Daring Fireball] [] для получения дополнительной информации.

Тогда ссылка определяется:

[Daring Fireball]: http://daringfireball.net/

Определения ссылок могут быть сделаны в любом месте документа Markdown. Вообще, это хорошая идея сделать их в соответствии с параграфом, в котором они используются. Но они также могут быть перечислены как сноски вместе в конце документа.

Небольшой пример:

Я получаю в 10 раз больше трафика от [Google] [1], чем от [Yahoo] [2] или [MSN] [3].

[1]: http://google.com/        "Google"

[2]: http://search.yahoo.com/  "Yahoo Search"

[3]: http://search.msn.com/    "MSN Search"

Сокращение идентификатора подразумеваемой ссылки также можно использовать для записи:

Я получаю в 10 раз больше трафика от [Google] [], чем от [Yahoo] [] или [MSN] [].

[google]: http://google.com/       "Google"

[yahoo]: http://search.yahoo.com/  "Yahoo Search"

[msn]: http://search.msn.com/      "MSN Search"

Оба примера приведут к следующему HTML-коду:

<p> Я получаю в десять раз больше трафика от <a href="http://google.com/" title="Google">Google,</a> чем от <a href="http://search.yahoo.com/" title="Поиск Yahoo">Yahoo</a> или <a href="http://search.msn.com/" title="MSN Поиск">MSN</a> . </p>

Для сравнения, тот же абзац следует с использованием встроенных ссылок Markdown:

Я получаю в 10 раз больше трафика из [Google](http://google.com/ "Google"), чем из [Yahoo](http://search.yahoo.com/ "Yahoo Search") или [MSN](http://search.msn.com/ "MSN Search").

Идея ссылочных ссылок не в том, что их легче написать. Идея в том, что они делают документы намного более читабельными. Пример абзаца имеет длину всего 80 символов со ссылочными ссылками, а ссылочные ссылки - всего 181 символ; как HTML, это 239 символов, больше разметки, чем содержания.

Благодаря ссылочным ссылкам Markdown исходный документ больше похож на окончательный формат вывода, как показано в браузере. Возможность извлекать метаданные для разметки из абзаца позволяет интегрировать ссылки в текст без замедления потока текста.

<a id="em"></a>

### Подчеркивание В Markdown звездочки (`*`) и подчеркивания (`_`) рассматриваются как индикаторы акцента. Текст, упакованный в отдельные `*` или `_`, заключен в HTML-тэг `<em>`, дубликаты `*` или `_` помечены тегом `<strong>` , Следующий текст, например:
    *Одиночные звезды*

    _Один подчеркивания_

    ** двойные звезды **

    __Двойные подчеркивания__

Потратит:

<em>Одиночные звезды</em>

<em>Индивидуальные подчеркивания</em>

<strong>Двойные звездочки</strong>

<strong>Двойное подчеркивание</strong>

Стиль можно выбрать произвольно. Единственное ограничение заключается в том, что один и тот же символ должен использоваться для открытия и закрытия области выделения.

Акцент может быть использован в середине слова:

  Г-н *Бог* причастие

Но когда `*` или `_` окружены пробелами, он рассматривается как простая звездочка или простое подчеркивание.

Чтобы написать звёздочку или подчеркивание в точке, где это будет восприниматься как акцент, его можно замаскировать обратной косой чертой:

  \ *Этот текст окружен звездочками \*

<a id="code"></a>

### Код Чтобы пометить область кода, она заключена в символы обратной черты (`` ```). В отличие от блока кода, область кода форматирует код в обычном абзаце:
    Используйте функцию `printf()` для вывода текста.

становится:

<p> Используйте функцию <code>printf()</code> для <code>printf()</code> текста. </p>

Если в области кода должен отображаться обратный тик, то можно использовать несколько обратных тики до и после области кода:

    ``Irgendwo hier (`) является скрытым обратным трюком```

Это становится:

<p><code>irgendwo hier (`) ist ein Backtick versteckt.</code></p>

Разделители обратного тика вокруг диапазона кода могут содержать пробелы - один после открывающего, один перед закрывающим обратным трением. Это позволяет использовать обратные метки в области кода также в начале или в конце:

Один тик в области кода: `` ```

Строка, заключенная в обратную косую черту в области кода: `` `foo` ``

будет выглядеть так:

<p> Один тик в области кода: <code>`</code> </p>

<p> Заключенная в <code>`foo`</code> строка в кодовой области: <code>§§SSSSS_0§§</code> </p>

В областях кода рекламные и угловые скобки кодируются как HTML Entitiy.

    Никто не использует теги `<blink>`.

Это становится:

<p> Никто не использует теги <code>&lt;blink&gt;</code> . </p>

Также работает так:

    `&#8212;` является десятичным кодированным эквивалентом `&mdash;`.

Это произойдет

<p> <code>&amp;#8212;</code> является десятичным кодированным эквивалентом <code>&amp;mdash;</code> , </p>

<a id="img"></a>

Следует признать, что довольно сложно найти «естественный» синтаксис для встраивания графики в текст.
В Markdown используется синтаксис, похожий на стиль ссылок. Это позволяет использовать два типа: встроенный и справочный.

Встроенный синтаксис выглядит следующим образом:

    ![Альтернативный текст](../../de/community/pfad/zum/bild.jpg)

    ![Альтернативный текст](../../de/community/pfad/zum/bild.jpg "Дополнительный заголовок")

так:

* Восклицательный знак: `!`;
* сопровождается набором квадратных скобок, показывающих значение

    `alt` Атрибуты для включенной графики;

* с последующими круглыми скобками, указывающими URL или путь к графике

и значение необязательного атрибута `title`, заключенное в кавычки.

Ссылки на изображения в стиле ссылок выглядят так:

    ! [Альтернативный текст] [идентификатор]

«id» - это имя определенной ссылки на изображение здесь. Ссылки на изображения определяются с тем же синтаксисом, что и ссылки:

[id]: url/zur/grafik  "Optionales title-Attribut"

В настоящее время у Markdown нет синтаксиса для указания размера графики. Если это необходимо, можно использовать обычный тег HTML `<img>`.

* * *

<div id="misc"></div>

## Разное
<a id="backslash"></a>

### Маскировка с обратной косой чертой
Markdown позволяет использовать маскирование обратной косой черты для написания символов, которые иначе имеют значение в синтаксисе Markdown.
Например, если вы хотите заключить слово в звездочки (вместо HTML-тега `<em>`), вы можете поставить обратную косую черту перед звездочками:

  \ *В окружении звездочек \*

Уценка предоставляет эту возможность для следующих символов:

Обратная косая черта

    * Звездочка

_ Подчеркивание {} фигурные скобки [] квадратные скобки () круглые скобки

# Ромб + знак плюс
    - знак минус (дефис)

, Точка! восклицательный знак

* * *

<a id="lizenz"></a>

### Лицензия
Это произведение лицензировано по международной лицензии Creative Commons Attribution-ShareAlike (BY-SA) 4.0] [by-sa].

[by-sa]: http://creativecommons.org/licenses/by-sa/4.0/deed.de

?> Это перевод [оригинальной синтаксической документации] [osd] [John Grubers] [jg] [Markdown] [md]. Данный перевод относится к состоянию на 15.12.2013 (Markdown Version 1.0.1). Гарантия правильности перевода не предоставляется. Если в переводе есть ошибки, отправьте короткое сообщение на <lasar@liepins.net>.
Любые другие отзывы также приветствуются. *

[jg]: http://daringfireball.net/

[md]: http://daringfireball.net/projects/markdown/

[osd]: http://daringfireball.net/projects/markdown/syntax