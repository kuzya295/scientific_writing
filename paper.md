# Разработка приложения для 3D моделирования в VR на основе hand tracking
Ключевые слова: 3D моделирование, hand-tracking, Leap Motion, распознавание жестов.

## Аннотация

В данной статье была исследована проблема взаимодействия человека и компьютера в процессе 3D моделирования. В процессе исследования были рассмотрены технологии, позволяющие человеку работать с 3D моделью при помощи жестов рук, и сделан вывод о том, что в большой степени на качество этих технологий влияет используемое устройство для распознавания жестов. 

Для решения проблемы была пославлена цель разработать приложение для 3D моделирования в VR при помощи hand tracking на основе контроллера Leap Motion. Так как основной сложностью является распознавание и интерпретация пользовательского ввода, а не сама деформация 3D модели, основное внимание в данной работе уделялось интеграции Leap Motion и Unity. В статье рассматривались такие нюансы, как преобразование пространственных координат контроллера в координаты Unity, проблема некорректной интерпретации пользовательского ввода при использовании похожих жестов для разных задач, калибровка точности жестов и позиций рук.

В результате разработки приложения была достигнута цель и выдвинуты направления для дальнейших исследований, связанных с расширением функционала приложения и перечня допустимых жестов, а также с возможностью пользователю самому настраивать используемые жесты.

## Введение

В настоящее время активно развивается проектирование объектов в цифровом трехмерном пространстве — 3D моделирование. Одной из проблем в этой области является процесс взаимодействия человека и машины. Несмотря на то, что в повседневной жизни для взаимодействия с окружающим миром в большинстве случаев используются руки, при работе с 3D-моделирующими приложениями (Autodesk Maya [1], Blender [2], 3ds Max [3] ...) человек вынужден использовать стандартные устройства ввода. В связи с этим у начинающих пользователей приложений для 3D моделирования возникают сложности с понятием пользовательского интерфейса.

Из вышесказанного возникает идея управлять 3D моделирующими приложениями исключительно при помощи жестов, что задает цель данной работы: разработать приложение для 3D моделирования в VR при помощи hand tracking.

Для реализации поставленной цели необходимо решить следующие задачи:
- исследовать существующие решения по 3D моделированию при помощи hand tracking;
- реализовать свое приложение для 3D моделирования при помощи hand tracking.

Осуществлять hand tracking можно при помощи различных средств, например, контроллеров для игровых приставок или очков дополненной реальности, реагирующих на движение рук. Однако при использовании таких устройств сковываются движения или может ощущаться дискомфорт. Альтернативой можно считать устройства для отслеживания жестов, работающие при помощи специальных камер, такие как Leap Motion [4], из которых в режиме реального времени можно извлекать данные о положении рук и пальцев. Поэтому предметом исследования 3D моделирования в VR при помощи hand tracking в данной статье является интеграция Unity и Leap Motion для разработки такого приложения.

## Обзор существующих решений

### Описание аналогов

Для того, чтобы выявить, что должно представлять из себя разрабатываемое приложение и какими качествами оно должно обладать, необходимо рассмотреть аналоги. Для обзора существующих решений были выбраны технологии, позволяющие моделировать виртуальные 3D объекты без помощи стандартных устройств пользовательского ввода, опираясь на движения рук и пальцев в пространстве и жесты. 
Основные требования к функционалу рассматриваемых аналогов включают возможность изменять положение модели (перемещать и/или вращать и/или изменять масштаб) и возможность изменять форму модели / создавать модель с нуля.

Приведем отобранные для рассмотрения аналоги с их кратким описанием.

1. Первая технология была предложена Хироаки Нишино в 1998 году - 3D моделирование объектов с использованием пространственных и пиктографических жестов [5]. Для ее использования необходимы бимануальные жестовые перчатки, очки с затвором и 200-дюймовый стереоскопический экран. Для создания модели необходимо подготовить несколько примитивных фигур, объединить эти примитивы, чтобы сформировать «грубую» форму и провести ее деформацию для корректировки. Присутствует возможность вращать объекты, захватывая их двумя руками, и регистрировать предпочитаемые жесты перед использованием технологии.

