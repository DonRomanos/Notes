# Value Semantics

References:
 * [Value Semantics: Safety, Independence, Projection](https://youtu.be/QthAU-t3PQ4) by Dave Abrahams

 Why you should prefer return values over out parameters:
 ```cpp
 // What is the behavior of this program?
 std::vector<int> in{3,2,1};
 auto comparator [&in](int lhs, int rhs){return lhs < in.front();} 
 std::sort(in.begin(), in.end(), comparator);
 ```
 Whenever references are involved as soon as any of the inputs mutates the other or you have aliasing things start to break. You basically have to document that the passed parameters do not affect each other.

If you **do not** use output parameters you avoid that problem in the very first place. Imagine our sort function would look like this:
```cpp
std::vector<int> sort(std::vector<int>, auto(*compare)(int,int)->bool)
```

