# 프로그래머스 소수찾기
- - - 

```
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

vector <int> v;
// 해당 문자열이 number로만 만들어진지 확인
bool allUsed(int i, string numbers) {
    string si = to_string(i);
    vector<bool> visit(v.size(), false);
        
    for (int j = 0; j < si.size(); j++) {
        int index = numbers.find(si.substr(j, 1));
        
        // numbers에서 해당 숫자가 발견되지 않을 경우
        if (index >= numbers.size()) {
            return false;
        }
        else {
            numbers = numbers.substr(0, index) + numbers.substr(index + 1);
        }
    }
    
    return true;
}


int solution(string numbers) {
    int answer = 0;
    
    //주어진 numbers를 조합해 만들 수 있는 가장 큰 수 만들기
    int max;
    sort(numbers.begin(), numbers.end(), greater<char>());
    max = stoi(numbers);
    
    //max 만큼 배열을 만들어 소수여부를 판단할 수 있는 값을 넣는다.
    bool *isPrime = new bool[max+1];
    for(int i=0; i<max+1; i++) isPrime[i] = true;
    for(int i=2; i<sqrt(max); i++){
        for(int k=2; i*k<=max; k++){
            isPrime[i*k] = false;
        }
    }
   // for(int i=2; i<max+1; i++) cout << i << "는" << isPrime[i] << endl;
    for(int i=2; i<max+1; i++){
        if(isPrime[i]){
            if(allUsed(i,numbers)) {
                answer++;
         }
        }
    }
    
    return answer;
}
```
