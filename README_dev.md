
# 本文档说明
- 暂且将项目readme文件作为主要更新功能日志，置于主页方便查看阅读
- 建议仓库成员定期查看，并结合代码理解，方便后期的调试工作
- 重要提醒也会置于此地

# 重要提醒
- 本仓库文件目录已于3.11规模重构，请查阅日志
- 三个链表的基本操作亟需测试!
- 本仓库文件目录已于3.16小规模重构，请查阅日志
- 3.16更新内容较多并包含复杂嵌套和goto，请仓库成员仔细查阅本日志，并拉取master分支在本地测试！
- 4.3更新了新的页面，请自行测试

# TODO-LIST
- 为界面不同货币添加汇率转换

# 更新日志
----------
## 3.10如下更新：
1. 新增buildRecordChain函数，双向链表，做了简单的测试
2. 对RecordChain.h声明的函数添加了较为详实的注释说明
3. 重构了StdCheck中所有的函数，取消了传入字符串之后再传入的len参数
4. 将字符串相似函数做成单独的头文件和源码StrSimilar，因为目前找不到合适的头文件来放
5. 新增了获取系统时间的功能，用以丰富一条销售记录的信息
6. 整理了若干文件目录，新增了日志

## 3.11如下更新：
1. 重构了master分支的文件目录，细则如下
    - 精简掉了所有cmake中间文件和makefile文件，只保留makelist
    - 精简掉了本地测试的中间文件和代码
2. 维护了gitignore文件

## 3.14如下更新：
1. 将链表节点的定义从源文件迁至头文件，以解决在主函数内访问其成员的问题
2. 将RecordChain的基本结构和操作推广至ClientChain和CommodityChain
3. 重构了文件目录，将链表相关的文件打包进文件夹ChainH和ChainC
4. 做了简单的测试

## 3.16如下更新：
1. 在文件系统里新增了Page系列，用以维护不同页面，我们的页面基本逻辑如下：
    - 进入程序经过登录后是Welcome页面，Welcome页面下三个页面
        - Record
            - 内有对销售记录的增删查改操作
        - Client
            - 内有对客户的增删查改操作
        - Commodity
            - 内有对商品的增删查改操作
    - 这三个页面不能互相跳转，以降低goto使用风险
    - 页面内的分页面如有必要，使用goto跳转来减少过多的if-else嵌套
2. 维护了WelcomePage和RecordPage的基本操作
3. 在主函数里新增了一些goto标签，慎用！慎用！慎用goto！
4. 新增计划：用extern声明变量代替Chains系列函数形参的对指针的指针，现在认为后者对理解代码有一定障碍

## 3.22如下更新：
1. 维护了main.c的主界面，record相关界面
2. **[重要]为recordChain相关操作加上了文件功能，现在初始数据从文件读入**
3. recordNode新增一个bool量isSoldOut，来区分进出货
4. 增加了程序打开时的备份功能
5. 新增chainopt文件，内涵两个操作，程序最开始的备份和最后结束的释放内存

## 3.23如下更新：
1. 完善addRecord函数操作
2. 新增Record页面中的模糊搜索功能
3. 重构StdCheck文件为InputCheck
4. 新增ClientPage，并做了简单测试
5. 修复若干BUG

## 3.25更新
- **登录界面可以使用了，但还需数据测试**
- 将登录界面的字符显示与其他界面统一
- 将md5加密结合登录界面
- 密码文件路径更改，并适应backupAll函数
- 新增浮点数检测，字符串转浮点数功能
- 对一些不规范的代码格式进行排版
- 修复了内存泄露的BUG

## 3.29更新
- 新增购物车链表
-  新增客户等级功能，是static变量
-  小规模重构主函数
-  ClientChainNode新增用以判断顾客和进货商的bool变量
-  welcomepage重做

## 3.30更新
- 将注册操作和client链表连接，现在新注册的用户可以直接在client中查询
- 完成用户界面的显示输出
- 将record链表的增删操作与commodity链表连接，现在commodity中的库存由record决定
- 完成总览界面，并将其融入到管理员界面

## 4.3更新
- 用户浏览商品页面完成
- 用户购物车操作完成
- 测试用用户账户密码均为client

## 4.5更新
- 现在购物车添加到record后可以改变commodity的库存
- 修改了record中删除操作

## 4.6更新
- 增添测试数据
- 增加管理员修改用户等级的功能
- 修改极端盈亏的显示

## 4.11更新
- 增加五次输入密码错误后锁住用户的功能

## 4.13更新
- 修改三个链表释放操作