2. В 2001 году Стивеном Школьном была предложена еще одна технология - рисование органических поверхностей в воздухе с помощью рук [6]. При помощи магнитного инструмента, прикрепленного к рукам, пользователь может рисовать поверхности в воздухе над «отзывчивым» рабочим столом. При помощи очков со стереоскопическим затвором над столом можно увидеть получаемую модель.
Пользователи могут перемещать объекты с помощью кухонных щипцов, оснащенных магнитными трекерами и датчиками (чтобы определять, когда они закрыты). Когда щипцы закрыты, пользователь может захватить объект и переместить его в виртуальное трехмерное пространство. Второй щипец можно использовать вместе с первым для масштабирования объектов (раздвигая с сдвигая щипцы по отношению друг к другу).

3. Кевин Т. Макдоннелл и Влодарчик в 2001 году разработали систему моделирования, которая позволяет деформировать упругую виртуальную глину, используя тактильный инструмент взаимодействия, обеспечивая реалистичный опыт скульптинга [7]. Пользовательский интерфейс состоит из тактильного устройства PHANToM, стандартной 2D-мыши и экранных элементов управления графическим интерфейсом.
Один из способов использования тактильного инструмента состоит в том, чтобы деформировать модель так же, как при лепке из глины. Геометрические инструменты используются для выбора ячеек в объекте с помощью трехмерного курсора для их вдавливания, разделения или выдавливания. Физические инструменты предназначены для формирования объекта путем редактирования физических свойств, таких как точки массы и распределение жесткости.

4. Цзя Шэн в 2006 году предложил интерфейс для виртуального трехмерного моделирования с использованием губки [8]. Данное приложение способно манипулировать 3D-моделями, используя губку в качестве инструмента. Основой является технология отслеживания движения на основе камеры для отслеживания пассивных маркеров на пальцах и губке, как показано на рисунке.

5. Freeform 3 - приложение, разработанное для использования с Leap Motion [4] (небольшое устройство длиной менее 8 см, представляющее собой оптическую систему слежения на основе стереозрения) [9]. В данном приложении 3D объект представляется вращающаяся форма из глины, стекла или пластика помещается на невидимый стол. Пользователи могут использовать свой палец в качестве инструмента для изменения формы. Для смены режимов работы данного приложения (выбор сцены, материала, вращения) предназначены иконки, располагающиеся по краям окна. 
 
### Сравнение аналогов
Определим критерии, по которым будем оценивать вышеперечисленные аналоги.

1. Манипулирование дополнительными устройствами.

Критерий обозначает необходимость во время работы держать специальные устройства в руках или надевать на руки. Если такая необходимость присутствует, то движения человека могут быть скованы либо человек может ощущать дискомфорт.

"+" означает, что требуется манипулировать дополнительными устройствами во время работы;

"-" означает, что не требуется.

"-" - "хорошо"; "+" - "плохо".

2. Необходимость работать с контекстным меню для смены режимов работы.

Критерий обозначает то, что в процессе моделирования не нужно отвлекаться на то, чтобы изменить какие-либо режимы/параметры работы где-нибудь в боковом меню. Это способствует уменьшению реалистичности, что является одним из главных требований к технологии VR.

"+" означает, что для смены режимов требуется работать с контекстным меню;

"-" означает, что не требуется.

"+" - "плохо"; "-" - "хорошо".

3. Доступность/цена необходимых устройств.

Критерий обозначает наличие для покупки в интернет-магазинах устройств, необходимых для 3D моделирования. Если возможность приобрести устройство есть, рассматривается еще и его цена. Важность критерия обоснована тем, что без возможности приобрести необходимые устройства либо при слишком высокой цене технология/метод не может получить широкого распространения.

"+/число$" означает, что устройство можно приобрести за цену, указанную после "/";

"-" означает, что устройство в свободном доступе найти нельзя.

"+/число$" - "хорошо"; "-2 - "плохо". Чем ниже цена, тем лучше.

4. Погрешность распознавания положения.

Критерий обозначает погрешность распознавания устройством, используемым аналогом, положения руки/маркера.

Чем больше для аналога погрешность, тем меньше точность процесса 3D-моделирования из-за некорректного распознавания жестов и положений рук.

Сравнение рассмотренных аналогов по вышеперечисленным критериям представлено в табл. 1.

Таблица 1 - сравнение аналогов

|     | аналог 1  | аналог 2 | аналог 3 | аналог 4 | аналог 5 |
| --- | --- | --- | --- | --- | --- |
| **манипулирование дополнительными устройствами** | + | + | + | + | - |
| **необходимость работать с контекстным меню для смены режимов работы** | - | - | + | - | + | 
| **доступность/цена необходимых устройств** | - | - | +/2400$ | - | +/90$ |
| **погрешность распознавания положения** |	2,54 см |	0,4 см |	0,26 см |	0,02 см |	0,012 см |

