Theory_Exception


1. Что такое исключения?
**Ответ:**
    (И. Блинов. Глава 8.) Исключение — это источник дополнительной информации о ходе выполнения приложения. Такая информация позволяет лучше адаптировать код к конкретным условиям его использования, а также на ранней стадии выявить ошибки или защититься от их возникновения в будущем. В противном случае «подавление» исключений приведет к тому, что о возникшей ошибке никто не узнает или узнает на стадии некорректно обработанной информации.
    (Oracle) Термин « исключение» является сокращением от фразы «исключительное событие». Когда в методе возникает ошибка, метод создает объект и передает его системе времени выполнения. Объект, называемый объектом исключения , содержит информацию об ошибке, включая ее тип и состояние программы на момент возникновения ошибки. Создание объекта исключения и передача его системе времени выполнения называется генерацией исключения .
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/definition.html]
[И. Блинов. 2013 Глава 8. Стр. 201]

2. Какие действия производит система времени выполнения при возникновении исключения?
**Ответ:**
    (Oracle) После того, как метод генерирует исключение, система времени выполнения пытается найти что-нибудь для его обработки. Набор возможных «вещей» для обработки исключения - это упорядоченный список методов, которые были вызваны для доступа к методу, в котором произошла ошибка.
    (Блинов) Каждой исключительной ситуации поставлен в соответствие некоторый класс, экземпляр которого инициируется при исключительной ситуации. Если подходящего класса не существует, то он может быть создан разработчиком.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/definition.html]
   [И. Блинов. 2013 Глава 8. Стр. 202]


3. Как называется блок кода, который обрабатывает исключение?
**Ответ:** 
    (Oracle) Система времени выполнения ищет в стеке вызовов метод, содержащий блок кода, который может обрабатывать исключение. Этот блок кода называется обработчиком исключений . Поиск начинается с метода, в котором произошла ошибка, и продолжается по стеку вызовов в обратном порядке, в котором были вызваны методы. Когда соответствующий обработчик найден, система времени выполнения передает исключение обработчику. Обработчик исключений считается подходящим, если тип созданного объекта исключения соответствует типу, который может быть обработан обработчиком.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/definition.html]

4. Как реализуется требование «Поймай или Укажи» (Catch or Specify)?
**Ответ:** 
    Код языка программирования Java должен соответствовать требованиям Catch или Specify Requirement Это означает, что код, который может вызывать определенные исключения, должен быть заключен в одно из следующего:
        •	tryУтверждение , что перехватывает исключение. tryДолжен предоставить обработчик исключения
        •	метод, указывающий, что он может вызвать исключение. Метод должен предоставить throwsпредложение, в котором перечислены исключения,
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/catchOrDeclare.html]
   [https://docs.oracle.com/javase/tutorial/essential/exceptions/handling.html]
   [https://docs.oracle.com/javase/tutorial/essential/exceptions/declaring.html]


5. Какая иерархия классов исключений?
**Ответ:**
   (Блинов)
   Все исключения являются наследниками суперкласса Throwable и его подклассов Error и Exception из пакета java.lang. Класс RuntimeException является подклассом Exception
**Источник.** [И. Блинов. 2013 Глава 8. Стр. 202]

6. Какие виды исключений относятся к непроверяемым?
**Ответ:**
   Исключение	Значение
   ArithmeticException 	Арифметическая ошибка: деление на нуль и др.
   ArrayIndexOutOfBoundsException 	Индекс массива находится вне границ
   ArrayStoreException 	Назначение элементу массива несовместимого типа
   ClassCastException 	Недопустимое приведение типов
   ConcurrentModificationException 	Некорректная модификация коллекции
   IllegalArgumentException 	При вызове метода использован незаконный аргумент
   IllegalMonitorStateException	Незаконная операция монитора на разблокированном экземпляре
**Источник.** [И. Блинов. 2013 Глава 8. Стр. 204]

7. Какие компоненты могут входить в обработчик исключений?
**Ответ:** Методы, объекты, операторы, новые переменные, новые блоки try.

8. Для каких ситуаций используется оператор try-with-resources?
**Ответ:**
   Оператор try-with-resources - это tryоператор, объявляющий один или несколько ресурсов. Ресурс является объектом , который должен быть закрыт после того, как программа закончит с ним. Оператор try-with-resources гарантирует, что каждый ресурс будет закрыт в конце оператора. Любой реализуемый объект java.lang.AutoCloseable, который включает в себя все реализующие объекты java.io.Closeable, может использоваться в качестве ресурса.
   Пример:
   static String readFirstLineFromFile(String path) throws IOException {
   try (BufferedReader br =
   new BufferedReader(new FileReader(path))) {
   return br.readLine();
   }
   }
   До Java SE 7 можно было использовать finallyблок, чтобы гарантировать, что ресурс закрыт, независимо от того, tryзавершается ли оператор нормально или внезапно.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html]

9. Какой код заключается в блок try?
**Ответ:**
    try {
    code
    }
    catch and finally blocks . .
    Отмеченный сегмент в примере code содержит одну или несколько допустимых строк кода, которые могут вызвать исключение.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/try.html]

