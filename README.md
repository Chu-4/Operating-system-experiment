模拟单用户多任务操作系统的软件程序，通过5个互相关联的模块模拟进程管理、存储管理、设备管理和文件管理四部分的主要内容<br>
*详细见实验大纲

### 进程模拟

创建→新建进程依次进入等待队列<br>
运行→等待队列中第一个进程弹出，进入运行队列，当运行队列中已有进程时，再点击运行，运行队列中进程弹出运行队列，进入等待队列队尾，等待队列队首进程进入运行队列<br>
阻塞→判断运行队列中是否有进程，如果没有则提示。如果有，将进程弹出运行队列，进入阻塞队列，运行队列为空<br>
唤醒→判断阻塞队列中是否有进程，如果没有则提示。如果有，进程弹出阻塞队列，进入等待队列队尾<br>
结束→判断运行队列中是否有进程，如果没有则提示，如果有，将进程从运行队列中移除，该进程离开当前环境<br>

### 分页式存储管理

位示图模拟内存分配情况，位数和物理块个数相同，初始化时随机占用部分内存，位示图中1为已占用，0为未占用可分配。<br>
块大小设定为1k，由进程大小判断该进程占用的内存块数量<br>
逻辑地址转为物理地址，输入16进制地址，计算占用物理块在内存中位置，位置x1024+偏移量=物理地址，释放内存时，占用位由1变回0<br>
页面置换<br>
FIFO：如果内存内有调用页，队列不变，如果没有，则移除最早进入的底部页<br>
LRU：如果内存内有调用页，页面如果调用就将该页置于顶部，队列改变，如果没有，将最久没有调用的底部页移除<br>
缺页率=页面从外面调入的次数/页面访问总次数（从外调入次数+访问内存次数）

### 设备管理

添加设备、控制器以及通道的时候要注明添加到哪个设备、控制器以及通道下，否则无法确定。<br>
申请时判断该设备、控制器以及通道链是否全部空闲，如果全部空闲，可以分配，如果有任一被占用，则不可以分配，申请进入等待队列等待之前的占用释放后，才可以分配

### 文件管理

MD（创建子目录）：创建目录文件，并在父目录文件中增加目录项。<br>
CD（切换工作目录）：根据当前目录切换到指定目录。<br>
RD（删除子目录）：搜索所要删除的目录是否为空目录，若是则删除。<br>
MK（创建空文件）：创建指定大小的文件，并在父目录中添加文件名称；还应对FAT表进行适当修改。<br>
DEL（删除文件）：如果所要删除的文件存在，则删除，同时修改父目录内容；还应对FAT表进行适当修改。<br>
DIR：列出当前目录的所有目录项。<br>

### 进程调度

程序开始运行时选择调度算法，创建进程时输入进程所需服务时间以及到达时间。<br>
FCFS:根据进程请求的先后次序进行调度<br>
SJF(短作业优先)：根据进程运行时间长短进行调度，运行时间短的先运行<br>
RR(时间片轮转)：设定时间片长度，根据请求先后每个进程都运行一个时间片长度的时间，一个时间片内没有完成运行的进程，返回到绪队列末尾重新排队，等待下一次调度。<br>
【针对单个进程↓】<br>
周转时间=完成时间-到达时间<br>
带权周转时间=周转时间/实际运行时间(不包括等待时间)<br>
【针对整体↓】<br>
平均周转时间=总周转时间(所有进程周转时间之和)/进程个数<br>
平均带权周转时间=总带权周转时间(所有进程带权周转时间之和)/进程个数
