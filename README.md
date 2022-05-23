## Thoughts on C Pointers
- 主要思想参考:https://blog.csdn.net/qq_21583681/article/details/78572009#commentBox

>> static char content[] ="Listen to me say thanks\n";

>>> (1) printf("%ld\n",content);//4227088 可以理解
    
>>> (2)  cout<<content<<endl;//Listen to me say thanks 认为是cout区别于printf的特性，cout直接输出值https://blog.csdn.net/yangyong0717/article/details/78173618
    
>>> (3)  printf("%c\n",*content);//L 可以理解
    
>>> (4) cout<<*content<<endl;//L 可以理解
    
>>> (5) printf("%ld\n",&content);//4227088 和直接输出content一样 printf("%ld\n",content);//4227088  
根据第一个url描述，是否可以理解为，由于指针就是为了指示其他变量，而且我没有找到指针本身的地址怎么获得，编译器把&一个指针符号等价于指针符号，（&content（5）和content（1）都表示指向的那个地址）
    
>>> (6) cout<<&content<<endl;//0x403010 4227088的16进制，不一样的话是每次调用不同导致的，我每次只运行了一行代码
    
>>> (7）printf("%ld\n",*&content);//4227088 这是为什么？*被忽略了，编译器特性？
    
>>> (8）cout<<*&content<<endl;//Listen to me say thanks cout特性 &*抵消，因此（2，8，10一样？）
    
>>> (9） printf("%ld\n",&*content);//4227088 可以理解 *先是char变量的值，然后&为地址

>>> (10）  cout<<&*content<<endl;//Listen to me say thanks cout特性 &*抵消，因此（2，8，10一样？）

其实感觉&和\*加一起没啥意思，本身指针就是地址，他的用处就是要么得到引用的那个变量的地址(&)或者值(*)
见：https://github.com/wufei-png/linux_kernel_memory_management/blob/master/src/mtest.c#L96
