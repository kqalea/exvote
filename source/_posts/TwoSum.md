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
#### Test by JUnit5
{% codeblock lang:java %}
@Test
public void twoSumTest() throws Exception {
    int target = 6;
    int[] numbers = {1, 2, 3, 4};
    int[] result;
    result = TwoSum.runTwoSum(numbers, target);
    assertTrue(numbers[result[0]] + numbers[result[1]] == target);
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

#### Test by Catch2
{% codeblock lang:cpp %}
TEST_CASE ("TwoSum Test") {
    TwoSum twosum;
    vector<int32_t> numbers{1,2,3,4};
    int32_t target = 6;
    vector<int32_t> answer{1,3};
    vector<int32_t> result;
    result = twosum.runTwoSum(numbers, target);
    std::sort(result.begin(), result.end());
    REQUIRE(result == answer);
}
{% endcodeblock %}

不得不說真的有點意思
尤其是Catch2 跟JUnit5的部分
未來也許會用Mockitoi? blog上面更好讀
下一個更新應該會用 gradle&cmake把code包好 and gitgub release
下下個更新應該是 Python + Javascript(NodeJs)
下下下個更新應該是 Kotlin + Dart ??? not sure
