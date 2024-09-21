# Cpp_STL_QuickRevision

It contains C++ STLs usage and quick help with easy to understand comments and examples (copy+paste to use). I learned these while solving different kinds of Leetcode Questions.
I will be using "int, string etc" for ease and not complex entities like pairs, structs etc 😉. You can replace it with any data structure If you are confused with the syntax or description, see the example. I am sure that will clear things BECAUSE I have specifically chosen
🔎 "EASY + IMPORTANT + MOST USED" examples. Last but not least, I have added Leetcode Qns also which can be easily solved using STLs

#📝Different ways of using priority_queue (i.e. heap) 🗻
• Default declarations
```
priority_queue<int> pq;                            //creates max-heap
priority_queue<int, vector<int>> pq;               //creates max-heap
```

• writing comparator function for priority_queue
```
1. Using in-built comparator provided by C++ : 

priority_queue<int, vector<int>, greater<int>> pq;  //creates min-heap
priority_queue< pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>> > pq; //min_heap of pairs
priority_queue< pair<int, int>, vector<pair<int, int>>, greater<> > pq;               //min_heap of pairs
```
```
2. Using user defined comparator as a structure

struct comp {
    bool operator()(int &a, int &b) {
        return a<b; //max-heap
        return a>b; //min-heap
    }
};

priority_queue<int, vector<int>, comp> pq;  //usage
```
```
3. Using user defined comparator as a function

static bool comp(int &a, int &b) {
    return a<b; //max-heap
    return a>b; //min-heap
}

priority_queue<int, vector<int>, function<bool(int&, int&)> > pq(comp);   //usage
```
```
4. Using lambda function

auto comp = [](int &a, int &b) {
    return a<b; //max-heap
    return a>b; //min-heap 
};

priority_queue<int, vector<int>, decltype(comp) > pq(comp);   //usage

NOTE :
You can receive parameters inside [] as well i.e. auto comp = [some_parameters]
Ex : You want to access a map inside this lambda function
unordered_map<int, int> mp;

auto comp = [&mp](int &a, int &b) {
    return mp[a] < mp[b]; //etc.
};
```
When and why to use std::move() ⬅️
```
/*
    To efficiently transfer the resources from source to target.
    By efficient, I mean no usage of extra space and time for creating copy.
*/
Examples :
    string source = "MIK";
    string target = "";
    target = std::move(source);
    cout << " source = " << source << endl;
    cout << "target = "  << target << endl;
    /*
        output :
        source = 
        target = "MIK"
    */
    
    vector<string> v;
    string str = "example";
    v.push_back(std::move(str));
    /*
    After this, str becomes empty i.e. ""
    And while moving str inside v, no extra copy of str was done implicitly.
    */

    vector<int> temp{1, 2, 3};
    vector<vector<int>> result;
    result.push_back(std::move(temp));
    /*
    This allows no copy of "temp" being created.
    It ensures that the contents of "temp"
    will be moved into the "result".  This is less
    expensive, also means temp will now be empty.
    */
```
📝 std::accumulate(begin_iterator, end_iterator, initial_sum) ➕
```
int sum = 0;
vector<int> nums{1, 3, 2, 5};
sum = accumulate(begin(nums), end(nums), 0);

cout << sum; //11

Benefit : You didn't have to write for loop to find the sum
```
📝 std::accumulate(begin_iterator, end_iterator, initial_sum, lambda) ➕
```
lambda : Binary operation taking an element of type <initial_sum> as first argument and an
            element in the range as second, and which returns a value that can be assigned to type T.

Example-1 : 

auto lambda = [&](int s, long n) {
    return s + n*n; //sums the square of numbers
    //You can call any other function inside as well
};

int sum = 0;
vector<int> nums{1, 3, 2, 5};
sum = accumulate(begin(nums), end(nums), 0, lambda);

cout << sum; //39

Example-2 : Handling 2-D matrix
//Summming all elements row by row
auto lambda = [&](int sum, vector<int> vec) {
    sum = sum + accumulate(begin(vec), end(vec), 0);
    return sum;
};

int result =  accumulate(matrix.begin(), matrix.end(), 0, lambda);


Beautiful example and usage :
Leetcode-1577 (My Approach - https://leetcode.com/problems/number-of-ways-where-square-of-number-is-equal-to-product-of-two-numbers/discuss/1305961/C%2B-(A-very-simple-Two-Sum-like-approach)

Leetcode-1572 (My Approach - https://leetcode.com/problems/matrix-diagonal-sum/discuss/3498479/Using-C%2B%2B-STL-%3A-accumulate)
```
📝 min_element(begin_iterator, end_iterator), max_element(begin_iterator, end_iterator), minmax_element(begin_iterator, end_iterator) 😲
```
vector<int> nums{1, 3, 2, 5};

int minimumValue = *min_element(begin(nums), end(nums)); //1
int maximumValue = *max_element(begin(nums), end(nums)); //5
                OR,
        auto itr  = minmax_element(begin(nums), end(nums));
int minimumValue  = *itr.first;  //remember, first is minimum  //1
int maximumValue  = *itr.second; //remember, second is maximum //5


Benefit : You didn't have to write for loop to find the max or min element
```