10. Выполняется ли весь код блока try в случае возникновения исключения?
**Ответ:**
    Когда используемый объект выбрасывает исключение, исполняющая система немедленно прекращает выполнение try блока; выполняемые вызовы методов не завершены. Затем исполняющая система начинает поиск подходящего обработчика исключений в верхней части стека вызовов методов.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/putItTogether.html]

11. Может ли использоваться только один блок try (без catch или finally)?
**Ответ:**
    Нельзя, так как это нарушает принцип обработки исключений.
    Блок try только определяет блок кода, в котором может произойти исключение, а обрабатывает исключения блок catch.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/handling.html]

12. Какое назначение блока catch?
**Ответ:**  
    Каждый catchблок является обработчиком исключения, который обрабатывает тип исключения, указанный его аргументом.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/catch.html]

13. Сколько блоков catch может содержаться после try-оператора?
**Ответ:**
    Если в блоке try может быть сгенерировано в разных участках кода несколько типов исключений, то необходимо наличие нескольких блоков catch, если только блок catch не обрабатывает все типы исключений.
**Источник.** [И. Блинов. 2013 Глава 8. Стр. 206]

14. Если применяется несколько блоков catch, то в каком порядке в случае возникновения исключения они вызываются?
**Ответ:**
    catchБлок содержит код , который выполняется , если и когда обработчик исключений вызывается. Система времени выполнения вызывает обработчик исключений, когда обработчик является первым в стеке вызовов, который ExceptionTypeсоответствует типу сгенерированного исключения. Система считает совпадением, если брошенный объект может быть легально назначен аргументу обработчика исключений.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/catch.html]

15. Какой код может быть между блоками try и catch?
**Ответ:**  
    Между концом tryблока и началом первого catchблока не может быть никакого кода
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/catch.html]

16. Может ли использоваться блок catch без блока try?
**Ответ:**
    Если в tryблоке возникает исключение, это исключение обрабатывается связанным с ним обработчиком исключений. Чтобы связать обработчик исключений с tryблоком, вы должны поставить catchпосле него блок.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/try.html]

17. Сколько типов исключений может обрабатывать один блок catch?
**Ответ:**
    На практике иногда возникают ситуации, когда инструкций catch несколько
    и обработка производится идентичная, например, вывод сообщения об исключении в журнал.
    try {
    // some operations
    } catch(NumberFormatException e) {
    e.printStackTrace();
    } catch(ClassNotFoundException e) {
    e.printStackTrace();
    } catch(InstantiationException e) {
    e.printStackTrace();
    }
    В версии Java 7 появилась возможность объединить все идентичные инструкции в одну, используя для разделения оператор «|».
    try {
    // some operations
    } catch(NumberFormatException | ClassNotFoundException | InstantiationException e) {
    e.printStackTrace();
    }
    Такая запись позволяет избавиться от дублирования кода.
    Введено понятие более точной переброски исключений (more precise rethrow). Это решение применимо в случае, если обработка возникающих исключений не предусматривается в методе и должна быть передана вызывающему данный метод методу.
**Источник.** [И. Блинов. 2013 Глава 8. Стр. 207]

