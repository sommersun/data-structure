# c++ STL 容器、迭代器、配接器、算法、空间配置器、仿函数
1. Vector : 动态数组 成倍扩容 随机访问   
迭代器begin 返回第一个元素的位置，end返回最后一个元素的后面的位置 迭代器可能失效：新空间扩容机制  
vector中erase方法真正删除了元素，迭代器不能访问了  
ralgorithn中的remove只是简单地将元素移到了容器的最后面，迭代器还是可以访问到。因为algorithm通过迭代器进行操作，不知道容器的内部结构，所以无法进行真正的删除。   
2. List ：双向链表 节点地址不连续 插入高效    
List::sort类似merge sort nlogn   
3. deque: 双向开口的连续线性空间 没有空间保留
deque采用一块map（不是STL的map容器）作为主控，其为一小块连续空间，其中每个元素都是指针，指向另一段较大的连续空间（缓冲区）。  
迭代器失效  
4. queue: 除了头部外，没有其他方法存取deque的其他元素。    
5. stack: 由deque实现  
6. heap: 一棵完全二叉树的数组对象。层次遍历顺序    
7. map： 由红黑树实现 查找时间logn  
没有空间预留 （分配器变化）  
AVL树为了维护平衡要不断调整，付出了更多的代价；而红黑树并不是一味追求平衡因子为1的平衡，而是近似平衡，因此在插入删除时会减少大量左旋右旋操作，性能更加稳定  
8. set: 其键值就是实值。红黑树  
9. hash_map: 查找时间 常数级 但hash function较耗时  
10. hash_set:   
11. new不仅可以开辟内存，还自动调用构造函数构造对象；delete要先析构对象，然后紧接着释放内存。空间配置器的核心功能就是把对象的内存开辟和对象构造的过程分解开，对象析构和内存释放的过程分解开。Allocate 开辟内存、deallocate 释放内存、construct 构造、destroy 析构  
12. 迭代器：顺序访问一个聚合对象中各个元素, 而又不需暴露该对象的内部表示  
