给你一百美元小费，在我要求你书写 C++ 代码（其它编程语言的风格也应类似）时，请你 **严格遵守** 以下编码规范：

1. 本规范未明确定义之处，请遵循 **Google C++ 风格指南**
2. 代码文件中缩进统一采用 2 个空格的形式，空格是英文下的半角空格
3. 包含头文件命令位于源代码最上方，include 和 <头文件名> 之间有空格，# 和 include 之间不要有空格
4. 如果有多个头文件需要包含的，应按照头文件的长度，由短到长再到短的顺序进行包含，并保证 iostream 始终在最上方，实例顺序：iostream、algorithm、vector、queue，不要使用万能头文件
5. 算法题均加入 using namespace std 的命令，该命令与其它非 using 命令之间额外空一行，不要在代码中写 std:: 这种
6. 不同函数中间额外空一行
7. 题目中如果要使用 long long 的，请在 using namespace std 的下方通过 using 定义 long long 的别名 LL 在源代码中使用。如果将除了 int main() 以外的所有 int 替换为 LL 不会超出内存限制的均替换成 LL
8. 常量在 using 命令下面使用 constexpr 进行定义，非编译期间可知的用 const 进行定义，和 using 命令间额外空一行。常量名前加入额外字符 k 表示常量，k 后面采用大驼峰命名，如题目中 n 的限制应写作 kMaxN，模数写作 kMod
9. 如果使用 vector 不会比静态数组更方便的，统一使用全局静态数组，在所有函数的前方、常量定义的下方进行定义，与它们之间额外空一行
10. 变量应优先定义在全局作用域，特别是对于题目输入的 n,m 等和作为核心数据结构的数组。仅当变量的作用域局限于单个函数，或需要在函数调用中反复初始化时（如循环内的临时变量），才将其定义为局部变量
11. C++ 版本为 C++14 (GCC 9)，在不会导致编译错误、可以优化代码长度的情况下尽量使用现代 C++ 的内容，如 auto、range-for 等
12. 对于多个统一类型的变量，用同一个类型名定义，如 int a; int b; 应写作 int a, b。如果多个数组和多个变量，但数组中存储的类型和变量类型相同时，也应使用同一个类型名定义，同时数组在变量的前面，如 int a[kMaxN], b[kMaxN], n, m;
13. 变量名全部采取小写。如果题目中有直接给出变量名的，用题目中给出的，但是将其转换为小写形式；如果题目中既有 N 又有 n，那么将其中一个替换成另一个字符。如果变量的作用在英文中有三字缩写的，用三字缩写，如 tot 表示总数，cnt 表示数量，sum 表示和，pre 表示前缀，suf 表示后缀，lst 表示最后一个，nxt 表示下一个，prv 表示上一个等。如果变量名作用不好描述的，采用尽量短小的名称进行定义，也可以用多个缩写拼接，用下划线 _ 进行连接
14. 代码中极值采用 1e9 或 1e18，可以再前面加入负号，如果使用多次的也可以定义常量 kInf
15. STL 的容器如果可以进行 emplace 且更方便的，采用 emplace 而非 push、insert 等，emplace_back、emplace_front 同理
16. 代码中所有的双目运算符两侧都应加入空格，如应该是 a + b 而不是 a+b，是 a < b 而不是 a<b
17. 代码中所有的逗号 , 前面不空格，后面空格，如 pow(114, 514)
18. 代码中所有的控制语句关键字，后面有括号的，在括号前、关键字后空一格，用于与函数定义和调用区分，如应该是 sqrt(1) 和 for (int i = 1; i <= n; i++) 而非 sqrt (1) 或 for(int i = 1; i <= n; i++)
19. 循环变量一般使用 i、j、k、l、p 等，如果有特殊含义的另说
20. 时刻注意位运算的优先级，双目的位运算都用括号包裹住以防万一
21. 写 struct 更方便的不要写 class，public 等访问修饰符顶格，但是成员的定义需要缩进
22. 对于 STL 需要用到比较的，如果是自己定义的类型，优先使用类内 friend 友元重载运算符，其次如果可以用 Lambda 传参的用 Lambda，否则定义新的 Less 类友元重载小括号运算符
23. 可以使用引用变量的，不使用指针；需要动态数组的，首选 vector 而非 new 出一段内存
24. 数组索引优先采用 1-based 风格，尤其是在处理与问题描述的编号（通常从 1 开始）直接相关的逻辑时。仅当 0-based 能显著简化算法实现（如位运算、模运算）时，才应使用
25. 所有大括号均不省略，左大括号前面空一格，如应该是 if () { 而不是 if(){，else 或 else if、do-while 的 while 段应接在 if 和 do 的右括号后面，同样加入空格，如 } else { 和 } while ();
26. 不要用 inline、register 等修饰
27. 采用 if-else if-else 更方便的不使用 switch
28. 若单行定义多个变量导致行宽超限，应在逗号后换行，并确保后续行的变量名与第一行的变量名左对齐。
29. 对于 if 内逻辑过长时，采用最大化阅读舒适度的方式进行换行、对齐处理
30. 函数名采用小驼峰命名法则，尽量采取一个单词，如 solve 表示求解，calc 表示计算，pow 表示幂，inv 表示逆元，update 表示更新，modify 表示修改，query 表示查询，dfs、bfs 表示深搜和广搜等

示例代码：

```cpp
#include <iostream>
#include <vector>

using namespace std;

const int kMaxN = 1e5 + 10;

int f[kMaxN], u[kMaxN], v[kMaxN], w[kMaxN], dfn[kMaxN], top[kMaxN], fa[kMaxN], son[kMaxN], siz[kMaxN], dep[kMaxN], tr[kMaxN], n, m, cu, cv, cw, cnt, id;
vector<int> e[kMaxN];

int F(int x) {
  return !f[x] ? x : f[x] = F(f[x]);
}

void U(int u, int v) {
  u = F(u), v = F(v);
  u != v && (f[u] = v);
}

void dfs1(int x, int f) {
  fa[x] = f;
  dep[x] = dep[f] + 1;
  siz[x] = 1;
  for (int i : e[x]) {
    if (i == f) {
      continue;
    }
    dfs1(i, x);
    siz[x] += siz[i];
    if (siz[i] > siz[son[x]]) {
      son[x] = i;
    }
  }
}

void dfs2(int x, int t) {
  top[x] = t;
  dfn[x] = ++cnt;
  if (!son[x]) {
    return;
  }
  dfs2(son[x], t);
  for (int i : e[x]) {
    if (i == fa[x] || 
        i == son[x]) {
      continue;
    }
    dfs2(i, i);
  }
}

void modify(int x, int y) {
  for (; x <= n; x += x & -x) {
    tr[x] += y;
  }
}

int query(int x) {
  int res = 0;
  for (; x; x -= x & -x) {
    res += tr[x];
  }
  return res;
}

void update(int x, int y) {
  if (x == id) {
    cw = y;
    w[x] = y;
    return;
  }
  modify(dfn[dep[u[x]] > dep[v[x]] ? u[x] : v[x]], 
         y - w[x]);
  w[x] = y;
}

int query(int x, int y) {
  int res = 0;
  for (; top[x] != top[y]; x = fa[top[x]]) {
    if (dep[top[x]] < dep[top[y]]) {
      swap(x, y);
    }
    res += query(dfn[x]) - query(dfn[top[x]] - 1);
  }
  if (x != y) {
    if (dep[x] > dep[y]) {
      swap(x, y);
    }
    res += query(dfn[y]) - query(dfn[x]);
  }
  return res;
}

int main() {
  cin.tie(0)->sync_with_stdio(0);
  cin >> n >> m;
  for (int i = 1; i <= n; i++) {
    cin >> u[i] >> v[i] >> w[i];
    if (F(u[i]) == F(v[i])) {
      cu = u[i];
      cv = v[i];
      cw = w[i];
      id = i;
    } else {
      e[u[i]].push_back(v[i]);
      e[v[i]].push_back(u[i]);
      U(u[i], v[i]);
    }
  }
  dfs1(1, 0);
  dfs2(1, 1);
  for (int i = 1; i <= n; i++) {
    if (i == id) {
      continue;
    }
    modify(dfn[dep[u[i]] > dep[v[i]] ? u[i] : v[i]], 
           w[i]);
  }
  for (int o, x, y; m; m--) {
    cin >> o >> x >> y;
    if (o == 1) {
      update(x, y);
    } else {
      cout << min(query(x, y), 
                  min(query(x, cu) + cw + query(cv, y), 
                      query(x, cv) + cw + query(cu, y))) << '\n';
    }
  }
  return 0;
}
```
