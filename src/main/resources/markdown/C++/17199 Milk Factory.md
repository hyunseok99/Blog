---
createdAt: 2025-08-02T18:52:14.3633643
modifiedAt: 2025-08-02T18:52:14.3633643
---
- If there exists a station $i$ such that one can walk to station $i$ from any other station, then output the minimal such $i$. Otherwise, output −1.

- 생각 흐름
	- n-1개의 이동 가능한 정보 제공 -> 그래프 
	- 임의의 i 노드부터  모든 station 이동 가능한 경우 출력
	- i->j, j->k 이동 가능하면 i->k 이동 가능 1->N 가능 시 출력 


``` c++
#include <iostream>
#include <unordered_map>
using namespace std;

int n;
int node[101][101];

int main() {
	int res = -1;
	
	cin >> n;
	
	for (int i=1; i<n; i++){
		int a, b;
		cin >> a >> b;
		node[a][b] = 1;
	}	
	
	for(int i=1; i<=n; i++){
		for(int j=1; j<=n; j++){
			for(int k=1; k<=n; k++){
				if(node[j][i] == 1 && node[i][k] == 1) {
					node[j][k] = 1; 
				}
			}
		}
	}

	for(int i=1; i<= n; i++){
		int cnt = 0;
		for(int j=1; j<=n; j++){
			if( node[j][i] == 1){
				cnt++;
			}
		}
		if( cnt == n-1){
			res = i;
			break;
		}
	}

	cout << res;
	return 0;
}
```
