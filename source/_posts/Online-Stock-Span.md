---
title: Online Stock Span
tags:
  - programming
categories:
  - 刷題
date: 2019-04-11 16:36:05
---


# 股價跨幅
# (持續更新)

#### Leetcode 901
#### Real-World Algorithms: A Beginner's Guide CP1

{% codeblock lang:cpp %}
class StockSpanner {
public:
    StockSpanner() {

    }

    int next(int price) {
        int span = 1;
        while(!mStack.empty() && price >= mStack.top().first){
            span += mStack.top().second;
            mStack.pop();
        }
        mStack.emplace(price, span);
        return span;

    }
private:
    stack<pair<int, int>> mStack;
};
{% endcodeblock %}