18. В случае отсутствия исключения в блоке try выполняется ли блок catch?
**Ответ:**
    В этом сценарии все операторы в области действия tryблока выполняются успешно и не вызывают исключений. Выполнение падает до конца tryблока, и исполняющая система передает управление finallyблоку.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/putItTogether.html]

19. Для чего используется блок finally?
**Ответ:**
    (Oracle)
    Finallyблок всегда выполняется , когда tryблок выходов. Это гарантирует выполнение finallyблока даже в случае возникновения непредвиденного исключения. Но finallyполезно для более , чем просто обработки исключений - это позволяет программисту , чтобы избежать код очистки случайно обойти по return, continueили break. Помещение кода очистки в finallyблок - всегда хорошая практика, даже если не ожидается никаких исключений.
    (Блинов)
    Возможна ситуация, при которой нужно выполнить некоторые действия по завершению программы (закрыть поток, освободить соединение с базой данных) вне зависимости от того, произошло исключение или нет. В этом случае используется блок finally, который обязательно выполняется после инструкций try или catch.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/finally.html]
[И. Блинов. 2013 Глава 8. Стр. 211]

20. В случае отсутствия исключения в блоке try выполняется ли блок finally (при его наличии)? 
**Ответ:**
    Finallyблок всегда выполняется, когда tryблок выходов.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/finally.html]

21. Могут ли использоваться блоки try-finally без блока catch?
**Ответ:**
    Try может быть в паре с finally, без catch. Работает это точно так же – после выхода из блока try выполняется блок finally. Это может быть полезно, например, в следующей ситуации. При выходе из метода вам надо произвести какие-либо действия. А return в этом методе стоит в некоторых местах. Писать одинаковый код перед каждым return нецелесообразно. Гораздо проще и эффективнее поместить основной код в try, а код, выполняемый при выходе в finally.
**Источник.** [https://jsehelper.blogspot.com/2016/01/java-core-3.html]

22. Приведите пример кода, в котором используется оператор try-with-resources.
**Ответ:**
    static String readFirstLineFromFile(String path) throws IOException {
    try (BufferedReader br =
    new BufferedReader(new FileReader(path))) {
    return br.readLine();
    }
    }
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html]

23. Какой оператор может использоваться вместо try-with-resources?
**Ответ:**
    В следующем примере finallyвместо оператора try-with-resources используется блок :
    static String readFirstLineFromFileWithFinallyBlock(String path) throws IOException {
    BufferedReader br = new BufferedReader(new FileReader(path));
    try {
    return br.readLine();
    } finally {
    br.close();
    }
    }
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html]

24. Может ли применяться оператор try-with-resources совместно с блоком finally?
**Ответ:**
    tryОператор -with-resources может иметь catch и finally блоки, как обычный tryоператор. В операторе try-with-resources любой блок catch or finally запускается после закрытия объявленных ресурсов.
**Источник.** https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html

25. Какое ключевое слово используется в сигнатуре метода, чтобы указать на возможность выбрасывания им исключения?
**Ответ:**
    (Oracle) Чтобы указать, что метод может вызвать два исключения, добавьте throwsпредложение в объявление метод. Предложение throws состоит из throws ключевого слова, за которым следует список всех исключений, вызванных этим методом, разделенных запятыми. Предложение идет после имени метода и списка аргументов и перед фигурной скобкой, определяющей область действия метода; вот пример:
    public void method() throws Exception {
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/declaring.html]

26. Сколько исключений может выбрасывать метод?
**Ответ:**
    Количество исключений ограничено 64K – 65536 штук. Чем больше исключений выбрасывается, тем больше можно быть точным в отношении любых исключений, которые вы обнаружите.
    НО. Обрабатываемые исключения -' замечательная особенность языка программирования Java. В отличие от возвращаемых кодов, они заставляют программиста отслеживать условия возникновения исключений, что значительно повышает надежность приложения. Это означает, что злоупотребление обрабатываемыми исключениями может сделать API менее удобным для использования.
