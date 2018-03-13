# Algorithm exercise(算法练习)

---

## PAT乙级真题选做：

### 1001 - 害死人不偿命的(3n+1)猜想(15)

对应"(3n+1) - first"

### 1002 - 写出这个数（20）

对应"write-the-world"（大概是起名字的时候脑子Bug了...

### 1003 - 我要通过！（20）

在[柳婼](https://www.liuchuo.net/archives/460)给出的题解中，寻找到题目生成的规律来简化问题。我的第一个反应就是根据表达式生成，在字符串长度100以内存在哪些式子，然后再进行匹配。

对应"want-to-pass"

### 1004 - 成绩排名（20）

简单的比一下最大最小值，对应"grades-rank"

### 1005 - 继续(3n+1)猜想（25）

[柳婼](https://www.liuchuo.net/archives/455)的题解中，是利用一个arr作为标记，将验证过的数字标记为1，最后把arr=0的数字输出出来。

我这里是用两个`set`，取一个差集得到没有验证过的数字。

###1006 - 换个格式输出整数 （15）

对应"change-print-format"

### 1007 - 素数对猜想（20）

对应"prime-pair"

### 1008 - 数组元素循环右移问题 （20）

对于这种问题，没必要完全模拟。这里利用三次反转进行。

```C++
	reverse(nums.begin(), nums.end());
	reverse(nums.begin(), nums.begin()+m);
	reverse(nums.begin() + m, nums.end());
```

### 1009 - 说反话（20）

可以使用`reverse`函数，也可以用栈。

```C++
stack<string> v;
v.push(s);
cout << v.top();
v.pop();
```

### 1010 - 一元多项式求导

这里要注意，当没有输出的时候，要输出"0 0"才可以。

另外，这种问题中，可以即时输入/输出的。

### 1011 - A+B和C（15）

### 1012 - 数字分类（20）

根据不同要求对数字进行分类。

### 1013 - 数素数（20）

### 1014 - 福尔摩斯的约会（20）

找到对应字符以后进行判断即可。注意最后输出的时候要前面加0补位。


### 1015 - 德才论（25）

这里没有AC，主要问题是超时。

因为对不同人的分类是在一个结构体中用`state`变量表示，在排序的时候采取的是所有人的排序，就会超时。

应该对不同`state`的人分别排序，然后再按照`state`进行输出，比如可以用`vector<node> v[4]`这样的`vector`数组。

### 1016 - 部分A+B

遍历一下字符串，再乘十计算就可以了。

### 1017 - A除以B（20）

手动模拟除法，难度不大。

### 1018 - 锤子剪刀布 （20）

问题不大，这里用了`map`来记录，没有发现`map`可以直接比较大小的，只封装了一个函数来做。

### 1019 - 数字黑洞（20）

这道题我是对每一位进行处理，但是看[柳婼的题解](https://www.liuchuo.net/archives/541)可以输入`string`然后利用`sort`调整位置。在对于位数较多的时候，`sort`是个比较好的方法。

### 1020 - 月饼（25）

一个规划的问题，但题目内容很简单，只要注意到浮点数和位数问题就不大了。

### 1021 - 个位数统计（15）

从开始遍历一遍即可。

### 1022 - D进制的A+B（20）

和后面的比，这个就太容易了

### 1023 - 组个最小数（20）

先找到最小的不为零的数作为第一个数字，其余数字升序排列即可。这里有一个可以加速的地方，当已知位置t之前没有合适的数字了，可以直接跳过这些进行输出。

### 1024 - 科学计数法（20）

我这里是用字符串进行处理的，把几个部分分开，然后再合并在一起。更多的是纯字符串的处理，没有过多用数学的办法。

### 1025 - 反转链表（25）

【感觉是目前，乙级真题中最复杂的一个了】

**关键是要知道`<algorithm>`中有一个`reverse`函数**。

这里借鉴[柳婼小姐姐](https://www.liuchuo.net/archives/463)的思路：

*注意，不是所有的元素都有用*

所以输入以后，需要`sum`统计一下有多少在链表中的元素。

接下来把链表按照顺序存入一个list中，但是实际上，对于这道题而言并不需要修改链表的`next`指针，只需要在输出的时候，输出`list[i+1]`就可以了。

利用`reverse`就可以反转链表，判断条件`sum`上需要去掉不能整除的部分：

```C++
for (int i = 0; i < (sum - sum % k); i += k)
        reverse(begin(list) + i, begin(list) + i + k);
```

### 1026 - 程序运行时间（15）

类比`clock()`函数进行计算，主要就是进位的问题。

### 1027 - 打印沙漏（20）

注意，这个沙漏！右面不能有空格。

这里使用了`string`的一种定义方法产生相同的字符串：

```C++
string stars(num, symbol);
```

### 1028 - 人口普查（20）

只要判断好时间界限，问题就比较容易啦~

### 1029 - 旧键盘（20） 

【参考[柳婼小姐姐的题解](https://www.liuchuo.net/archives/559)比较好~

```C++
#include <iostream>
#include <cctype>
using namespace std;
int main() {
    string s1, s2, ans;
    cin >> s1 >> s2;
    for (int i = 0; i < s1.length(); i++)
        if (s2.find(s1[i]) == string::npos && ans.find(toupper(s1[i])) == string::npos)
            ans += toupper(s1[i]);
    cout << ans;
    return 0;
}
```

后面有一道题目比这个还要复杂一些。

### 1030 - 完美数列（25）

排个序，问题就很容易解决啦~

### 1031 - 查验身份证（15）

其实还挺有用的:)

字符串处理一下，记得最后的对应关系就可以啦~

### 1032 - 挖掘机技术哪家强（20）

用个`vector`存一下就好啦

### 1033 - 旧键盘打字（20）

承接`1029`题目，多加了一些错误的情况。

```C++
#include <iostream>
#include <cctype>
using namespace std;
int main() {
  string bad, should;
  getline(cin, bad);  //为了防止第一行是空的，不能用cin >> ,用getline(cin, ...)
  getline(cin, should);
  for (int i = 0, length = should.length(); i < length; i++) {
    if (bad.find(toupper(should[i])) != string::npos) continue;//如果字母有错误的话
    if (isupper(should[i]) && bad.find('+') != string::npos) continue;//如果输出应该是大写字母，但是上档坏掉了
    cout << should[i];
  }
  return 0;
}
```

### 1034 - 有理数四则运算（20）

【这道题有一些麻烦，因为涉及到分数的四则运算，四种运算都需要写出来。

我的思路是建一个结构体用来存储，同时有化简分数、带分数化成假分数的函数。在结构体外重构了加减乘除的运算，同时实现了通分的操作。

这样是先化简再进行通分，最后再根据结果要求调整格式。

### 1035 - 插入与归并（25） important

判断当前的序列是处于插入排序还是归并排序，二者的主要区别是在经过前面的一段有序队列后，剩余的队列是否有序。

先用一个指针`i`找到从头开始最后一个排好序的位置，注意这里的限定条件要到`n-1`，因为判断的时候会用到`i+1`。

接下来用指针`j`从`i+1`的位置开始寻找第一个不满足`a[j]==b[j]`，如果`j`能够到结尾，就说明是插入排序。`j`的判断是寻找后面有没有变动，如果都没变动，就判断是插入排序。

模拟递归排序的过程：

```C++
cout << "Merge Sort" << endl;
int k = 1, flag = 1;
while(flag) {
    flag = 0;
    for (i = 0; i < n; i++) {
        if (a[i] != b[i])
            flag = 1;
    }
    k = k * 2;
    for (i = 0; i < n / k; i++)
        sort(a + i * k, a + (i + 1) * k);
    sort(a + n / k * k, a + n);
```

注意，最后一句的`sort`是为了处理剩余的内容，由于是正整数，所以$n/k\times k \neq n $

### 1036 - 跟奥巴马一起编程（15）

那就编呗-。-期待以后还有川普的

### 1037 - 在霍格沃茨找零钱（20）

就是一个进制的问题，盘算一下就好啦

### 1038 - 统计同成绩学生（20） 

可以用一个数组，也可以用一个`map`来记录数字。

### 1039 - 到底买不买（20）

第一直觉是用`map`来解决，然后每一项进行对比。

也可以用两个数组来搞定，遇到相同的就“消消乐”变成'#'，然后再统计其他的数量。

### 1040 - 有几个PAT（25）

首先来一段柳婼同学活泼的分析：

> 要想知道构成多少个PAT，那么遍历字符串后对于每一A，它前面的P的个数和它后面的T的个数的乘积就是能构成的PAT的个数。然后把对于每一个A的结果相加即可\~~辣么就简单啦，只需要先遍历字符串数一数有多少个T\~~然后每遇到一个T呢~countt–;每遇到一个P呢，countp++;然后一遇到字母A呢就countt \* countp\~\~~把这个结果累加到result中\~~\~~最后输出结果就好啦\~~对了别忘记要对10000000007取余哦\~~\~~

这种问题最好抽象出数学规律~这样会极大降低计算的难度的。本来想用三层循环来模拟，暴力的求解，结果超时了...

### 1041 - 考试座位号（15）

一个搜索的问题，后面用试机位置号，那前面的标记也是用试机来做。

### 1042 - 字符统计（20）

注意**包含空格**，所以不能用`cin >>`

统计的内容只包括英文字母，所以只需要一个长度为26的数组来保存。

### 1043 - 输出PATest（20）

整理现有的字母然后输出。

### 1044 - 火星数字（20）

进制转换问题的基础上又加了一些新的内容，将火星人的两位用不同的表示。

就是处理的时候，稍微麻烦了一些，难度还好。

### 1045 - 快速排序（25）

如果重复遍历，很容易超时。就用空间来换取时间，定义一个`max`和一个`min`的数组，分别存储由前到后和由后到前的最大最小值。最后再遍历一遍和前后的最大最小值比较一下就可以啦~

而[柳婼小姐姐](https://www.liuchuo.net/archives/505)的思路是先整体排序，如果**当前元素没有变化**而且**它左边的所有值的最大值都比它小**的时候，它就可能是主元。

### 1046 - 划拳（15）

简单算一下就好啦~

（不过划拳这么麻烦呀...感觉会懵的hh

### 1047 - 编程团体赛（20）

记录一下参赛的队伍就可以啦~

### 1048 - 数字加密（20） 

这里需要注意两个数字位数不一样的情况，如果A比B长，就把B前面补零补齐。

### 1049 - 数列的片段和（20）

注意是`double`就可以啦~

### 1050 - 螺旋矩阵（25)

这个似乎是一次期末考试的题目，思路也比较清晰，但是要注意各种边界情况。在计算范围的时候，也要格外小心，是谁减一的问题。





### 韩信点兵/中国剩余定理 - Hanxin-CRT

相传韩信才智过人，从不直接清点自己军队的人数，只要让士兵先后以三人一排、五人
一排、七人一排地变换队形，而他每次只掠一眼队伍的排尾就知道总人数了。输入包含多组
数据，每组数据包含3个非负整数a，b，c，表示每种队形排尾的人数（a＜3，b＜5，c＜
7），输出总人数的最小值（或报告无解）。已知总人数不小于10，不超过100。

### "猜数字"游戏 - master-mind hints UVa 340

实现一个经典"猜数字"游戏。给定答案序列和用户猜的序列，统计有多少数字位置正确
（A），有多少数字在两个序列都出现过但位置不对（B）。
输入包含多组数据。每组输入第一行为序列长度n，第二行是答案序列，接下来是若干
猜测序列。猜测序列全0时该组数据结束。n=0时输入结束。

### 三位数字排序问题 - three-number-permutation

用1，2，3，…，9组成3个三位数abc，def和ghi，每个数字恰好使用一次，要
求abc：def：ghi＝1：2：3。按照“abc def ghi”的格式输出所有解，每行一个解。提示：不必
太动脑筋。

### 安迪的第一个字典（Andy's First Dictionary，Uva 10815）- get-all-words

输入一个文本，找出所有不同的单词（连续的字母序列），按字典序从小到大输出。单词不区分大小写。

### 最小生成元 - Digit-Generator

如果x加上x的各个数字之和得到y，就说x是y的生成元。给出n（1≤n≤100000），求最小生成元。无解输出0。例如，n=216，121，2005时的解分别为198，0，1979。

### 分子量的计算 - Molar-Mass

分子量（Molar Mass, ACM/ICPC Seoul 2007, UVa1586）给出一种物质的分子式（不带括号），求分子量。本题中的分子式只包含4种原子，分别为C, H, O, N，原子量分别为12.01, 1.008, 16.00, 14.01（单位：g/mol）。例如，C6H5OH的分子量为94.108g/mol。

### 环形队列最小表示 - Circular-Sequence

长度为n的环状串有n种表示法，分别为从某
个位置开始顺时针得到。例如，图3-4的环状串
有10种表示：
CGAGTCAGCT，GAGTCAGCTC，AGTCAGCTCG等。在这些表示法中，字典序最小的称
为"最小表示"。
输入一个长度为n（n≤100）的环状DNA串（只包含A、C、G、T这4种字符）的一种表
示法，你的任务是输出该环状串的最小表示。例如，CTCC的最小表示是
CCCT，CGAGTCAGCT的最小表示为AGCTCGAGTC。

#### 反片语（Ananagrams，Uva 156）

输入一些单词，找出所有满足如下条件的单词：该单词不能通过字母重排，得到输入文
本中的另外一个单词。在判断是否满足条件时，字母不分大小写，但在输出时应保留输入中
的大小写，按字典序进行排列（所有大写字母在所有小写字母的前面）。
