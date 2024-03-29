## Сравнение аналогов
## Принцип отбора аналогов

Для обзора используются технологии, позволяющие моделировать виртуальные 3d объекты без помощи стандартных устройств пользовательского ввода, опираясь на движения рук в пространстве и жесты рук. 
Основные требования к функционалу: возможность изменять положение модели (перемещать и/или вращать и/или изменять масштаб) и возможность изменять форму модели / создавать модель с нуля.

### <Аналог1>

Первая технология была предложена Хироаки Нишино в 1998 году - 3D моделирование объектов с использованием пространственных и пиктографических жестов [1]. Для ее использования необходимы бимануальные жестовые перчатки, очки с затвором и 200-дюймовый стереоскопический экран. Для создания модели необходимо подготовить несколько примитивных фигур, объединить эти примитивы, чтобы сформировать «грубую» форму и провести ее деформацию для корректировки. Присутствует возможность вращать объекты, захватывая их двумя руками, и регистрировать предпочитаемые жесты перед использованием технологии.

### <Аналог2>

В 2001 году Стивеном Школьном была предложена еще одна технология - рисование органических поверхностей в воздухе с помощью рук [2]. При помощи магнитного инструмента, прикрепленного к рукам, пользователь может рисовать поверхности в воздухе над «отзывчивым» рабочим столом. При помощи очков со стереоскопическим затвором над столом можно увидеть получаемую модель.
Пользователи могут перемещать объекты с помощью кухонных щипцов, оснащенных магнитными трекерами и датчиками (чтобы определять, когда они закрыты). Когда щипцы закрыты, пользователь может захватить объект и переместить его в виртуальное трехмерное пространство. Второй щипец можно использовать вместе с первым для масштабирования объектов (раздвигая с сдвигая щипцы по отношению друг к другу).

### <Аналог3>

Кевин Т. Макдоннелл и Влодарчик в 2001 году разработали систему моделирования, которая позволяет деформировать упругую виртуальную глину, используя тактильный инструмент взаимодействия, обеспечивая реалистичный опыт скульптинга [3]. Пользовательский интерфейс состоит из тактильного устройства PHANToM, стандартной 2D-мыши и экранных элементов управления графическим интерфейсом.
Один из способов использования тактильного инструмента состоит в том, чтобы деформировать модель так же, как при лепке из глины. Геометрические инструменты используются для выбора ячеек в объекте с помощью трехмерного курсора для их вдавливания, разделения или выдавливания. Физические инструменты предназначены для формирования объекта путем редактирования физических свойств, таких как точки массы и распределение жесткости.

### <Аналог4>

Цзя Шэн в 2006 году предложил интерфейс для виртуального трехмерного моделирования с использованием губки [4]. Данное приложение способно манипулировать 3D-моделями, используя губку в качестве инструмента. Основой является технология отслеживания движения на основе камеры для отслеживания пассивных маркеров на пальцах и губке, как показано на рисунке.

### <Аналог5>

Freeform 3 - приложение, разработанное для использования с Leap Motion (небольшое устройство длиной менее 8 см, представляющее собой оптическую систему слежения на основе стереозрения) [5]. В данном приложении 3d объект представляется вращающаяся форма из глины, стекла или пластика помещается на невидимый стол. Пользователи могут использовать свой палец в качестве инструмента для изменения формы. Для смены режимов работы данного приложения (выбор сцены, материала, вращения) предназначены иконки, располагающиеся по краям окна. 
 
## Критерии сравнения аналогов

### <Критерий 1 - манипулирование дополнительными устройствами>

Критерий обозначает необходимость во время работы держать специальные устройства в руках или надевать на руки. Если такая необходимость присутствует, то движения человека могут быть скованы либо человек может ощущать дискомфорт.

"+" означает, что требуется манипулировать дополнительными устройствами во время работы;

"-" означает, что не требуется.

"-" - "хорошо"; "+" - "плохо".

### <Критерий 2 - необходимость работать с контекстным меню для смены режимов работы>

Критерий обозначает то, что в процессе моделирования не нужно отвлекаться на то, чтобы изменить какие-либо режимы/параметры работы где-нибудь в боковом меню. Это способствует уменьшению реалистичности, что является одним из главных требований к технологии VR.

"+" означает, что для смены режимов требуется работать с контекстным меню;

"-" означает, что не требуется.

"+" - "плохо"; "-" - "хорошо".

### <Критерий 3 - доступность/цена необходимых устройств>