**Источник.** [http://skipy.ru/technics/exceptions.html#no_trans ]
    [Joshua Bloch. Effective Java. Chapter Exceptions. Статья 41]

27. Какое ключевое слово используется для гарантированного выбрасывания исключения?
**Ответ:**
    Независимо от того, что вызывает исключение, оно всегда вызывается вместе с throw оператором.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/throwing.html]

28 Можно ли создавать свои собственные классы исключений?

29. Приведите примеры наиболее известных подклассов класса Exception. 
**Ответ:**
    IllegalAccessException, NoSuchFieldException, NoSuchMethodException, CloneNotSupportedException, InterruptedException, ClassNotFoundException, IOException
**Источник.** [И. Блинов. 2013 Глава 8. Стр. 203]

30. Приведите примеры наиболее известных подклассов класса RuntimeException.
**Ответ:**
    ArithmeticException; ArrayIndexOutOfBoundsException; ArrayStoreException; ClassCastException; ConcurrentModificationException; IllegalArgumentException; IllegalMonitorStateException; IllegalStateException; IllegalThreadStateException; IndexOutOfBoundsException; NegativeArraySizeException; NullPointerException; NumberFormatException; StringIndexOutOfBoundsException; UnsupportedOperationException.
**Источник.** [И. Блинов. 2013 Глава 8. Стр. 204]

31. Что такое сцепление исключений?
**Ответ:**
    Приложение часто реагирует на исключение, создавая другое исключение. Фактически, первое исключение вызывает второе исключение. Может быть очень полезно знать, когда одно исключение вызывает другое. Цепные исключения помогают программисту в этом.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/chained.html]

32. Приведите пример кода со сцеплением исключений.
**Ответ:**
    В следующем примере показано, как использовать исключение в цепочке.
    попробуйте {
    } catch (IOException e) {
        throw new SampleException ("Other IOException", e);
    }
    В этом примере при IOExceptionперехвате создается новое SampleExceptionисключение с присоединенной исходной причиной, и цепочка исключений передается обработчику исключений следующего более высокого уровня.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/chained.html]

33. Какая информация приводится при трассировке стека во время исключения?
**Ответ:**
    Трассировки стека содержит информацию об истории выполнения текущего потока и перечисляет имена классов и методов , которые были вызваны в тот момент , когда произошло исключение. Трассировка стека - это полезный инструмент отладки, которым вы обычно пользуетесь при возникновении исключения.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/chained.html]

34. В каких случаях целесообразно создавать собственный класс исключения?
**Ответ:**
    Вы должны написать свои собственные классы исключений, если ответите утвердительно на любой из следующих вопросов; в противном случае вы, вероятно, можете использовать чужой.
    •	Вам нужен тип исключения, которого нет на платформе Java?
    •	Помогло бы пользователям, если бы они могли отличить ваши исключения от исключений, создаваемых классами, написанными другими поставщиками?
    •	Ваш код генерирует более одного связанного исключения?
    •	Если вы используете чужие исключения, будут ли пользователи иметь доступ к этим исключениям? Аналогичный вопрос: должен ли ваш пакет быть независимым и самодостаточным?
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/creating.html]

35. Какой класс исключений может использоваться в качестве суперкласса для собственного исключения?
**Ответ:**
    Любой Exceptionподкласс может использоваться как родительский класс LinkedListException. Однако быстрое изучение этих подклассов показывает, что они неуместны, потому что либо слишком специализированы, либо совершенно не связаны с ними LinkedListException. Следовательно, родительский класс LinkedListExceptionдолжен быть Exception.
    Большинство написанных вами апплетов и приложений будут генерировать объекты, имеющие значение Exceptions. Errors обычно используются для серьезных, серьезных ошибок в системе, таких как те, которые препятствуют запуску JVM.
    Для удобочитаемого кода рекомендуется добавлять строку Exceptionк именам всех классов, которые наследуются (прямо или косвенно) от Exceptionкласса.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/creating.html]

36. Какие исключения целесообразно делать проверяемыми, а какие – непроверяемыми?
**Ответ:**
    Вот практический совет: если есть основания ожидать, что клиент восстановится после исключения, сделайте это исключением отмеченным. Если клиент не может ничего сделать для восстановления после исключения, сделайте его непроверенным исключением.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/runtime.html]