Цены устройств для аналогов 3 и 5 взяты из источников [10] и [4]. 
Погрешности для аналогов 1-5 взяты из источников [11], [12], [13], [14], [15].

В результате сравнения было выявлено, что у каждой из рассмотренных технологий есть слабые стороны в отношении рассмотренных критериев. Однако приложение Free Form показывает лучшие результаты среди рассмотренных аналогов (побеждает по двум критериям из трех): за разумную цену купить оборудование можно только для Free Form, что означает, что для рядового пользователя доступно в основном только это приложение; при его использовании не нужно использовать какие-либо датчики либо держать специальные устройства в руках, так что руки полностью свободны (ограничены только пространством, в котором камеры улавливают движения рук).

Это означает, что при разработке приложения для 3D моделирования при помощи hand tracking необходимо взять лучшие стороны от Free Form (использовать устройство Leap Motion, чтобы соответствовать критериям "манипулирование дополнительными устройствами" и  "доступность/цена необходимых устройств"), но постараться избежать необходимости работать с контекстным меню для смены режимов работы (всю работу выполнять только при помощи специальных жестов).

## Выбор метода решения

На основании обзора существующих решений было определено, что должно собой представлять решение задачи и какими основными качествами оно должно обладать.

Главное требование не изменилось: решение должно представлять собой разработанное приложение для 3D моделирования в VR при помощи hand tracking. Однако добавились некоторые уточнения к реализации, которые приведены ниже.

Hand tracking должен осуществляться при помощи контроллера Leap Motion по следующим причинам:

- Отслеживание рук и жестов через обычную веб-камеру возможно, но имеет малую точность и скорость по сравнению с решениями, использующими дополнительные устройства для отслеживания рук, поэтому не распространено для задачи 3D моделирования в VR. Поэтому необходимо использование специального устройства для отслеживания жестов рук.
- Leap Motion - самое доступное для покупки устройство среди рассмотренных аналогов, т.е. его можно приобрести на официальном сайте за самую низкую цену по сравнению с устройствами, необходимыми для работы рассмотренных аналогов.
-Leap Motion относительно рассмотренных аналогов удобно в исспользовании: для взаимодействия с ним нужно только подключить его к компьюьеру, необходимость держать в руках какие-либо дополнительные датчики либо устройства (или прикреплять их к рукам) отсутствует.
- Leap Motion из устройств рассмотренных аналогов имеет меньшую погрешность распознавания положения.

В отличие от Free Form, где hand tracking также реализован при помощи Leap Motion, в разрабатываемом приложении работа пользователя, связанная с 3D моделированием, должна осуществляться только при помощи жестов, т.е. без необходимости менять режимы работы в контекстных меню. В таком случае управление будет более интуитивно понятно, не будет необходимости изучать все возможности интерфейса.

Основные требования к программе остаются такими же, как при выборе аналогов для сравнения: необходимо, чтобы была возможность изменять положение объекта в пространстве (вращать, перемещать, масштабировать) и изменять форму объекта.

## Описание метода решения

### Используемые технологии
В предыдущем разделе было решено использовать контроллер Leap Motion для пользовательского ввода, на основании чего выбирались используемые технологии.

Выбор среды разработки - Unity - был обусловлен возможностью VR интеграции c Leap Motion [17]. Среди вариантов также была среда разработки Unreal, однако в разрабатываемом приложении нет необходимости использовать высококачественные графические эффекты и лучше избегать высокой вычислительной мощности, присущих данному кандидату.

Для интеграции Leap Motion и Unity в программе используется ресурс Leap Motion Core Assets [18]. Он позволяет проекту Unity получать данные из фреймов, в которых Leap Motion API хранит атрибуты для рук, пальцев, костей и суставов пользователя. Эти данные используются для интерпретации пользовательского ввода.

В качестве языка разработки был выбран С#. Основным требованием при выборе была поддержка языком ресурса Leap Motion Core Assets.

### Сценарий использования
Для общего понимания, что из себя представляет приложение, рассмотрим его работу с точки зрения пользователя, а именно - сценарий использования.

