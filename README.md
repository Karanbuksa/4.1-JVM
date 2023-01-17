
# 4.1.1 Понимание JVM
## Задача

Описать каждую строку с точки зрения происходящего в JVM
## Код для исследования
```java
public class JvmComprehension {
    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }
    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
}
```

## Выполнение

### ClassLoader'ы
После компиляции файла с разрешением .java в байткод JVM нужно узнать, какие классы использовались при написании программы, чтобы корректно загрузить их.
Данная задача выполняется ClassLoader'ами. За все классы, которые написал программист отвечает Application ClassLoader. В нашем случае он будет отвечать 
за класс JvmComprehension. В целях безопасности Application ClassLoader не может работать один. За классы платформы, относящиеся к пакету java.util,
отвечает Platform ClassLoader. В нашей программе классов из этого пакета я не заметил. За классы Java Core, то есть классы пакета java кроме java.util 
отвечает Bootstrap ClassLoader. Такими в нашей программе являются System, Object и Integer. Bootstrap ClassLoader загрузит System, Object и Integer, передаст команду
Platform ClassLoader'у, он ничего не загрузит, передаст команду Application ClassLoader, который загрузит JvmComprehension.

### Области памяти (стэк (и его фреймы), хип, метаспейс) 
По аналогии с лекцией
[](https://prnt.sc/jxwAcpFO_m8Y)
- сборщик мусора


