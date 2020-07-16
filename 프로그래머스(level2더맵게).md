# 프로그래머스 Level2 더맵게
- - -
우선순위큐에 관한문제다..
처음엔 vector로풀었다가 sort를 많이하는 바람에 시간초과가 뜬 것 같다...

```
#include <string>
#include <vector>
#include <queue>
#include <iostream>
using namespace std;

int solution(vector<int> scoville, int K) { 
    int answer = 0;
   
    priority_queue< int, vector<int>, greater<int> > pq;
    for(int i=0; i<scoville.size(); i++) pq.push(scoville[i]);
    while(1){
        if(pq.size() == 1 && pq.top() < K) {
            answer = -1;
            break;
        }
        if(pq.top() >= K){
            break;
        }
        int first = pq.top(); pq.pop();
        int second = pq.top(); pq.pop();
        pq.push(first + 2*second);
        answer++;
    }
    
    return answer;
}
```
