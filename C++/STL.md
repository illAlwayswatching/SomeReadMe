# 📘 C++ STL大纲

---

## 一、STL 概述

- ✅ STL 是什么？
- ✅ STL 的四大组成部分：
  - 容器（Containers）
  - 算法（Algorithms）
  - 迭代器（Iterators）
  - 函数对象 / 仿函数（Function Objects）
- ✅ STL 的优点：高效、通用、可复用

---

## 二、容器 Containers

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

好的！我们来详细展开你提到的这一段内容：

---

## 一、STL 概述

---

### ✅ STL 是什么？

**STL（Standard Template Library，标准模板库）** 是 C++ 标准库中的一部分，它提供了一系列通用的、可复用的数据结构和算法。

通俗来说，STL 就像是一个“工具箱”，里面包含了各种已经写好的数据结构（比如数组、链表、集合、映射等）、常用的算法（比如排序、查找、合并等），以及用来操作这些结构的工具（比如迭代器、函数对象等）。

> 📌 STL 的设计目标是：**高效性 + 通用性 + 可扩展性**

---

### ✅ STL 的四大组成部分

STL 主要由 **四个核心组件** 构成，它们分别是：

---

#### 1. 容器（Containers）

容器是用来存储数据的结构。你可以把它理解为“装东西的盒子”。

##### 常见容器包括：
- 序列式容器：`vector`, `deque`, `list`
- 关联式容器：`set`, `map`, `multiset`, `multimap`
- 无序关联式容器：`unordered_set`, `unordered_map`
- 容器适配器：`stack`, `queue`, `priority_queue`

🔗 [详细讲解容器分类与使用](#)

---

#### 2. 算法（Algorithms）

算法是用来处理容器中数据的函数。例如：排序、查找、替换、统计等。

##### 特点：
- 所有算法都通过**迭代器**操作数据
- 不依赖具体容器类型
- 高度抽象化，非常灵活

##### 常用算法举例：
```cpp
std::sort(vec.begin(), vec.end()); // 排序
std::find(vec.begin(), vec.end(), 5); // 查找
std::accumulate(vec.begin(), vec.end(), 0); // 求和
```

🔗 [常用 STL 算法一览 & 示例](#)

---

#### 3. 迭代器（Iterators）

迭代器是连接容器和算法的桥梁。你可以把它看作是一个“指针”，用来访问容器中的元素。

##### 分类：
- 输入迭代器、输出迭代器
- 前向迭代器、双向迭代器、随机访问迭代器

##### 常用方法：
```cpp
vec.begin(); // 指向第一个元素
vec.end();   // 指向最后一个元素之后的位置
```

🔗 [深入理解迭代器类型与失效问题](#)

---

#### 4. 函数对象 / 仿函数（Function Objects）

函数对象（Functor）是一种行为像函数的对象。它可以作为参数传给算法，实现自定义逻辑。

##### 优点：
- 比普通函数更灵活
- 可以携带状态
- 编译期优化更好

##### 示例：
```cpp
struct GreaterThanFive {
    bool operator()(int x) { return x > 5; }
};

std::find_if(vec.begin(), vec.end(), GreaterThanFive());
```

也可以使用 Lambda 表达式替代：
```cpp
std::find_if(vec.begin(), vec.end(), [](int x){ return x > 5; });
```

🔗 [详解函数对象与 Lambda 表达式](#)

---

### ✅ STL 的优点：高效、通用、可复用

| 优点 | 说明 |
|------|------|
| 🔥 高效 | 内部实现经过高度优化，接近原生代码性能 |
| 🔄 通用 | 所有组件都使用模板编写，适用于任意数据类型 |
| 💡 可复用 | 提供开箱即用的数据结构和算法，避免重复造轮子 |

---


要不要现在就开始？🚀
