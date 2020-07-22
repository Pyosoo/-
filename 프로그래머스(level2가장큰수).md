# 가장 큰수 (문자열)
- - -

```
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

bool cmp(string a, string b){
    return a+b > b+a ? true : false;
}

string solution(vector<int> numbers) {
    string answer = "";
    vector<string> arr;
    for(int i=0; i<numbers.size(); i++){
        arr.push_back(to_string(numbers[i]));
    }
    sort(arr.begin(), arr.end(), cmp);
    
    for(int i=0; i<arr.size(); i++){
        answer += arr[i];
    }
    if(arr[0] == "0") answer = "0";
    return answer;
}
```
