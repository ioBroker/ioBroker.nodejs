---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.device-reminder/README.md
title: ioBroker.device-напоминание
hash: dJkkVjbUSb8+xqm1CW8yhmrkkEJm7K6WiNM36a0jNUo=
---
![Логотип](../../../en/adapterref/iobroker.device-reminder/admin/icon.png)

![Количество установок (стабильно)](http://iobroker.live/badges/device-reminder-stable.svg)
![Количество установок (последнее)](http://iobroker.live/badges/device-reminder-installed.svg)
![Версия NPM](http://img.shields.io/npm/v/iobroker.device-reminder.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.device-reminder.svg)
![Статус зависимости](https://img.shields.io/david/xenon-s/iobroker.device-reminder.svg)
![Лицензия](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)
![Пожертвование Paypal](https://img.shields.io/badge/paypal-donate%20%7C%20spenden-blue.svg)
![NPM](https://nodei.co/npm/iobroker.device-reminder.png?downloads=true)

# IoBroker.device-напоминание
![Тестирование и выпуск](https://github.com/xenon-s/iobroker.device-reminder/workflows/Test%20and%20Release/badge.svg)

## Нужен немецкий ридми?<br> [немецкий ридми](https://github.com/Xenon-s/ioBroker.device-reminder/blob/master/README_GER.md)
<br>

# Адаптер для мониторинга состояния устройств Версия 1.x
Этот адаптер может использовать измерительные гнезда, чтобы определять, включено ли устройство, работает или было выключено, и реагировать на это. Затем сообщения могут быть отправлены автоматически через Telegram, whatsapp, alexa, sayit, pushover и электронную почту (возможен множественный выбор для каждого устройства). Также возможно автоматическое отключение розетки после завершения процесса (также с задержкой по времени).

# Что следует учитывать?
Интервал обновления от «значения потребления в реальном времени (называется **&quot; _ энергия &quot;**)» для большинства устройств не должен превышать 10 секунд, в противном случае сообщения могут появляться с большой задержкой.<br> Команда в консоли Tasmota: TelePeriod 10<br> **Запись:**

- Значения ниже 1 ватта считаются 0 ватт и автоматически означают «** выключено **».
- Значения выше 1 ватта указывают на то, что устройство находится в режиме «** ожидания **».

# Что возможно на единицу?
- Уведомление при запуске агрегата
- Уведомление об окончании работы соответствующего устройства
- Уведомление в Telegram (возможно несколько идентификаторов)
- Уведомление Alexa (возможно несколько идентификаторов)
- Уведомление WhatsApp (возможно несколько идентификаторов)
- Уведомление о пустом месте (возможно несколько идентификаторов)
- Уведомление по электронной почте (возможно несколько идентификаторов)
- Уведомления могут быть созданы бесплатно или также указаны внешним скриптом
- Точки данных с текущим статусом, живым потреблением и последним отправленным статусным сообщением, чтобы иметь возможность использовать значения из этого адаптера в других скриптах
- При необходимости агрегаты можно выключить (в том числе с задержкой по времени), когда процесс будет признан завершенным.
- Голосовые помощники можно временно отключить через точку данных

# Инструкция
## Основные вещи заранее
Для каждой группы устройств, алекса и т. Д. Есть кнопка «Проверить ввод». Если щелкнуть эту кнопку, существующие входные данные будут проверены на достоверность, и вы сразу же получите ответ, все ли введенные правильно. Если были внесены изменения, эту кнопку необходимо нажать!

## Создать устройство
![addDevice.png](../../../en/adapterref/iobroker.device-reminder/admin/addDevice.png)

- **имя устройства** произвольно выбираемое имя
- **тип устройства** здесь вы должны выбрать, какое это устройство, чтобы вычисления в адаптере могли быть выполнены правильно.
- **потребление / энергия** нажмите кнопку с тремя белыми точками, чтобы открыть управление объектами. Необходимо выбрать точку данных, которая отображает **текущее живое потребление**
- ** включить / выключить **: нажатие на кнопку с тремя белыми точками открывает управление вашим объектом. Точка данных, которая включает / выключает ** ваше гнездо, должна быть выбрана (не обязательно).
- **Начальный текст** уведомление будет отправлено при запуске устройства (также возможны специальные символы)
- **Конечный текст** уведомление будет отправлено, когда устройство завершит свою работу (также можно использовать специальные символы)

С помощью **Начальный текст** и **Конечный текст** вы также можете получить сообщение из внешней точки данных. Это сообщение считывается из точки данных с задержкой в 1 секунду после изменения состояния устройства. Таким образом, вы можете создать сообщение с помощью внешнего сценария. Адаптер автоматически распознает, исходит ли сообщение из точки данных или оно было просто введено вручную. Чтобы выбрать точку данных, просто нажмите кнопку с тремя белыми точками, а затем выберите соответствующую точку данных. **Обратите внимание** можно использовать только точку данных **или** введенное вручную сообщение!<br><br>

## Создать Alexa
![addAlexa.png](../../../en/adapterref/iobroker.device-reminder/admin/addAlexa.png)

- **alexa name** произвольно выбираемое имя, также возможны специальные символы.
- **alexa "объявление" / "говорить"** здесь необходимо выбрать точку данных, которая позволяет вашей Alexa говорить. Чтобы выбрать точку данных, просто нажмите кнопку с тремя маленькими белыми точками.
- Volume 0-100 **: громкость, с которой ваш Alexa должен говорить (от 0 до 100%).

Последние 4 поля можно использовать для создания периода времени, в течение которого вашему Alexa разрешено говорить. По умолчанию активен период с 00:00 до 23:59.

- **«активен с часа»** время начала в часах
- активен с минут Время начала в минутах
- **«неактивен с часа»** время окончания в часах
- **«неактивен с минут»** время окончания в минутах

<br> <br>

## Создание устройства SayIt
![addSayit.png](../../../en/adapterref/iobroker.device-reminder/admin/addSayit.png)

- **sayit name** произвольно выбираемое имя, также возможны специальные символы.
- **sayit path "../ text"** выберите точку данных "text" в соответствующей папке sayIt устройства. Вывод текста отправляется сюда.
- **volume 0-100** громкость, с которой ваше устройство sayIt должно говорить (от 0 до 100%).
- **«активен с часа»** время начала в часах
- **«активен с минут»** время начала в минутах.
- **«неактивен с часа»** время окончания в часах
- **«неактивен с минут»** время окончания в минутах

<br> <br>

## Создать пользователя WhatsApp
![addWhatsapp.png](../../../en/adapterref/iobroker.device-reminder/admin/addWhatsapp.png)

- **WhatsApp name** произвольно выбираемое имя, также возможны специальные символы.
- **WhatsApp path «sendMessage»** выберите точку данных «sendMessage» в соответствующей папке WhatsApp. Вывод текста отправляется сюда.

## Создать пустого пользователя
![addPushover.png](../../../en/adapterref/iobroker.device-reminder/admin/addPushover.png)

- **имя** произвольно выбираемое имя, также возможны специальные символы.
- ** pushover instance "**: экземпляр для отправки
- **приоритет** приоритет, с которым должно быть отправлено сообщение.
- **звук** звук, который воспроизводится, когда Pushover получает сообщение.

## Создать пользователя электронной почты
![addEmail.png](../../../en/adapterref/iobroker.device-reminder/admin/addEmail.png)

- **имя** произвольно выбираемое имя, также возможны специальные символы.
- **адрес отправителя** адрес электронной почты, с которого отправляется электронное письмо.
- **адрес получателя** адрес электронной почты, на который будет отправлено сообщение.

# Устройства по умолчанию
![default-devices.png](../../../en/adapterref/iobroker.device-reminder/admin/default-devices.png) Эти значения были определены в течение нескольких месяцев с помощью многочисленных тестеров. Изменение значений может привести к тому, что устройства больше не будут правильно записываться, что приведет к ложным отчетам.

# Custom-устройства
![custom-devices.png](../../../en/adapterref/iobroker.device-reminder/admin/custom-devices.png) Эти значения могут быть изменены пользователем и затем использованы. Вот объяснение:

- **начальное значение** начальное значение в ваттах, которое должно быть превышено, чтобы устройство было распознано как запущенное.
- конечное значение **: конечное значение в ваттах, которое должно быть занижено, чтобы устройство было признано готовым.
- Число значений «start» **: указывает, как часто «начальное значение» должно быть превышено ** подряд **. Падение ниже его одного раза приведет к прерыванию запуска. Среднее значение этих значений должно быть выше начального значения, чтобы устройство было признано запущенным.

* Пример: значение должно быть 10 Вт и должно быть превышено 3 раза подряд. 1. 15 Вт, 2. 1 Вт, 15 Вт => Фаза запуска была прервана, потому что второе значение было ниже 10.

- Число значений «конец»: указывает, сколько значений должно быть записано перед вычислением того, закончен ли блок. Чем меньше здесь значений, тем менее точен результат и возрастает риск ложных отчетов. Чем выше значение, тем точнее запись. Однако недостатком является то, что готовое сообщение отправляется с большой задержкой. Конец распознается только тогда, когда "количество значений заканчивается" и среднее потребление ниже "конечного значения".

* Краткий пример расчета Значения потребления поступают каждые 10 секунд. **конечное значение** установлено на 50, **значения end** на 100. После того, как устройство было распознано как запущенное, записываются 100 значений (* длительность 100 значений x 10 секунд = 1000 секунд *), и только после этого рассчитано среднее значение. Если это значение меньше 50, **готово** распознается прибл. 16,5 минут (мы запоминаем **конец значений** = 100 значений) и сообщение (если настроено) гаснет. Если значение больше 50, ничего не происходит, потому что блок все еще работает. Каждое дополнительное значение теперь заменяет самое старое, и новое среднее значение рассчитывается после каждого нового значения.<br>

# Настроить устройства
![configureDevices.png](../../../en/adapterref/iobroker.device-reminder/admin/configureDevices.png)

![refresh-table.png](../../../en/adapterref/iobroker.device-reminder/admin/refresh-table.png)<br> Если кнопка «обновить» синего цвета, нажмите на нее. Будут отображаться только те устройства, для которых не было обнаружено ошибок.

- **активный** активирован по умолчанию. Здесь вы можете временно отключить устройство, чтобы оно больше не отправляло уведомления.
- **устройство** создается автоматически
- **Alexa** все ранее созданные Alexas перечислены здесь и могут быть добавлены щелчком
- **sayit** здесь перечислены все ранее созданные устройства Sayit, и их можно добавить, щелкнув по ним.
- **WhatsApp** здесь перечислены все ранее созданные пользователи WhatsApp, и их можно добавить, нажав на них
- **pushover** здесь перечислены все ранее созданные пользователи pushover, и их можно добавить, щелкнув по ним.
- **электронная почта** все ранее созданные пользователи электронной почты будут перечислены здесь и могут быть добавлены щелчком
- Telegram **: здесь перечислены все доступные пользователи Telegram, которые можно назначить устройству, щелкнув по ним. Соответствующий экземпляр указан в [квадратных] скобках.

** Если имена не отображаются: ** Проверьте, содержит ли запись в "telegram.X.communicate.users" (X означает соответствующий экземпляр, например, 0) следующую структуру: "{" ID IN NUMBERS ": { "firstName": "User1"}} ", если нет, это можно просто изменить. Адаптер ищет как ** firstName **, так и ** userName **. Затем вы можете решить, на какое имя отправлять. Можно выбрать только ** firstName ** или ** userName **!

- **выключить** если выбрано, розетка автоматически отключается после завершения процесса.
- **выключить через минуты** здесь можно указать время ожидания в **минутах** По истечении тайм-аута розетка отключается *, если активировано автоматическое отключение *. Однако тайм-аут не влияет на уведомление об окончании работы устройства!
- Обнаружение прерывания **: если этот параметр активирован, адаптер пытается определить, было ли устройство уже выключено вручную перед уведомлением, а затем больше не уведомляет.

После нажатия на «** Сохранить и закрыть **» в разделе *Объекты -> устройство-напоминание* создается папка для каждого вновь созданного устройства, на котором

- текущее время выполнения в чч: мм: сс
- текущее время выполнения в миллисекундах
- текущее состояние устройства
- текущее живое потребление (берется из *потребления пути / энергии* и
- сообщение в мессенджер
- среднее потребление (может использоваться как помощь для определения ваших собственных пороговых значений)
- не беспокоить (если активирован, через **голосовой помощник** сообщения не отправляются)

отображается.<br>

# Служба поддержки
** Если вам нравятся мои работы: **<br>

[![PayPal] (https://www.paypalobjects.com/en_US/DK/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=3EYML5A4EMJCW&source=url)<br><br>

## Changelog
<!--
	Placeholder for the next version (at the beginning of the line):
    ### __WORK IN PROGRESS__
-->

### 1.0.5 (2021-01-16)
* (xenon-s) bugfix: no messages were sent

### 1.0.4 (2021-01-12)
* (xenon-s) bugfix pushover
* (xenon-s) bugfix message: there may now be a "." at the end of the messages

### 1.0.3 (2021-01-07)
* (xenon-s) bugfix pushover
* (xenon-s) added link "german readme" in readme

### 1.0.2 (2021-01-06)
* (xenon-s) fix name in io-package.json

### 1.0.1 (2021-01-05)
* (xenon-s) bugfix

### 1.0.0 (2021-01-05)
* (xenon-s) initial commit version 1.0

### 0.7.4 (2020-12-20)
* (xenon-s) bugfix: telegram instance was not recognised correctly
* (xenon-s) bugfix: abort detection prevented sending of notifications

### 0.7.1 (2020-12-17)
* (xenon-s) fix telegram bug
* (xenon-s) Deleted incorrect version numbers in the io package

### 0.7.0 (2020-12-10)
* (xenon-s) Data is now queried cyclically

### 0.6.2 (2020-12-04)
* (xenon-s) bugfix index_m

### 0.6.0 (2020-12-03)
* (xenon-s) bugfix: alexa speak-volume when input is empty
* (xenon-s) bugfix: telegram now shows both names, otherwise there were errors in the notifications 
* (xenon-s) add: Device status can now be configured yourself

### 0.5.4 (2020-11-28)
* (xenon-s) calculation optimised, custom / default values may have to be adjusted if they have been changed by the user

### 0.5.0 (2020-11-22)
* (xenon-s) bugfix: volume sayit
* (xenon-s) add: volume alexa
* (xenon-s) DP runtime in milliseconds

### 0.4.10 (2020-11-17)
* (xenon-s) bugfix main.js

### 0.4.0 (2020-11-11)
* (xenon-s) config page revised to simplify the input of devices
* (xenon-s) inserted a break, so that it is recognized, if a device is switched off prematurely at the device switch
* (xenon-s) bugfix: telegram users are not always recognized correctly and displayed incorrectly
* (xenon-s) adjustable values inserted at "Type
* (xenon-s) readme extended and adapted

### 0.3.0 (2020-11-07)
* (xenon-s) standby detection, even if the power outlet should not be switched off
* (xenon-s) It is now possible to get messages from an external data point and send them as start / end message
* (xenon-s) device "microwave" added

### 0.2.1 (2020-11-05)
* (xenon-s) readme adapted

### 0.2.0 (2020-11-05)
* (xenon-s) update to version 0.2: index_m completely revised and whatsapp added

### 0.1.0 (2020-10-23)
* (xenon-s) beta release

### 0.0.1 (2020-10-20)
* (xenon-s) initial commit

## License

MIT License

Copyright (c) 2020 xenon-s

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.