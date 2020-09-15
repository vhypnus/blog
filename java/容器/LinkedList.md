### 概述

- 单向链表
- 适合随机删除、插入场景

```
+-------+      +-------+              +-------+      
| first | ---> |  next | ---> ...---> | last  |
+-------+      +-------+              +-------+
```

**优势**

- 频繁新增，删除时性能较好，无需扩容移动数据

**劣势**

- 需要额外的空间

### 源码分析

关键属性定义

```java
transient int size = 0;

transient Node<E> first;

transient Node<E> last;

// 统计次数
protected transient int modCount = 0;

//-------------------Node 定义------------------------
private static class Node<E> {
    E item;
    // 单向：前驱 --> 后驱，双向：后驱 <--> 前驱
    Node<E> next;
    Node<E> prev;

    Node(Node<E> prev, E element, Node<E> next) {
        this.item = element;
        this.next = next;
        this.prev = prev;
    }
}
```



**新增**

```java
public boolean add(E e) {
    // 添加在最后
    linkLast(e);
    return true;
}


void linkLast(E e) {
    final Node<E> l = last;
    final Node<E> newNode = new Node<>(l, e, null);
    last = newNode;
    if (l == null)
        first = newNode;
    else
        l.next = newNode;
    size++;
    modCount++;
}
```

**获取第一个元素并删除**

```java
public E pollFirst() {
    final Node<E> f = first;
    return (f == null) ? null : unlinkFirst(f);
}

private E unlinkFirst(Node<E> f) {
    // assert f == first && f != null;
    final E element = f.item;
    final Node<E> next = f.next;
    f.item = null;
    // 不处理，first有可能不会被回收 
    f.next = null; // help GC
    
    //
    first = next;
    if (next == null)
        last = null;
    else
        next.prev = null;
    size--;
    modCount++;
    return element;
}
```