После запуска приложения перед пользователем возникает сцена со сферой в центре, которая является объектом, с которым пользователь может взаимодействовать. Для начала взаимодействия пользователю необходимо поместить руки над подключенным контроллером Leap Motion на высоте около 15 см - на экране появится изображение рук. При дальнейшей работе с объектом пользователь должен ориентироваться на расположение рук в виртуальном пространстве: следить за тем, чтобы руки отображались на экране, т.е. не выходили за пределы зоны видимости контроллера, и совершать жесты в требуемом положении относительно объекта.

Рассмотрим виды взаимодействия пользователя с моделью в виртуальном пространстве.

1. Изменение формы.
Для того, чтобы изменить форму объекта, пользователю необходимо поднести к поверхности объекта правую руку, соединить указательный и большой пальцы, а затем, не изменяя жеста, перемещать руку в пространстве в то положение, в котором должна оказаться выбранная точка для деформации сетки объекта. После этого пальцы следует разъединить.

2. Масшабирование.
Для того, чтобы изменять размер объекта на сцене, пользователю необходимо поместить обе руки в область видимости контроллера, сжать их в кулаки, и уменьшать расстояние между ними по оси Х, чтобы уменьшить объект, или увеличивать расстояние между руками, чтобы увеличить объект. Для прекращения масштабирования кулаки надо разжать.

3. Перемещение.
Для того, чтобы перемещать объект на сцене, пользователю необходимо поместить левую руку в центр объекта, сжать ее в кулак и перемещать руку в пространстве. Модель будет перемещаться вместе с рукой пользователя. Чтобы закончить перемещение объекта, кулак надо разжать.

4. Вращение.
Для вращения объекта также используется левая рука. Пользователю необходимо соединить указательный и большой пальцы (как для изменения формы объекта) и перемещать их в пространстве. Процесс вращения модели происходит аналогично вращению глобуса, только не вокруг оси, а вокруг центральной точки объекта.

### Особенности интеграции Leap Motion и Unity
Рассмотрев, как приложение должно работать с точки зрения пользователя, можно приступить к описанию основных особенностей реализации, связанных с интеграцией Leap Motion и Unity.

1. Непрерывность отслеживания рук.
При работе пользователя в VR необходимо обеспечить непрерывное поступление данных от Leap Motion API с начала запуска программы. 
Для этого в методе Start необходимо создать объект Controller при помощи метода Controller() [16], а в методе Update() необходимо получать обновленные данные о руках от фрейма Leap Motion при помощи метода Frame() [16].

2. Координаты.
Для всех решаемых задач пользовательского ввода важно пространственное положение рук/пальцев в виртульной реальности, однако было обнаружено, что системы координат Leap Motion и Unity не совпадают. Это связано с тем, что контроллер предоставляет координаты в миллиметрах реального мира, а не в системе отсчета Unity.

Для перевода координат с фрейма Leap Motion в систему координат Unity было решено использовать объект InteractionBox. Он представляет собой прямоугольную призму и предоставляет нормализованные координаты для рук и пальцев при помощи метода NormalizePoint(Vector position) [16]. Метод преобразует координаты Leap Motion в координаты в диапазоне [0; 1], так, что минимальное значение InteractionBox отображается на 0, а максимальное значение InteractionBox отображается на 1. После этого координаты необходимо "растянуть" на всю ширину объекат InteractionBox.

Последним шагом для приведения координат Leap Motion к координатам Unity является отражение оси z, т.е. домножение всех z-координат на -1. Это связано с тем, что в контроллере используется правосторонняя система координат, а в Unity - левосторонняя.

3. Выбор жестов.
При разработке приложения большое внимание уделялось тому, чтобы жесты пользователя для разных взаимодействий не могли перепутаться и при этом оставались интуитивно понятными. Так, например, для вращения объекта и для деформации точки пользователь должен совершить один и тот же жест - соединить указательный и большой пальцы, а для масштабирования и перемещения объекта - сжать кулак.

Во избежание спутывания операций было решено использовать ввод левой рукой, правой рукой и обеими руками четко разделенным. 
Для этого при каждом обновлении фрейма контроллера выполняется проверка, приведенная в коде ниже:

if (frame.Hands.Count == 2)
    //масштабирование объекта
else{
    if(frame.Hands[0].IsRight)
        //деформация формы
    if(frame.Hands[0].IsLeft)
        //перемещение либо вращение объекта, в зависимости от выполненного жеста
}

4. Учет погрешностей пользователя. 
При захвате пользователем точки на объекте для деформации модели сложно достигнуть того, чтобы координаты пальцев пользователя полностью совпадали с точкой, т.к. для этого точность движений пользователя должна составлять доли миллиметра, что вызывает значительные сложности.  Было решено использовать допустимые границы, определяющие близость расстояния пальцев пользователя до поверхности объекта и, если пользователь попадает в заданные границы, выбирать ближайшую точку для взаимодействия.