37. Какие преимущества в механизме выбрасывания и обработки исключений?
**Ответ:**
    Преимущество 1: Отделение кода обработки ошибок от «обычного» кода
    Исключения позволяют отделить детали того, что делать, когда происходит что-то необычное, от основной логики программы. В традиционном программировании обнаружение ошибок, создание отчетов и обработка часто приводят к путанице в спагетти-коде.
    Преимущество 2: распространение ошибок вверх по стеку вызовов
    Второе преимущество исключений - это возможность распространять сообщения об ошибках вверх по стеку вызовов методов.
    Преимущество 3: Группировка и дифференциация типов ошибок
    Поскольку все исключения, создаваемые в программе, являются объектами, группировка или категоризация исключений является естественным результатом иерархии классов. Примером группы связанных классов исключений в платформе Java являются классы, определенные в java.io- IOExceptionи его потомки. IOExceptionявляется наиболее общим и представляет любой тип ошибки, которая может возникнуть при выполнении ввода-вывода. Его потомки представляют более конкретные ошибки.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/advantages.html]

38. Можно ли выбрасывать исключения в конструкторах?
**Ответ:**
    Да, можно. Пример из практического задания.
    public PurchasesList(String fileName) {
    try (Scanner scanner = new Scanner(new FileReader(PATH + fileName + EXTENSION))) {
    …
    } catch (FileNotFoundException e) {
    …
    }
    } 
**Источник.** [Брюс Эккель Философия Джавы (2015) стр.371]

39. Может ли произойти потеря исключения? Если да – приведите пример.
    **Ответ:**
    Точно так же блок finally может вызвать потерю исключений. Посмотрите вот на этот пример:
    package test;
        import java.io.IOException;
        /**
        * ExceptionLossTest
        */
        public class ExceptionLossTest{
        public static void main(String[] args){
            try {
                try {
                    throw new Exception("a");
                    } finally {
                        if (true) {
                            throw new IOException("b");
                        }
                        System.err.println("c");
                    }
                    } catch (IOException ex) {
                        System.err.println(ex.getMessage());
                    } catch (Exception ex) {
                        System.err.println("d");
                        System.err.println(ex.getMessage());
                    }
                }
            }
    Этот тест очень часто давался на интервью. И правильно отвечали единицы. Между тем – результатом его выполнения будет вывод в консоль b. И только. После инициации первого исключения – new Exception("a") – будет выполнен блок finally, в котором будет брошено исключение new IOException("b"). И именно это исключение будет поймано и обработано. Исходное же исключение теряется.
