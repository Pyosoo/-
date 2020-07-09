# 프로그래머스 level2 프린터
- - -

```
#include <string>
#include <vector>
#include <iostream>
#include <utility>
using namespace std;


int solution(vector<int> priorities, int location) {
    int answer = 0;
    vector<pair<int, int>> wait;
    for (int i = 0; i < priorities.size(); i++) {
        pair<int, int> temp = make_pair(priorities[i], i);
        wait.push_back(temp);
    }
    int cnt = 0;
    for (int i = 0; i < wait.size(); i++) {
       // cout << "현재 I 값은 : " << i << endl;
        int find = 0;// 자신보다 큰수의 발견 유무
        for (int k = 1; k < wait.size(); k++) {
            if (wait[i].first < wait[k].first) { //자신보다 우선순위가 높은 것이 있다면
                //자신은 맨뒤로 가서 붙는다.
                wait.push_back(wait[i]);
                //그리고 맨앞에서 제거한다.
                wait.erase(wait.begin());
                find = 1;
                break;
            }
        }
        if (find == 1) {
            i = -1;
        }
        if (find == 0) {
            if (location == wait[0].second) {
                answer = ++cnt;
            }
          //  cout << "현재 맨앞인 " << wait[0].first << "를 출력하고 삭제합니다." << endl;
            wait.erase(wait.begin());
            i = -1;
            cnt++;
        }
    }


    for (int j = 0; j < wait.size(); j++) {
        if (wait[j].second == location) {
            answer = j+1;
        }
    }
    
    return answer;
}
```