Аналогичная ситуация с самим распознаванием жестов сведения большого и указательного пальцев (жест "pinch") и распознаванием жеста сжатия руки в кулак (жест "grab"). Для проверки выполнения этих жестов вызываются методы GrabStrength() [16] и PinchStrength() [16], которые возвращают число из диапазона [0; 1], где 0 означает, что проверяемый жест не выполнен пользователем, а 1 означает, что с вероятностью 1 пользователь выполнил проверяемый жест. Нижняя граница, при которой жест пользователя "засчитывается", была установлена в 0.8.

## Заключение

В ходе данного исследования был составлен обзор существующих технологий для 3D моделирования в VR при помощи hand tracking и было выявлено, что основным фактором, влияющим на качество рассмотренных аналогов, является устройство, используемое для распознавания жестов. Лучшие результаты среди рассмотренных решений показал контроллер Leap Motion, используемый приложением FreeForm, который имеет наименьшую погрешность - 0.012 см и цену - 90$ среди аналогов. По итогам исследования было решено использовать контроллер Leap Motion для осуществления отслеживания рук.

Было реализовано приложение для 3D моделирования в VR при помощи hand tracking. Данное приложение после запуска не нуждается в пользовательском вводе с мыши/клавиатуры, а управляется исключительно жестами, что не требует отвлечения внимания пользователя на 2D ввод. 

Были предложены решения для некоторых проблем в области интеграции Leap Motion и Unity: процедура перевода координат контроллера в координаты Unity при помощи объекта InteractionBox() и метода NormalizePoint(Vector Point) [16]; упрощение ввода пользователя за счет установления допустимых погрешностей для положения рук и жестов; снижение вероятности спутывания жестов при помощи разделения ввода для левой, правой и обеих рук.

Таким образом, цель работы была достигнута и появляется возможность для разработки улучшений приложения. Направление дальнейших исследований включает в себя увеличение количества возможных преобразований 3D модели путем добавления таких воздействий как сплющивание, скручивание, разрывание объекта и т.д. Для реализации этого необходимо будет разработать новые жесты для обеспечения пользовательского ввода, притом такие, чтобы программа не могла интерпретировать предполагаемое пользователем действие как другое. После расширения функционала приложения планируется сделать его настраиваемым, то есть внедрить возможность пользователю задавать собственные жесты для работы в приложении.

## Список литературы

[1] https://www.autodesk.ru/products/maya/overview

[2] https://www.blender.org

[3] https://www.autodesk.ru/products/3ds-max/overview

[4] https://www.leapmotion.com

[5] Hiroaki Nishino, Kouichi Utsumiya, K. K. (1998). 3d object modeling using spatial and pictographic gestures. VRST.

[6] Steven Schkolne, Michael Pruett, P. S. (2001). Surface drawing: Creating organic 3d shapes with the hand and tangible tools. CHI.

 [7] Kevin T. McDonnell, H. Q. and Wlodarczyk, R. A. (2001). Virtual clay: A real-time sculpting system with haptic toolkits.

 [8] Jia Sheng, Ravin Balakrishnan, K. S. (2006). An interface for virtual 3d sculpting via physical proxy.

 [9] https://www.fastcompany.com/3021997/leap-motions-free-form-app-lets-you-sculpt-in-mid-air

 [10] https://controlengrussia.com/programmnye-sredstva/taktilnoe-upravlenie-narabotka-opyta/

 [11] Ronan Boulic, Gerard Hegron. (1996). Computer Animation and Simulation.

 [12] Kristy K. Brock. (2016). Image Processing in Radiation Therapy.

 [13] Wiegand, Thomas E. von; Schloerb, David W.; Sachtler, W. L. (1999). Virtual Workbench: Near-Field Virtual Environment System with Applications.

 [14] Pierre Merriaux, Yohan Dupuis, Rémi Boutteau, Pascal Vasseur, Xavier Savatier. (2017). A Study of Vicon System Positioning Performance.

 [15] Frank Weichert, Daniel Bachmann, Bartholomäus Rudak, Denis Fisseler. (2013). Analysis of the Accuracy and Robustness of the Leap Motion Controller.
 
 [16] https://developer-archive.leapmotion.com/documentation/v2/