Критерий обозначает наличие для покупки в интернет-магазинах устройств, необходимых для 3d моделирования. Если возможность приобрести устройство есть, рассматривается еще и его цена. Важность критерия обоснована тем, что без возможности приобрести необходимые устройства либо при слишком высокой цене технология/метод не может получить широкого распространения.

"+/число$" означает, что устройство можно приобрести за цену, указанную после "/";

"-" означает, что устройство в свободном доступе найти нельзя.

"+/число$" - "хорошо"; "-2 - "плохо". Чем ниже цена, тем лучше.

### <Критерий 4 - влияющие на точность факторы>

Критерий обозначает факторы, от которых точность распознавания жестов может снижаться. Чем меньше таких условий у аналога, тем меньше вероятность возникновения ошибок. 
Условиями могут являться:
 - Освещенность. При использрвании устройств, которые используют для распознавания камеры, низкая освещенность может являться причиной некорректного распознавания положения рук или жестов.
 - Нахождение в границах распознавания. Если при отслеживании жестов пользователь держит руки на неправильном расстоянии от устройства (ближе/дальше области распознавания), руки не смогут распознаваться.
 - Положение устройства. При расположении устройства под наклоном действия пользователя могут распознаваться с каким-либо смещением. Так, в аналоге №3 из-за того, что пользователь при взаимодействии должен прикладывать силу к устройству, при его неправильном расположении сила тяжести повлечет погрешности.

 Если аналогу несоответствует ни один из приведенных факторов, то все заданные жесты и движения рук будут распознаваться без ошибок. Если присущие аналогу факторы в допустимых пределах, hand tracking также будет осуществляться корректно.

## Таблица сравнения по критериям

|     | аналог 1  | аналог 2 | аналог 3 | аналог 4 | аналог 5 | 
| --- | --- | --- | --- | --- | --- | 
| **манипулирование дополнительными устройствами** | + | + | + | + | - |
| **необходимость работать с контекстным меню для смены режимов работы** | - | - | + | - | + | 
| **доступность/цена необходимых устройств** | - | - | +/2400$ | - | +/90$ | 
| **влияющие на точность факторы** | Нахождение в границах распознавания | Нахождение в границах распознавания | Положение устройства | Освещенность, нахождение в границах распознавания | Освещенность, нахождение в границах распознавания | 

Цены устройств для аналогов 3 и 5 взяты из источников [6] и [7]. 

## Выводы по итогам сравнения

В результате сравнения было выявлено, что у каждой из рассмотренных технологий есть слабые стороны в отношении рассмотренных критериев. Однако приложение Free Form показывает лучшие результаты среди рассмотренных аналогов по первым трем критериям (побеждает по двум критериям из трех): за разумную цену купить оборудование можно только для Free Form, что означает, что для рядового пользователя доступно в основном только это приложение; при его использовании не нужно использовать какие-либо датчики либо держать специальные устройства в руках, так что руки полностью свободны. 

Это означает, что при разработке приложения для 3d моделирования при помощи hand tracking необходимо взять лучшие стороны от Free Form (использовать устройство Leap Motion, чтобы соответствовать критериям "манипулирование дополнительными устройствами" и  "доступность/цена необходимых устройств"), но постараться избежать необходимости работать с контекстным меню для смены режимов работы (всю работу выполнять только при помощи специальных жестов). Также необходимо, опираясь на четвертый критерий, сделать в приложении вывод предупреждений в случаях, когда руки пользователя за пределами зоны распознавания либо освещенность рабочего пространства недостаточна.

## Источники

[1] Hiroaki Nishino, Kouichi Utsumiya, K. K. (1998). 3d object modeling using spatial and pictographic gestures. VRST.

[2] Steven Schkolne, Michael Pruett, P. S. (2001). Surface drawing: Creating organic 3d shapes with the hand and tangible tools. CHI.

[3] Kevin T. McDonnell, H. Q. and Wlodarczyk, R. A. (2001). Virtual clay: A real-time sculpting system with haptic toolkits.

[4] Jia Sheng, Ravin Balakrishnan, K. S. (2006). An interface for virtual 3d sculpting via physical proxy.

[5] https://www.fastcompany.com/3021997/leap-motions-free-form-app-lets-you-sculpt-in-mid-air

[6] https://controlengrussia.com/programmnye-sredstva/taktilnoe-upravlenie-narabotka-opyta/

[7] https://www.arrow.com/en/products/90-0002/ultraleap
