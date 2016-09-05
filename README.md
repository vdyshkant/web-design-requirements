### **Requirements & Guidelines for PSD templates** //Ultimate alpha ver.



#### 1. Цветовой профиль

Проблема с цветовыми профилями чаще всего возникает из-за отсутствия понимания у дизайнера, что же такое цветовой профиль и как его выбирать. Наиболее часто встречаются профили Adobe RGB (1998) и sRGB IEC61966-2.1 (далее просто sRGB), о которых можно почитать, например, здесь.

Для веба, как правило, используется профиль sRGB — он является профилем по умолчанию, например, в ОС Windows. Это значит, что мы видим изображение на экране в цветах, определенных стандартом sRGB IEC61966-2.1. Разница между Adode RGB и sRGB заключается в ширине цветового спектра.

В чем же проблема? Дизайнер, создавая в Photoshop новый проект, не указывает цветовой профиль, и, как следствие, Photoshop оставляет значение по умолчанию — Adode RGB. В свою очередь, верстальщик, получив макет, нарезает его, и в какой-то момент замечает, что цвета в макете и на свёрстанной странице отличаются на несколько тонов.

![Minion](http://storage1.static.itmages.com/i/16/0905/h_1473046659_3502541_33af51bad6.png)

Что же произошло? Еще на стадии сохранения нарезанных изображений, верстальщик воспользовался замечательной функцией Save for Web & Devices, которая по умолчанию выполняет преобразование изображения в sRGB. В итоге мы видим одни цвета в рабочем пространстве Photoshop и совсем другие на готовом сайте.

Для одного заказчика небольшая разница в цвете фона на сайте может быть некритична, а для другого — это повод для скандала. Думаю, найдутся люди, которым приходилось полностью переделывать дизайн или вёрстку из-за такого упущения, как забытый цветовой профиль.

Решение проблемы — всегда при начале работы убеждаться, что установлен правильный профиль.

![Minion]()

![Minion]()

#### 2. Направляющие

Установка направляющих — казалось бы, простое дело. Но и тут возникают проблемы. Невнимательный верстальщик, используя установленные дизайнером направляющие, нарезает изображения и получает на выходе что-то подобное:

![Minion](https://habrastorage.org/getpro/habr/post_images/090/76c/617/09076c61777419f77bc2477eb63ba8e7.jpg)

Почему так получилось? При близком рассмотрении видно, что направляющие сами не привязываются к границам пикселей, соответственно, когда дизайнер «на глаз» ставит направляющую, то, скорее всего, она не попадёт ровно между пикселями

![Minion](https://habrastorage.org/getpro/habr/post_images/84f/7de/b25/84f7deb25d3d0b03d27835b59c6c7b48.jpg)

Выделение, наоборот, привязывается к пикселям:

![Minion](https://habrastorage.org/getpro/habr/post_images/de0/a4d/87b/de0a4d87b04ed42e2790e4ca12abba64.jpg)

Даже если верстальщик был внимателен и заметил это, то все равно встаёт вопрос: куда всё таки дизайнер хотел поставить направляющую — левее или правее?

Простой совет, как избежать этой проблемы: сначала выполните выделение, а затем установите направляющую на линию выделения.


#### 3. Группы, слои, маски

Верстальщику необходимо отдавать именно подготовленный к вёрстке макет, а не рабочий проект весом под 100 Мб. 

Что значит «подготовленный к вёрстке макет»?

1. Группы и слои проименованы: основные элементы дизайна необходимо именовать
  - в соответствии с их назначением (блока/части/модуля)
  - указывать смысловые названия для:
    - групп слоев;
    - основных слоёв;
    - контентных модулей по их предназначению (например, названия можно брать из того, что обсуждалось с лицом, представляющим заказчика/ТЗ) и в нисходящем порядке, т.е. от высшего к низшему.
  - лучше всего латиницей

  Примеры: 

  ![Minion](http://pix.toile-libre.org/upload/original/1470393498.png)![Minion](http://pix.toile-libre.org/upload/original/1470393477.png)

2. Если есть сгруппированные слои, то группировка выполнена в соответствии с логической структурой страницы:
шапка, контент, баннер, кнопка, список и т. д., и вложенность не превышает разумных пределов, а лучше вообще избегать вложенности групп.
3. Скрытые, но не играющие никакой роли в дизайне слои, должны быть удалены
  > Неактуальные скрытые слои вводят в заблуждение, подразумевающее изменение стилей при определенных условиях. Поэтому такие слои не просто лишние в шаблоне, но и мешают. Просьба удалять их.    
    ![Minion](http://pix.toile-libre.org/upload/original/1470392439.png) (Антипример)

4. Обрезка фотографий (главным образом, скругления углов и т.п.) должны производиться с сохранением исходных изображений — лучше всего делать это с помощью масок
  > Если подразумевается, что элемент на сайте целостный, просьба его и реализовать целостным. Нет смысла его держать разбитым на куски, чтоб обрезать по маске эти куски, потом объединять несколько слоев (после того как нашел нужные) в одну картинку и только потом извлекать;
    ![Minion](http://pix.toile-libre.org/upload/original/1470393339.png)(антипример)


5. Размер холста должен соответствовать максимально возможной ширине/высоте дизайна


#### 4. Цвета

Вернёмся к проблемам с цветами. Для элементов, имеющих по замыслу одинаковый цвет границы/заливки/шрифта, необходимо указывать, как нетрудно догадаться, одинаковый цвет в параметрах наложения, свойствах символа и т.д.

Что за ерунда? И так ведь понятно, что цвет одинаковый.
Но не тогда, когда, например, цвет одной надписи отличается от другой всего на половину тона. Придирчивый заказчик может запросто испортить верстальщику, выбравшему неверный вариант их двух возможных, настроение до конца дня, если заметит эту разницу. А дизайнер по факту будет не при чём.

Совет дизайнерам: используйте палитры или каким-либо образом заготовленные наборы цветов, чтобы избежать разногласий.

#### 5. Трансформации, фигуры

Прошли времена вёрстки скругленных уголков картинками. Каждый уважающий себя браузер умеет скруглять углы с помощью CSS-свойства border-radius, чем и пользуются верстальщики.

Но порой встречаются дизайн-макеты, в которых скругления «не совсем округлые». Что это значит? Просто дизайнер в какой-то момент изменил размер своего скругленного прямоугольника с помощью функции Transform, изменив его пропорции. В результате углы оказались вовсе не скругленными, а «овальными».

Само собой, верстальщик не станет из-за этого нарезать блок картинками. Но это говорит о ненадлежащем отношении дизайнера к работе.


![Minion](https://habrastorage.org/getpro/habr/post_images/0c2/2f0/045/0c22f004512605c794faeaeda2a6c7fb.jpg)

Решив вопрос скгругления углов, верстальщик вновь столкнулся с проблемой:

![Minion](https://habrastorage.org/getpro/habr/post_images/dc8/8a8/abd/dc88a8abd8b405ea91c0185166ea1de8.jpg)

Когда речь идет о pixel-perfect вёрстке, подобные неточности в дизайне могут доставить немало хлопот верстальщику. В данном случае левый край блока имеет нечёткую границу, а из-за этого невозможно точно определить ширину блока.

Для предотвращения нечеткости границ фигур в Photoshop 13 есть специальная опция «выровнять края».


#### 6. Единицы измерения, символы, абзацы

Чаще всего в вебе нам приходится иметь дело с пикселями. В большинстве случаев нет причин использовать какие-либо другие единицы измерения, такие как пункты, дюймы и т. д. Желательно, чтобы дизайнер устанавливал в настройках Photoshop именно пиксели в качестве основной единицы измерения.

Как и в случае с цветами, для дизайна текстовых блоков дизайнеру следует придерживаться строго фиксированных значений размеров. Для каждого абзаца необходимо однозначно задавать кегль и интерлиньяж.

Если Вы изменили размер текста с помощью Transform, то после этого кегль или другие свойства символа могут принять дробное значение (например, 14.5 px). При подготовке макета к вёрстке обязательно нужно привести все размеры к целым значениям. В противном случае перед верстальщиком вновь встанет дилемма: 14 или 15 пикселей?

Что касается выключки строк (выравнивания), то дизайнеру следует помнить: браузеры полноценно поддерживают лишь 3 варианта: по левому краю, по правому краю или по центру. Выключка по формату в браузере зачастую сильно отличается от того, что мы видим в Photoshop.

#### 7. Параметры наложения, стили слоя

![Minion](https://habrastorage.org/getpro/habr/post_images/d42/2fd/6f5/d422fd6f5794e138eebcfadfcd0d9c24.jpg)

- Тени и свечения (внутренние и внешние)<br>
  _ text-shadow _ — тень для текста<br>
  _ box-shadow _ — тень для блока
- Обводка
  _ border _ — обводка линией<br>
  _ box-shadow _ — возможна обводка однопиксельной тенью<br>
  _ outline _ — строго прямоугольная обводка
- Заливка
  _ background-color _ — заливка цветом (возможно полупрозрачным)<br>
  _ background-image _ — заливка узором/картинкой<br>
  _ background-image: linear-gradient() _ — линейный градиент<br>
  _ background-image: radial-gradient() _ — радиальный градиент
- Прозрачность
  _ opacity _ — прозрачность элемента целиком<br>
  _ [color:] rgba(r,g,b,a) _ — прозрачность rgb-цвета, где a — степень непрозрачности от 0 до 1<br>
  _ [color:] hsla(h,s,l,a) _ — прозрачность hsl-цвета, где a — степень непрозрачности от 0 до 1



О поддержке браузерами того или иного свойства можно узнать [[здесь]](http://caniuse.com/ "здесь!").

Стоит помнить: браузеры не поддерживают ни один из режимов наложения, такие как Overlay, Screen и др. Это необходимо обязательно учитывать и при необходимости обходиться нормальным режимом наложения в сочетании с прозрачностью и градиентами.


#### Подводя итог

Нами были рассмотрены некоторые нюансы подготовки дизайнером psd-макета для верстальщика. Надеюсь, кто-нибудь почерпнёт из нее для себя что-либо новое или просто найдет в ней повод напомнить своим дизайнерам о несложных правилах, придерживаясь которых они прослывут педантами в хорошем смысле этого слова, а их работы будут поражать аккуратностью исполнения.



![Minion]()

![Minion]()

![Minion]()