Here's a hundred-dollar tip. When I ask you to write C++ code (and the style for other programming languages should be similar), please **strictly adhere** to the following coding standards:

1.  For anything not explicitly defined in this guide, please follow the **Google C++ Style Guide**.
2.  Use an indent of 2 spaces for all code files. The spaces must be half-width English spaces.
3.  Header include directives should be at the top of the source file. There should be no space between `#` and `include`, and one space between `include` and `<header_name>`.
4.  When including multiple headers, `iostream` should always be first. The remaining headers should be ordered by length in a "short-long-short" pattern, for example: `iostream`, `algorithm`, `vector`, `queue`. The use of `bits/stdc++.h` is forbidden.
5.  All competitive programming code should include the `using namespace std;` directive. This directive should be separated by a blank line from other non-`using` blocks (like `#include` or constant definitions). The `std::` prefix should not appear elsewhere in the code.
6.  Separate function definitions with a blank line.
7.  If the problem requires `long long`, define an alias `LL` using `using LL = long long;` below the `using namespace std;` directive. When memory limits permit, all instances of `int` should be replaced with `LL`, except for the return type of `int main()`.
8.  Constants should be defined below the `using` directive, separated by a blank line. Use `constexpr` for compile-time constants and `const` for non-compile-time constants. Constant names must be prefixed with `k` and follow the UpperCamelCase convention, e.g., the constraint for $n$ should be `kMaxN`, and a modulus should be `kMod`.
9.  Prefer global static arrays over `vector` unless `vector` offers a clear convenience. Global arrays should be defined below the constant definitions and before any functions, separated by a blank line.
10. Prefer defining variables in the global scope, especially for input variables like $n$ and $m$ and for core data structures like arrays. Define variables locally only when their scope is confined to a single function or when they need to be re-initialized in repeated function calls (e.g., temporary variables inside a loop).
11. The C++ standard should be C++14 (GCC 9). Use modern C++ features like `auto` and range-based `for` loops to shorten code, as long as it does not cause compilation errors.
12. Declare multiple variables of the same type in a single statement, e.g., `int a, b;`. If multiple arrays and variables share the same type, they should also be combined into one definition, with arrays declared before variables, e.g., `int a[kMaxN], b[kMaxN], n, m;`.
13. All variable names should be in lowercase. If a variable name is given in the problem statement, use its lowercase form directly. If the problem uses both uppercase and lowercase versions of the same letter (e.g., $N$ and $n$), rename one to avoid confusion. Prefer common industry three-letter abbreviations for variable names, such as `tot` (total), `cnt` (count), `sum` (summation), `pre` (prefix), `suf` (suffix), `lst` (last), `nxt` (next), `prv` (previous), etc. If a variable's purpose is complex, connect multiple abbreviations with an underscore `_` for clarity.
14. Represent large values in code as `1e9` or `1e18`. Their negative forms are also acceptable. If used multiple times, define a constant `kInf`.
15. For STL containers, prefer using `emplace` functions (e.g., `emplace`, `emplace_back`, `emplace_front`) over `push` or `insert` when available and more convenient.
16. Place a space on both sides of all binary operators, such as `a + b` and `a < b`.
17. Do not place a space before a comma `,`, but add one space after it, e.g., `pow(114, 514)`.
18. Place a space between control flow keywords (like `if`, `for`, `while`) and the following parenthesis to distinguish them from function calls. The correct format is `for (int i = 1; i <= n; i++)`.
19. Use `i`, `j`, `k`, `l`, `p`, etc., for loop variables, unless they have a specific meaning.
20. Always be mindful of bitwise operator precedence. Enclose all binary bitwise operations in parentheses to ensure the intended order of operations.
21. Prefer `struct` over `class` if it's more convenient. Access specifiers like `public` should not be indented, but their member definitions must be indented.
22. When an STL algorithm requires custom comparison logic, follow this order of preference: First, use a `friend` function to overload operators inside the custom type. Second, if applicable, pass a lambda expression. Finally, define a new `Less` functor.
23. Prefer references over pointers when possible. For dynamic arrays, prefer `vector` over allocating memory with `new`.
24. Prefer 1-based indexing for arrays, especially when dealing with logic directly related to problem statement numbering (which usually starts from 1). Use 0-based indexing only when it significantly simplifies the algorithm implementation (e.g., in bitwise or modulo operations).
25. Braces are never optional. The opening brace `{` should be preceded by a space, e.g., `if () {`. The `else`, `else if`, or the `while` part of a `do-while` loop should immediately follow the preceding closing brace `}`, separated by a space, e.g., `} else {` and `} while ();`.
26. Do not use specifiers that are deprecated or discouraged in modern C++, such as `inline` and `register`.
27. Prefer `if-else if-else` structures over `switch` if they are more convenient.
28. If a single-line variable definition exceeds the maximum line width, break the line after a comma and align the variable names on subsequent lines with the first variable name.
29. For `if` conditions that are too long to fit on one line, break and align them in a way that maximizes readability.
30. Function names should use lowerCamelCase and preferably be single words, such as `solve`, `calc` (calculate), `pow` (power), `inv` (inverse), `update`, `modify`, `query`, `dfs` (depth-first search), `bfs` (breadth-first search), etc.

Example Code:

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