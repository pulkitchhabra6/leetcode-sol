**Intuition** <br>
Let _a1_ be the area of the 1st rectangle, _a2_ be the area of the 2nd rectangle and _a12_ be the area of the region shared by both the rectangles, then _req_area = a1 + a2 - a12_ <br>
<br> **Algorithm** <br>
Finding the areas _a1_ and _a2_ is trivial, let’s see how to find the value of _a12_. <br>
To find the shared area, the first thing to realise is that the shared area will itself be a rectangle. To find the dimensions of the shared rectangle, we just need to find the _x_range_ and the _y_range_ shared by the given rectangles. <br> 
It is not hard to prove that the _x_range_ will be [_max(A,E), min(C,G)_] (i.e. _max of starting x_ to _min of ending x_ coordinates).
Similarly, _y_range_ can be found. <br>
At the end, _ans = a1 + a2 - shared_x_range_length*shared_y_range_length_.

```
class Solution {
public:
	int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
		int area1 = (C - A) * (D - B);
		int area2 = (G - E) * (H - F);

		long x31 = max(A, E), x32 = min(C, G);
		long y31 = max(B, F), y32 = min(D, H);

		int len = max(0l, x32 - x31);
		int breadth = max(0l, y32 - y31);

		int ans = area1 + area2 - len * breadth;

		return ans;
	}
};
```

Note: _long_ has been used at some places because although it is given that the required area will be in the range of _int_, yet the coordinates can have greater values.
