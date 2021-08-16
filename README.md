# MST
Build a minimum spanning tree c++ 

Here is how i implement it
-----------------------------------------
```cpp
#include <bits/stdc++.h>
using namespace std;
const int INF=0x3f3f3f3f;

void prim(vector<vector<int>> v){
    int num=v.size();//The numbers of vertices.
    vector<int> rem(num,0);// We use this vector to record which vertex we have already go through.
    int start=0;// The vertex we use to start, you can change the value of "start" it doesn't influence the consequence.
    rem[start]=1;// Because we start with "start" so we change it value into "1" that we know it has benn go through.
    int sum=0;
    vector<int> lowcost(num,0);// We use this vector to record the minimum edge value that connect to the vertex we haven't go through.
    //In this loop we fill some vertex with value,which is connect to "start".
    for(int i=0;i<num;i++){
        lowcost[i]=v[start][i];
    }
    //In this loop we run (num-1) times to get (num-1) edge.
    for(int i=0;i<num-1;i++){
        int mincost=INF,vertex=-1;
        //In this loop we try to get the mimimum value of edge that connect with the vertex that we haven't go through.
        for(int j=0;j<num;j++){
            if(rem[j]==0 and mincost>lowcost[j]){
                vertex=j;
                mincost=lowcost[j];
            }
        }
        //After the process we find the Target vertex and mincost.
        rem[vertex]=1,sum+=mincost;
        //In this loop, we try to update the value of "lowcost" because we find the new vertex above and we might fiind a smaller value of edge that connect with the vertex we haven't go through.
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
    int a,b,c;//a and b is the vertex, c is value of the edge that connect a and b.
    for(int i=0;i<m;i++){
        cin>>a>>b>>c;
        v[a][b]=c;
        v[b][a]=c;
    }
    prim(v);   
}
```