**Источник.** [http://skipy.ru/technics/exceptions.html]

40. Обладают ли исключения свойством транзакционности?
**Ответ:**
    Cвойством транзакционности исключения не обладают – действия, произведенные в блоке try до возникновения исключения, не отменяются поcле его возникновения.
**Источник.** http://www.skipy.ru/technics/exceptions.html

41. Является ли данный код антипаттерном?
    Обоснуйте ответ.
    void methodCatchesSomeException() {
    ...
    try {
    ...
    } catch (SomeException ex) {
    ...
    }
    ...
    }
    Ответ:
    Нет, не является. Конструкция блока try и catch прописана правильно, первый блок следует за другим. Нет определенных исключений, а значит не требуется операторы throws в названии метода и оператора trрow для обозначения исключения.

42. Является ли данный код антипаттерном?
    Обоснуйте ответ.
    void methodThrowsSomeCheckedException() {
    ...
    throw new SomeCheckedException();
    ...
    }
**Ответ:**
    Да, является. В методе прописано определённое исключение, а значит и в назывании метода следует прописать throws SomeCheckedException.

43. Является ли данный код верным? Укажите почему.
    void methodThrowsSomeCheckedException() throws SomeCheckedException {
    ...
    throw new SomeCheckedException();
    ...
    }
**Ответ:**
    Да, является. В названии метода прописан throws и в теле метода прописан throw.

44. Приведите примеры кода с выбросом RuntimeException явным образом и в случае программной ошибки.
**Ответ:**
    Явным образом:
    void methodThrowsSomeRuntimeException(){
    ...
    throw new SomeRuntimeException();
    ...
    }
    В случае программной ошибки:
    void methodThrowsSomeRuntimeException(){
    try{
    …
    }catch(SomeRuntimeException){
    …
    }

45. Можно ли отрефакторить данный код? Если да, то выполните.
    void methodThrowsSomeRuntimeException() {
    ...
    throw new SomeRuntimeException();
    ...
    }
**Ответ:**
    try{
    …
    }catch(SomeRuntimeException e){
    …
    }
46. Является ли данный код антипаттерном?
    Обоснуйте ответ.
    void methodThrowsSomeRuntimeException() throws SomeRuntimeException {
    ...
    throw new SomeRuntimeException();
    ...
    }
**Ответ:**
    Да, является. RuntimeException являются UncheckedExceptions по этому throws не нужен.

47. В какой версии Java появился оператор try-with-resources? Приведите пример кода с использованием указанного оператора.
**Ответ:**
    С Java SE 7.
    static String readFirstLineFromFile(String path) throws IOException {
    try (BufferedReader br =
    new BufferedReader(new FileReader(path))) {
    return br.readLine();
    }
    } 
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html]

48. Является ли данный код антипаттерном?
    Обоснуйте ответ.
    void methodWithAutocloseableInstance() {
    ...
    try(SomeResource res = new SomeResource(...)) {
    ...
    }
    ...
    }
**Ответ:**
    tryОператор -with-resources может использоваться без catch и finally. Обычно программисты прописывают блок catch после блока try.
    CloseableИнтерфейс расширяет AutoCloseableинтерфейс. closeМетод Closeableинтерфейса генерирует исключения типа в IOExceptionто время как closeметод AutoCloseableинтерфейса генерирует исключения типа Exception. Следовательно, подклассы AutoCloseableинтерфейса могут переопределять это поведение closeметода, чтобы генерировать специализированные исключения, например IOException, или вообще не исключать исключения.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html]

49. Является ли данный код антипаттерном?
    Обоснуйте ответ.
    void methodWithAutocloseableInstance() {
    ...
    try(SomeResource res = new SomeResource(...)) {
    ...
    } catch (CorrectCheckedException ex) {
    …
    }
    ...
    }
**Ответ:**
    tryОператор -with-resources может иметь catchи finallyблокировать, как обычный tryоператор. В операторе try-with-resources любой блок catchor finallyзапускается после закрытия объявленных ресурсов.
**Источник.** [https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html]

50. Является ли данный код антипаттерном?
    Обоснуйте ответ.
    try {
    …
    }  catch (SomeException е) {
    //no code
    }
**Ответ:**
    Да, является. Если появится ошибка, не прописано как его обрабатывать.

51. Является ли данный код антипаттерном?
    Обоснуйте ответ.
    try {
    …
    }  catch (SomeException е) {
    System.out.println(“Something went wrong!”);
    }
**Ответ:**
    Да является. Требуется боллее точно описать проблему, которую прехватило исключение.

52. Является ли данный код антипаттерном, если блок catch находится не в конце раннер-метода main()?
    Обоснуйте ответ.
    try {
    …
    }  catch (Exception е) {
    …
    }
    …
или другой вариант
try {
…
}  catch (Throwable е) {
…
}
…

53. Является ли данный код антипаттерном?
    Обоснуйте ответ.
    try {
    int i = 0;
    while(true) {
    а[i++].f();
    }
    } catch(ArraylndexOutOfBoundsException е) {
    …
    }
**Ответ:** 
    ArraylndexOutOfBoundsException – это ошибка индекса массива, находящегося вне границ. В коде не прописано, где может возникнуть ошибка и массив увеличивается до максимального значения i.

54. Есть ли недостатки у API  написанного только с использованием обрабатываемых исключений?
**Ответ:**
    При нечастом использовании проверяемые исключения могут повысить надежность программ. При злоупотреблении они делают использование API болезненным. Если вызывающий код не в состоянии восстановиться после сбоя, генерируйте непроверяемые исключения. Если восстановление возможно и вы хотите заставить пользователей обрабатывать исключительные ситуации.
