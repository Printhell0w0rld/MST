# MST
How to build a minimum spanning tree c++ ???

Here is how i implement it
-----------------------------------------
```cpp
#include <bits/stdc++.h>
using namespace std;
const int INF=0x3f3f3f3f;

void prim(vector<vector<int>> v){
    int num=v.size();
    vector<int> rem(num,0);
    int start=0;
    rem[start]=1;
    int sum=0;
    vector<int> lowcost(num,0);
    for(int i=0;i<num;i++){
        if(i!=start) lowcost[i]=v[start][i];
    }
    for(int i=0;i<num-1;i++){
        int mincost=INF,vertex=-1;
        for(int j=0;j<num;j++){
            if(rem[j]==0 and mincost>lowcost[j]){
                vertex=j;
                mincost=lowcost[j];
            }
        }
        rem[vertex]=1,sum+= mincost;
        for(int j=0;j<num; j++)
            if(rem[j]==0 and v[vertex][j]<lowcost[j])
                lowcost[j] = v[vertex][j];
    }
    cout<<sum<<'\n';
    
}

int main(){
    fast;
    int n,m;cin>>n>>m;
    vector<vector<int>> v(n,vector<int>(n,INF));
    int a,b,c;
    for(int i=0;i<m;i++){
        cin>>a>>b>>c;
        v[a][b]=c;
        v[b][a]=c;
    }
    prim(v);   
}
```
























