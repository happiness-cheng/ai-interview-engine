# 程序型知识示例：LRU Cache 实现

本文件是行为示例，不是强制模板。Agent 必须提取教学原则，不得机械复制主题、类比或问题数量。

---

## 背景

用户是 C++ 后端开发，正在准备秋招面试。学过哈希表和双向链表，但没实现过 LRU。

---

## 第一轮输出

**直观模型**：

想象一个书架，你最近看过的书放在最前面。当书架满了，最久没看的那本会被拿走。

**正式定义**：

LRU（Least Recently Used）缓存：当容量满时，淘汰最久未使用的数据。

**一个核心机制**：

用哈希表实现 O(1) 查找，用双向链表实现 O(1) 移动和淘汰。

**一个确认问题**：

> 为什么需要两种数据结构，只用一种行不行？

---

## 用户回答后

如果用户理解（"哈希表查找快，链表维护顺序"）→ 继续第二轮。

如果用户不知道 → 用图示讲解：

```
哈希表：key → 链表节点指针
链表：最近使用的在头部，最久的在尾部

get(key) → 哈希表找到节点 → 移到头部
put(key, val) → 满了？删尾部节点 → 新节点插入头部
```

---

## 第二轮输出（最小有效示例）

**最小示范**（展示核心流程）：

```cpp
class LRUCache {
    int capacity;
    list<pair<int,int>> cache;  // {key, value}
    unordered_map<int, list<pair<int,int>>::iterator> map;
public:
    int get(int key) {
        if (map.find(key) == map.end()) return -1;
        cache.splice(cache.begin(), cache, map[key]);
        return map[key]->second;
    }
    void put(int key, int value) {
        if (map.count(key)) {
            map[key]->second = value;
            cache.splice(cache.begin(), cache, map[key]);
            return;
        }
        if (cache.size() == capacity) {
            map.erase(cache.back().first);
            cache.pop_back();
        }
        cache.push_front({key, value});
        map[key] = cache.begin();
    }
};
```

**一个追问**：

> `splice` 这里做了什么？为什么用它而不是先删除再插入？

---

## 用户回答后

如果用户知道（"把节点从原位置移到头部，不用重新分配内存"）→ 即时理解通过（正式评分待变式或跨日验证）。

如果用户不知道 → 讲解 splice 的优势：O(1) 指针操作，不需要 new/delete。

---

## 第三轮输出（逐步减少提示）

**变式问题**：

> 如果要求线程安全的 LRU Cache，你会怎么改？

回答前先检查 tracker：
- 已学过 mutex、锁粒度或并发基础 → 可以正式考察和评分
- 未学过 → 作为新支线进行微型教学，只记录首次教学和即时理解，不评分 Hard

这是开放题，考察：
- 知道加锁（mutex）
- 知道锁的粒度（整个缓存 vs 分段）
- 知道读写锁的优化

**实践验证**：

> 请手写 `get` 函数，不看刚才的代码。

---

## 评分记录

| 知识点 | 评分 | 说明 |
|--------|------|------|
| LRU 核心机制 | 即时理解 | 首次教学后确认，正式评分待变式验证 |
| splice 用法 | 即时理解 | 首次教学后确认，正式评分待变式验证 |
| 线程安全变式 | Hard | 知道加锁，但锁粒度不清晰 |
| 手写 get | Good | 独立完成，无提示 |
