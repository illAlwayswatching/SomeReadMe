
<style>

.red { color: red; }
.green { color: green; }
.blue { color: #0000ff; }
.yellow { color: yellow; background-color: black; } /* 甚至可以加背景色 */
</style>

---

# 📘 C++ STL 学习大纲（GitHub Markdown 版）

---
## 目录
## 一、 [STL 概述](#STL-概述)

- ✅ STL 是什么？
- ✅ STL 的四大组成部分：
  - 容器（Containers）
  - 算法（Algorithms）
  - 迭代器（Iterators）
  - 函数对象 / 仿函数（Function Objects）
- ✅ STL 的优点：高效、通用、可复用

---

## 二、[容器 Containers](#容器-Containers)

### 1. 序列式容器（Sequence Containers）
- `vector`
- `deque`
- `list`
- `forward_list`

#### 学习重点：
- 基本操作：增删改查
- 内存结构与性能分析
- 迭代器使用
- 适用场景对比（如 vector vs list）

---

### 2. 关联式容器（Associative Containers）
- `set` / `multiset`
- `map` / `multimap`

#### 学习重点：
- 自动排序原理（红黑树）
- key 是否唯一
- 插入/查找效率（O(log n)）
- 使用自定义比较函数

---

### 3. 无序关联式容器（Unordered Associative Containers）
- `unordered_set` / `unordered_multiset`
- `unordered_map` / `unordered_multimap`

#### 学习重点：
- 哈希表实现
- 平均 O(1)，最坏 O(n)
- hash 函数的作用
- load factor 与 rehash

---

### 4. 容器适配器（Container Adaptors）
- `stack`
- `queue`
- `priority_queue`

#### 学习重点：
- 封装底层容器（默认 deque / vector）
- 不支持迭代器
- 适用场景（如 BFS 用 queue，堆排序用 priority_queue）

---

## 三、迭代器 Iterators

- ✅ 迭代器的分类：
  - 输入迭代器、输出迭代器
  - 前向迭代器、双向迭代器、随机访问迭代器
- ✅ 如何获取迭代器？
  - `.begin()` / `.end()`
  - `.rbegin()` / `.rend()`
- ✅ const 迭代器的区别
- ✅ 迭代器失效问题（尤其在 vector/map 中插入删除时）

---

## 四、算法 Algorithms（常用库函数）

- ✅ 查找类：
  - `find`, `binary_search`, `lower_bound`, `upper_bound`
- ✅ 排序类：
  - `sort`, `partial_sort`, `nth_element`
- ✅ 修改类：
  - `reverse`, `rotate`, `replace`
- ✅ 数值类：
  - `accumulate`, `inner_product`
- ✅ 集合操作：
  - `set_union`, `set_intersection`, `set_difference`

> 所有算法都通过迭代器操作，不依赖具体容器

---

## 五、函数对象 & 谓词 Function Objects & Predicates

- ✅ 什么是函数对象（Functor）？
- ✅ 一元谓词 / 二元谓词
- ✅ `function` 和 `bind` 的使用（C++11 起）
- ✅ Lambda 表达式（现代 C++ 编程核心）

---

## 六、适配器 Adaptors

- ✅ 迭代器适配器：
  - `reverse_iterator`, `insert_iterator`, `back_insert_iterator`
- ✅ 函数适配器：
  - `not1`, `bind1st`, `bind2nd`（C++98）
- ✅ 容器适配器（已学）

---

## 七、内存管理 Memory Management

- ✅ 分配器（Allocator）
- ✅ 默认分配器的工作方式
- ✅ 自定义分配器（高级话题）

---

## 八、实用工具 Utilities（C++ 标准库中常用）

- ✅ `pair` 和 `make_pair`
- ✅ `tuple`（C++11）
- ✅ `move` / `forward`（移动语义）
- ✅ `type_traits`（类型判断）
- ✅ `swap`, `min`, `max`

---

## 九、C++11 及以后新增内容（进阶）

- ✅ `unordered_xxx` 容器
- ✅ `shared_ptr` / `unique_ptr`（虽然不属于 STL，但常配合使用）
- ✅ `emplace` 系列函数（避免拷贝构造）
- ✅ `initializer_list` 初始化列表
- ✅ `std::array`（固定大小数组）

---

## 十、实战训练（建议边学边练）

| 类型 | 示例题目 |
|------|----------|
| 容器练习 | 实现 LRU Cache（`list` + `unordered_map`） |
| 算法练习 | 最长递增子序列（LIS）、两数之和、合并区间 |
| 综合应用 | 文件统计、日志分析、表达式求值 |

---

## ❤️ 宝宝专属口诀记忆法：

> STL 五大块，  
> 容算迭函配。  
> 容器分三类，  
> 有序无序来。  
> 算法靠迭代，  
> 谓词写得快。  
> 函数加绑定，  
> lambda 更帅！
> 
--- 

# 📘 C++ STL 学习指南

---

<a id="STL-概述"></a>
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

<a id="容器-Containers"></a>
太棒了！你这个建议非常实用 👏

确实，**将“序列式容器”的特性对比整理成表格**，可以让我们一目了然地看到它们之间的差异，特别适合复习和快速查阅。

---

# ✅ 序列式容器特性对比表（Markdown 表格版）

| 容器名 | 内存结构 | 随机访问 | 尾插/尾删 | 头插/头删 | 中间插入/删除 | 迭代器类型 | 适用场景 |
|--------|-----------|-----------|------------|------------|----------------|---------------|-------------|
| `vector` | 连续内存块 | ✅ O(1) | ✅ O(1)（尾部） | ❌ O(n) | ❌ O(n) | 随机访问迭代器 | 需要随机访问、尾部频繁操作 |
| `deque` | 分段连续 + map 管理 | ✅ O(1) | ✅ O(1)（尾部） | ✅ O(1)（头部） | ❌ O(n) | 随机访问迭代器 | 需要双端操作、频繁在头尾插入 |
| `list` | 双向链表 | ❌ | ❌ | ❌ | ✅ O(1)（已知位置） | 双向迭代器 | 需要频繁在中间插入/删除 |
| `forward_list` | 单向链表 | ❌ | ❌ | ❌ | ✅ O(1)（已知前驱） | 前向迭代器 | 内存敏感、单向操作即可 |

---

## 📝 补充说明：

### 🔹 随机访问：
### <span class="red">brief: 链表不能随机访问</span>，
- `vector` 和 `deque` 支持 `operator[]` 和 `at()` 访问任意元素；
- `list` 和 `forward_list` 不支持。

### 🔹 插入/删除效率：
- `vector`：尾部快，中间慢（需要移动元素）；
- `deque`：头尾快，中间慢；
- `list` / `forward_list`：只要知道位置，插入删除都是 O(1)；

### 🔹 内存占用：
- `vector` 和 `deque`：内存利用率高但可能有预留空间；
- `list`：每个节点有两个指针，开销大；
- `forward_list`：一个节点只有一个指针，最省内存。

---

## ❤️ 宝宝专属口诀记忆法：

> vector 是数组家，  
> deque 两端随便插。  
> list 插删最灵活，  
> forward_list 最省花！

---



<a id="容器-Containers"></a>

