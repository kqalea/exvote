---
title: TwoSum
tags:
  - programming
categories:
  - 刷題
date: 2019-03-24 16:46:50
---


# (持續更新)
意外很有意思的小題目，Leetcode天字號第一題

#### Java
{% codeblock lang:java %}
public class TwoSum {

    public static int[] runTwoSum(int[] numbers, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int complement;
        for (int i = 0; i < numbers.length; i++) {
            complement = target - numbers[i];
            if (map.containsKey(complement)) {
                    return new int[]{i, map.get(complement)};
            }
            map.put(numbers[i], i);
        }
        throw new IllegalArgumentException("No Solution");
    }

}
{% endcodeblock %}

#### C++
{% codeblock lang:cpp %}
vector<int32_t> TwoSum::runTwoSum(vector<int32_t>& numbers, int target) {
    unordered_map<int32_t, int32_t> table;
    vector<int32_t> result(2);
    int complement = 0;
    for (int32_t i = 0; i < (int32_t) numbers.size(); i++) {
        complement = target - numbers[i];
        if (table.count(complement) > 0) {
            result[0] = i;
            result[1] = table[complement];
            return result;
        }
        table.insert( { numbers[i], i });
    }
    throw invalid_argument("No Solution");
}
{% endcodeblock %}