**Источник.** [Джошуа Блох, Джава эффективное программирование, 3-е издание, Статья Избегайте ненужных проверяемых исключений]

55. Даны два варианта сеттера.
    Какой является более предпочтительным в использовании?
    Обоснуйте ответ.
    Вариант 1.
    void setPositiveValue(int value) {
    if(value <= 0) {
    throw new IllegalArgumentException(...);
    }
    this.value = value;
    }
    Вариант 2.
    void setPositiveValue(int value) throws SomeCheckedException {
    if(value <= 0) {
    throw new SomeCheckedException(...);
    }
    this.value = value;
    }
**Ответ:**
    Рекомендуется не злоупотреблять проверяемыми исключениями. IllegalArgumentException используется при вызове метода использован незаконный аргумент. Он может использоваться, когда в сетере будет отрицательное значение.

56. Приведите пример наиболее распространенных из повторно используемых исключений и причины их применения.
**Ответ:**
    Иногда вам может понадобиться заново возбудить уже перехваченное исключение, что особенно вероятно при использовании класса Exception для перехвата любого исключения. Так как вы уже получили ссылку на это исключение, вы его попросту возбуждаете еще раз
**Источник.** [Брюс Эккель, Философия Java, 4-ое полное издание, стр. 379]

57. Если недостаточно информации для принятия решения и...
1)     исключительная ситуация должна быть исправлена на ближайшем уровне;
2)     исключительная ситуация маловероятна
Экземпляры подклассов каких типов исключений целесообразно сгенерировать в каждом случае?

