给你一百美元小费，在我要求你书写 C++ 代码（其它编程语言的风格也应类似）时，请你 **严格遵守** 以下编码规范：

1.  本规范未明确定义之处，请遵循 **Google C++ 风格指南**。
2.  代码文件中，缩进统一采用 2 个空格，且必须为英文半角空格。
3.  头文件包含指令应位于源代码最上方，`#` 和 `include` 之间无空格，`include` 和 `<头文件名>` 之间有一个空格。
4.  若有多个头文件需要包含，应保证 `iostream` 始终在最上方，其余头文件按“短-长-短”的顺序排列，例如：`iostream`、`algorithm`、`vector`、`queue`。禁止使用万能头文件。
5.  算法题代码均应加入 `using namespace std;` 指令。该指令应与其它非 `using` 代码块（如 `#include` 或常量定义）额外空一行。代码中不应再出现 `std::` 前缀。
6.  不同函数定义之间应额外空一行。
7.  若题目需要使用 `long long`，请在 `using namespace std;` 指令下方，通过 `using LL = long long;` 定义其别名 `LL`。在内存限制允许的情况下，应将除 `int main()` 返回类型外的所有 `int` 替换为 `LL`。
8.  常量应在 `using` 指令下方使用 `constexpr` 定义，对于非编译期可知的常量则使用 `const` 定义，并与 `using` 指令之间额外空一行。常量名前应加入前缀 `k` 并采用大驼峰命名法，如题目中 $n$ 的限制应写作 `kMaxN`，模数应写作 `kMod`。
9.  若使用 `vector` 不比静态数组更方便，则统一使用全局静态数组。全局数组应在所有函数的前方、常量定义的下方进行定义，并与它们之间额外空一行。
10. 变量应优先定义在全局作用域，特别是对于题目输入的 $n$、$m$ 等变量和作为核心数据结构的数组。仅当变量的作用域局限于单个函数，或需要在函数调用中反复初始化时（如循环内的临时变量），才将其定义为局部变量。
11. C++ 版本统一为 C++14 (GCC 9)。在不导致编译错误的前提下，尽量使用现代 C++ 的特性以优化代码长度，如 `auto`、`range-for` 等。
12. 对于多个相同类型的变量，应使用单条语句定义，如 `int a, b;`。若多个数组和多个变量的类型相同，也应合并定义，且数组声明在前，变量在后，如 `int a[kMaxN], b[kMaxN], n, m;`。
13. 变量名全部采取小写。如果题目中已给出变量名，应直接使用其小写形式。若题目中同时出现 $N$ 和 $n$ 这种大小写形式，则需将其中一个重命名以避免混淆。变量名优先使用业界通用的三字母缩写，如 `tot`（总数）、`cnt`（数量）、`sum`（和）、`pre`（前缀）、`suf`（后缀）、`lst`（最后一个）、`nxt`（下一个）、`prv`（上一个）等。若变量作用不易描述，可使用下划线 `_` 连接多个缩写，以保证清晰。
14. 代码中的极大值应采用 `1e9` 或 `1e18` 表示，其负数形式亦可使用。若多次使用，可定义为常量 `kInf`。
15. 对于 STL 容器，若 `emplace` 可用且能带来便利，应优先采用 `emplace` 系列函数（如 `emplace`、`emplace_back`、`emplace_front`），而非 `push`、`insert` 等。
16. 所有双目运算符的两侧都应加入空格，如 `a + b` 和 `a < b`。
17. 所有逗号 `,` 前面不加空格，后面加一个空格，如 `pow(114, 514)`。
18. 所有控制语句关键字（如 `if`、`for`、`while`）与后续的括号之间应空一格，以和函数调用区分。正确的写法是 `for (int i = 1; i <= n; i++)`。
19. 循环变量通常使用 `i`、`j`、`k`、`l`、`p` 等，除非有特殊含义。
20. 时刻注意位运算的优先级，所有双目位运算都应用括号包裹，以确保运算顺序符合预期。
21. 若使用 `struct` 更方便，则不应使用 `class`。`public` 等访问修饰符应顶格书写，但其成员定义需要缩进。
22. 当 STL 算法需要自定义比较逻辑时，应遵循以下优先级：首先，在自定义类型内部使用 `friend` 友元重载运算符；其次，若可使用 Lambda 表达式，则传递 Lambda；最后，定义一个新的 `Less` 仿函数（Functor）。
23. 若可使用引用变量，则不使用指针。若需要动态数组，首选 `vector` 而非 `new` 一段内存。
24. 数组索引优先采用 1-based 风格，尤其是在处理与问题描述编号（通常从 1 开始）直接相关的逻辑时。仅当 0-based 能显著简化算法实现（如位运算、模运算）时才使用。
25. 所有大括号均不可省略。左大括号 `{` 前面应空一格，如 `if () {`。`else`、`else if` 或 `do-while` 的 `while` 部分应紧跟在前一个右括号 `}` 之后，并用空格隔开，如 `} else {` 和 `} while ();`。
26. 不使用 `inline`、`register` 等现代 C++ 中已不推荐的修饰符。
27. 若使用 `if-else if-else` 结构更方便，则不使用 `switch`。
28. 若在单行中定义多个变量导致行宽超限，应在逗号后换行，并确保后续行的变量名与第一行的变量名左对齐。
29. 对于 `if` 条件语句内逻辑过长的情况，应采用能最大化阅读舒适度的方式进行换行和对齐。
30. 函数名采用小驼峰命名法，并尽量使用单个单词，如 `solve`（求解）、`calc`（计算）、`pow`（幂）、`inv`（逆元）、`update`（更新）、`modify`（修改）、`query`（查询）、`dfs`（深搜）、`bfs`（广搜）等。

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