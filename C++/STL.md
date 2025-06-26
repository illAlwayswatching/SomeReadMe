---

# 📘 C++ STL 学习指南

## 目录
1. [概述](#概述)
2. [容器 Containers](#容器-containers)
3. [算法 Algorithms](#算法-algorithms)
4. [迭代器 Iterators](#迭代器-iterators)
5. [函数对象 Function Objects](#函数对象-function-objects)

---

<a id="概述"></a>
## 概述

**STL（Standard Template Library）标准模板库** 是 C++ 标准库中最强大、最常用的一部分，它提供了一组通用的数据结构和算法。

### ✅ STL 的四大组成部分：
- **容器（Containers）**：存储数据的结构。
- **算法（Algorithms）**：处理数据的操作。
- **迭代器（Iterators）**：连接容器与算法的桥梁。
- **函数对象 / 仿函数（Function Objects）**：用于自定义逻辑的可调用对象。

### ✅ STL 的优点：
- **高效性**：内部实现经过优化，性能接近原生代码。
- **通用性**：使用模板编写，适用于任意数据类型。
- **可复用性**：开箱即用，避免重复造轮子。

---

<a id="容器-containers"></a>
## 容器 Containers

容器是用来存储和管理一组数据的对象。

### 分类：

| 类型 | 常见容器 | 特点 |
|------|----------|------|
| 序列式容器 | `vector`, `deque`, `list` | 支持顺序访问 |
| 关联式容器 | `set`, `map`, `multiset`, `multimap` | 自动排序，基于红黑树 |
| 无序关联容器 | `unordered_set`, `unordered_map` | 基于哈希表，平均 O(1) |
| 容器适配器 | `stack`, `queue`, `priority_queue` | 对已有容器进行封装 |

### 示例代码：

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {1, 2, 3};

    // 添加元素
    v.push_back(4);

    // 遍历输出
    for (int x : v) {
        cout << x << " ";
    }
    return 0;
}
```

---

<a id="算法-algorithms"></a>
## 算法 Algorithms

STL 提供了大量现成的算法，操作容器中的数据。

### 常用算法示例：

| 算法名 | 功能 |
|--------|------|
| `sort` | 排序 |
| `find` | 查找 |
| `accumulate` | 求和 |
| `reverse` | 反转 |
| `lower_bound` / `upper_bound` | 二分查找 |

### 示例代码：

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> v = {5, 3, 1, 4, 2};

    // 排序
    sort(v.begin(), v.end());

    // 查找
    auto it = find(v.begin(), v.end(), 3);
    if (it != v.end()) {
        cout << "找到位置：" << it - v.begin() << endl;
    }

    return 0;
}
```

---

<a id="迭代器-iterators"></a>
## 迭代器 Iterators

迭代器是连接容器和算法的“指针”，用来遍历和操作容器中的元素。

### 分类：
- 输入迭代器
- 输出迭代器
- 前向迭代器
- 双向迭代器
- 随机访问迭代器

### 示例代码：

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {10, 20, 30};

    // 使用迭代器遍历
    for (auto it = v.begin(); it != v.end(); ++it) {
        cout << *it << " ";
    }

    return 0;
}
```

---

<a id="函数对象-function-objects"></a>
## 函数对象 Function Objects

函数对象（Functor）是一个重载了 `operator()` 的类或结构体，可以像函数一样被调用。

### 示例代码：

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

// 自定义函数对象
struct IsEven {
    bool operator()(int x) const {
        return x % 2 == 0;
    }
};

int main() {
    vector<int> v = {1, 2, 3, 4, 5};

    // 使用函数对象作为谓词
    auto it = find_if(v.begin(), v.end(), IsEven());
    if (it != v.end()) {
        cout << "第一个偶数是：" << *it << endl;
    }

    return 0;
}
```

---