58. Выделите в блоке try-catch основной и альтернативный сценарии.
    Обоснуйте ответ.
    try {
    ...
    User user = source.getUser(login, password);
    if(GUEST_USER.equals(user) {
    …
    } else {
    …
    }
    ...
    }  catch (SourceException е) {
    …
    }
    class Source {
    public User getUser(String login, String password) throws SourceException {
    ...
    throw new SourceException(...);
    ...
    return GUEST_USER;	//wrong login or password
    ...
    return new User(...);
    }
    ...
    }

59. Перепишите код предыдущего задания с условием, что ввод неправильных логина или пароля является альтернативным сценарием.

60. Что такое трансляция исключения, когда ее используют и какие правила ее использования? Приведите пример трансляции исключения.

61. Как можно избежать использования трансляций и зачем нужно это предпринимать?

62. В каких случаях надо предпочесть сцепление трансляции?

63. Можно ли для исключительной ситуации определить, класс, который не является подклассом Exception, RuntimeException, Error.
    Если да, то как он будет себя проявлять (как checked-exception или как unchecked-exception)?

64. Обязательно ли информацию об исключительное ситуации представлять строковым полем?
    Если нет, то какой альтернативный способ создания строкового представления исключения?

65. Если метод завершается сбоем, что нужно сделать с объектом, на котором был вызван этот метод?

66. Приведите способы достижения атомарности по отношению к сбоям.

67. Приведите пример, когда отсутствие транзакционности в исключениях, приводит к сохранению ссылки на объект в неверном состоянии.

68. Необходимо создать коллекцию из результатов тестов, находящихся в валидном файле src/in.csv.
    Пример файла
    cool;75;90
    clever;68;95
    looser;30;48
    Является ли код, реализующий задание, антипаттерном?
    Обоснуйте ответ.

public class Runner {
public static void main(String[] args) {
List<Trial> trials = new ArrayList<Trial>();
try(Scanner sc = new Scanner(new FileReader("src/in.csv"))) {
while(sc.hasNext()) {
Trial trial = getTrial(sc);
trials.add(trial);
}
printTrials(trials);
} catch (FileNotFoundException e) {
System.out.println(Constants.ERROR_FILE_FOUND);
}
}
private static Trial getTrial(Scanner sc) {
String csvLine = sc.nextLine();
String[] values = csvLine.split(Constants.DELIMETER);   	
try {
String name = values[Constants.NAME_INDEX];
int mark1 = Integer.parseInt(values[Constants.MARK1_INDEX]);
int mark2 = Integer.parseInt(values[Constants.MARK2_INDEX]);
return new Trial(name, mark1, mark2);
} catch (CsvLineException e) {
System.out.println(Constants.ERROR_WRONG_DATA);
}
}

69. Приведите пример кода собственного исключения (реализация в одном классе всего нижеперечисленного). Класс исключения содержит:
-         поле, которым является неправильная строка, считанная из файла (имя csvLine);
-         конструктор по умолчанию, вызывающий конструктор суперкласса;
-         параметризованный конструктор, принимающий экземпляр исключения и неправильную строку, считанную из файла;
-         параметризованный конструктор, принимающий строку с указанием причины исключения и  неправильную строку, считанную из файла;
-         геттер с возвратом неправильной строки;
-         переопределенного метода toString с указанием неправильной строки и метода вывода сообщения об ошибки.
**Ответ:**
package by.gsu.epamlab.exceptions;
import by.gsu.epamlab.constants.Constants;
public class CsvLineException extends Exception {
private String csvLine;
private String message;
    public CsvLineException() {
        super();
    }
    public CsvLineException(String message, Throwable cause, String csvLine) {
        super(message, cause);
        this.csvLine = csvLine;
    }
    public CsvLineException(String csvLine, String message) {
        this.csvLine = csvLine;
        this.message = message;
    }
    public String getCsvLine() {
        return csvLine;
    }
    @Override
    public String toString() {
        return csvLine + Constants.HYPHEN + message;
    }
}

70. Необходимо создать метод для экспорта csv-файла в коллекцию.
    При наличии хотя бы одной ошибки в исходных данных “отменить” создание
    коллекции.
    Какие антипаттерны содержит следующий код?
    Предложите варианты по избавлению от них.
    private static List<Trial> getTrials(Scanner sc) {
    List<Trial> trials = new ArrayList<Trial>();
    try {
    while(sc.hasNext()) {
    Trial trial = getTrial(sc);
    trials.add(trial);
    }
    } catch (CsvLineException e) {
    System.err.println(e);
    }
    return trials;
    }

72. Создать метод для экспорта данных в коллекцию из последовательного источника экземпляров Trial.
    См. код ниже.
    Его необходимо дополнить, чтобы происходила обработка следующих исключительных ситуаций:
1. 	Файл не найден.
2. 	Ошибка в csv строке.
      Примечание: код не должен нарушать принцип “верхние уровни приложения должны перехватывать исключения нижних уровней и, в свою очередь, генерировать исключения, которые можно пояснить в терминах абстракции верхнего уровня”
      См. Блох, Д. Java эффективное программирование. 3-е издание. Глава 10 Исключения. Стр 370.
      Считается, что классы для исключений созданы и имеют необходимый функционал.
      Подсказка:
---
Надо использовать два исключения. Одно из которых будет нижнего уровня, другое верхнего уровня.
---
Еще одна подсказка:
---
Одно из исключений обрабатываемое, другое нет.
---

//начало кода, реализующего задание
//---
interface TrialProvidable {
boolean hasTrial();
Trial getTrial();
}

public class TrialCsvImpl implements TrialProvidable {
private Scanner sc;
public CsvImpl(String csvName) {            	
sc = new Scanner(new FileReader(csvName));
}
public boolean hasTrial() {             	
return sc.hasNextLine();
}
public Trial getTrial() {
// get Trial instance from csv line
return trial;
}
}

public class Runner {
private static List<Trial> getTrials(TrialProvidable trialProvider) {
List<Trial> trials = new ArrayList<Trial>();
while(trialProvider.hasTrial()) {
Trial trial = trialProvider.getTrial();
trials.add(trial);
}
return trials;
}

public static void main(String[] args) {
TrialProvidable trialProvider = null;
try {
if("csv".equals(args[0])) {
trialProvider = new TrialCsvImpl("src/in.csv");
} else {
trialProvider = new TrialDBImpl();
}
List<Trial> trials = getTrials(trialProvider);
…
} finally {
if (trialProvider != null) {
trialProvider.close();
}
}
}
}
//---
//конец кода, реализующего задание

