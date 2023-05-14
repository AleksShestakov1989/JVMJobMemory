# JVM (JavaCore Lesson 10)

В Metaspace  хранится вся информация о классах (JvmComprehension.class, Object.class, Integer.class, System.class), то есть их имена, методы, поля и т.д.
Classloaders: загрузка классов на уровне Bootstrap( все базовые классы и входят в комплект поставки).
1. Выполнение метода main():
- в стеке создается фрейм main для хранения значений всех переменных этого метода
- в этом фрейме main сохраняется примитивная переменная int i = 1 //1
2. Выделяется память в куче под объект Object //2
- создается переменная и ей присваевается адресс объекта Object //2
- выделяется память в стеке фрейма main //2
3. так же как и с Object используется автоупаковка примитивного типа данных в класс-оболочку//3
4. создается новый фрейм для метода printAll() //4
- для переданных параметров в метод создаются переменные и выделяется место в стеке //4
- присваиваются новые ссылки на используемые объекты, так как создался новый фрейм и в нем уже не видно старые ссылки //4
5. создается новый объект Integer в памяти кучи и присваивается ссылка на переменную uselessVar в фрейме printAll //5
6. в стеке создается новый фрейм метода println(), в котором создаются ссылки  на используемые объекты //6
- в стеке создается новый фрейм для метода toString(),  в котором создаются ссылки  на используемые объекты //6
7. в стеке создается новый  фрейм для метода println(), в котором создается ссылка на объект "finished" , а в куче создается объект String с текстом "finished" //7
# Сборщик мусора:
- после выполнения кода метода printAll(o, i, ii) сборщик мусора может очистить кучю, удалить все объекты,так как они больше не используются //4