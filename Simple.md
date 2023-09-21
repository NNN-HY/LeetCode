### 1.两数之和

暴力枚举：时间复杂度O(n*2)，空间复杂度：O(1)

C++ vector容器

### 9.回文数

反转数字

特殊情况的考虑：负数，0，以及个位数是0的数

### 13.罗马数字转整数

解法并没有理清楚

```java
class Solution {
    Map<Character, Integer> symbolValues = new HashMap<Character, Integer>() {{
        put('I', 1);
        put('V', 5);
        put('X', 10);
        put('L', 50);
        put('C', 100);
        put('D', 500);
        put('M', 1000);
    }};

    public int romanToInt(String s) {
        int ans = 0;
        int n = s.length();
        for(int i = 0; i < n; ++i) {
            int value = symbolValues.get(s.charAt(i));
            if (i < n-1 && value < symbolValues.get(s.charAt(i + 1))) {
                ans -= value;
            } else {
                ans += value;
            }
        }
        return ans;
    }
}
```

外网高分解法

```
public static int romanToInt(String s) {
	int res = 0;
    char[] arr = s.toCharArray();
	for (int i = arr.length - 1; i >= 0; i--) {
		char c = arr[i];
		switch (c) {
		case 'I':
			res += (res >= 5 ? -1 : 1);
			break;
		case 'V':
			res += 5;
			break;
		case 'X':
			res += 10 * (res >= 50 ? -1 : 1);
			break;
		case 'L':
			res += 50;
			break;
		case 'C':
			res += 100 * (res >= 500 ? -1 : 1);
			break;
		case 'D':
			res += 500;
			break;
		case 'M':
			res += 1000;
			break;
		}
	}
	return res;
}
```

