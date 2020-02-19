---
title: добро пожаловать
lastChanged: 29.03.2019
translatedFrom: de
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/README.md
hash: klNmY+JqLgd9SlD/x+ZDGAOFs8yiJDfoeM1r0KCV9aY=
---
# Добро пожаловать в ioBroker
!> **Примечание для начинающих** Если слишком много неизвестных терминов было использовано для чтения этих первых слов, они будут подробно объяснены снова в [следующая страница](./basics/README.md).

ioBroker - это программное решение для интеграции различных систем SmartHome, которые остались бы без островных решений ioBroker в общую систему.

Таким образом, ioBroker является платформой интеграции для Интернета вещей.

Система ioBroker имеет модульную структуру. Разнообразные ***адаптеры*** позволяют общаться с более чем 200 различными платформами от A, например, от Alexa до Z, например, отслеживание времени.

Будь то интеграция коммерческих продуктов практически из всех областей жизни или интеграция самостоятельно созданного решения - ioBroker делает практически все возможное.

!> Документация находится в стадии разработки и постоянно расширяется. Поэтому может случиться, что ссылки еще не работают или контент отсутствует. Мы благодарны за любую помощь в создании новых статей или для улучшений. Информация об этом может быть найдена в [на форуме](https://forum.iobroker.net). <br><br> **До тех пор, пока все содержимое не будет передано, старая документация все еще остается [найти здесь](https://www.iobroker.net/docu/). Он будет последовательно заменен новой документацией.**

## Кроссплатформенный
Любой, кто знаком с домашней автоматизацией, рано или поздно обнаружит, что системы часто несовершенны. У каждой системы есть свои сильные и слабые стороны. Поэтому ioBroker является кроссплатформенным. Параллельная работа с существующими решениями возможна в любое время. Синергетические эффекты могут быть использованы и объединены лучшие из всех миров.

Сам ioBroker дома почти на всех платформах. ioBroker может быть установлен под Windows, Linux, OSX или как Dockerimage.
Предварительно сконфигурированные установочные образы удаляют работу по установке от пользователя.

Дополнительный облачный доступ позволяет пользователю или системным интеграторам удаленно управлять локально установленной системой ioBroker 24/7. Контроль доступа может быть свободно настроен пользователями и группами пользователей.

## Масштабируемый
Если со временем будут подключены дополнительные системы Smarthome, они могут быть реализованы пользователем в любое время через дополнительные адаптеры во время работы. ioBroker также является масштабируемым.
Несколько серверов ioBroker могут быть подключены к системе `Mutihost`.
Можно даже совместить платформы операционной системы и соединение одноплатных компьютеров SoC с большими многоядерными серверами.
Для систем с самыми высокими требованиями к производительности может быть интегрирован дополнительный Redis, особенно быстрая база данных.

## Программируемый
Необязательное программирование выполняется с помощью JavaScript, языка сценариев, который постоянно разрабатывается с 1995 года. Это легко понять, так что новые требования могут быть быстро реализованы. Это позволяет каждому внести свой вклад в ioBroker, а также реализовать индивидуальные требования.

Для новичков в программировании доступен вариант «Блочный», который позволяет «без перетаскивания» без обширных знаний в области программирования быстро получать результаты.

## Визуализация
С `VIS` ioBroker предоставляет мощный инструмент для создания индивидуальной визуализации. Текущие значения датчиков могут отображаться графически, а также исторические градиенты. Живые изображения с камер видеонаблюдения, реализация системы охранной сигнализации, систем отопления и кондиционирования воздуха - практически все, что можно вообразить, также может быть реализовано.

![VIS](../de/media/vis2.png) *Пример самостоятельно созданного пользовательского интерфейса VIS*

Пользователь имеет максимальную свободу дизайна. Сборные строительные блоки для удобства использования помогают пользователю. Но возможно не только отображение информации. Управление устройствами также быстро осуществляется через интерфейс визуализации. Работа интерфейса может быть адаптирована для самых разных устройств - от смартфона через настенный планшет с сенсорной функцией до персонального компьютера - все можно реализовать простым перетаскиванием мышью.

Простые готовые пользовательские интерфейсы могут быть быстро реализованы с помощью адаптера материала или адаптера HabPanel.

## Сообщество
С 2014 года ioBroker широко поддерживается тысячами пользователей и разработчиков благодаря многочисленным преимуществам. В специально созданных [форум](https://forum.iobroker.net) пользователи и разработчики встречаются и обмениваются своим опытом и предложениями. Поскольку ioBroker является программным обеспечением с открытым исходным кодом, все исходные тексты свободно доступны на платформе [GitHub](https://github.com/ioBroker).

?> Чем ioBroker не является: ioBroker не является коммерческим программным обеспечением. ioBroker разработан и поддерживается добровольцами. Таким образом, использование программного обеспечения осуществляется под личную ответственность, за исключением случаев умышленного повреждения.
Нет контрактной поддержки.

[im Forum]: https://forum.iobroker.net/viewtopic.php?f=8&t=16933