
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
![img](https://i.ibb.co/wRwnzwX/JVM-0.jpg)
![img](https://i.ibb.co/yQStwWW/JVM-1.jpg)
![img](https://i.ibb.co/zrpy888/JVM-2.jpg)
![img](https://i.ibb.co/L6yZq5s/JVM-3.jpg)
![img](https://i.ibb.co/wYkXvBw/JVM-4.jpg)
![img](https://i.ibb.co/smjsm3G/JVM-5.jpg)
![img](https://i.ibb.co/7YPdhxX/JVM-6.jpg)
![img](https://i.ibb.co/FJbB0M6/JVM-7.jpg)
![img](https://i.ibb.co/7z3LWsK/JVM-8.jpg)
![img](https://i.ibb.co/M7zQm2Q/JVM-9.jpg)
![img](https://i.ibb.co/b22t5FX/JVM-10.jpg)
![img]https://i.ibb.co/KrKv8M4/JVM-11.jpg)
![img](https://i.ibb.co/R7SqQC3/JVM-12.jpg)
- сборщик мусора


