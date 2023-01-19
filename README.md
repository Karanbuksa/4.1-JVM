
# 4.1.2 Исследование JVM через VisualVM
## Задача

Изучить использование памяти через VisualVM при загрузке новых классов и создании новых объектов

## Выполнение

### Лог консоли
02:29:20.911: loading io.vertx  
02:29:21.262: loaded 529 classes  
02:29:24.275: loading io.netty  
02:29:24.927: loaded 2117 classes  
02:29:27.938: loading org.springframework  
02:29:28.168: loaded 869 classes  
02:29:31.168: now see heap  
02:29:31.168: creating 5000000 objects  
02:29:32.665: created  
02:29:35.676: creating 5000000 objects  
02:29:41.045: created  
02:29:44.069: creating 5000000 objects  
02:29:48.826: created  

### Classes и Metaspace
В лекции рассказывалось, что классы загружаются в Metaspace. Благодаря VisualVM явно видно корреляцию графиков Metaspace и Classes. Каждый раз, когда загружается какой-либо пакет, в Metaspace загружаются классы из этого пакета. 
![img](https://i.ibb.co/Fb4YDvc/4-1-2-0jpg.jpg)  

### Heap
Когда создаётся экземпляр класса, он отправляется в Heap. На графиках VisualVM видно, что при создании объектов в Heap'е заполняется и выделяется больше памяти.  
![img](https://i.ibb.co/J2q4g8k/4-1-2-1jpg.jpg)  
 Что интересно: заполнение памяти - процесс экспаненциальный, а выделение памяти - аппериодический (с института глаз натренирован видеть их, у процесса выделения памяти есть даже характерное перерегулирование в конце).  
![img](https://i.ibb.co/kyTrvj5/image.png)




