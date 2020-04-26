# Djisktra-Algo
//#include<iostream>
#include<bits/stdc++.h>
#include<string>
#include<vector>
#include<stack>
#include<cmath>
#include<queue>
#include<set>
#include<map>
#include <iomanip>
#include<algorithm>
#define int  long long
#define fuck  ios::sync_with_stdio(false);
#define rep(i,a,b)  for(int  i=a;i<b;i++)
#define M 100000000
int gcd(int a,int b){ if(!a) {return b;}return gcd(a,b%a);}
using namespace std;
void addedge(vector<pair<int,int> >arr[],int u,int v,int d)
{
  arr[u].push_back(make_pair(v,d));
  arr[v].push_back(make_pair(u,d));
}
void dfs(vector<pair<int,int> >arr[],int visit[],int dist[],int x)
{
set<pair<int,int> >s;
set<pair<int,int> >::iterator it;
s.insert(make_pair(0,x));
dist[0]=0;
while(s.empty()==false)
{
  it=s.begin();
  int y=it->second;
  s.erase(it);
  visit[y]=1;
  for(int i=0;i<arr[y].size();i++)
  {
    int lexi=arr[y][i].first;
    //cout<<lexi<<endl;
    //cout<<"mf"<<endl;
 
    if(visit[lexi]==0)
    {
      if((dist[y]+arr[y][i].second)<dist[lexi])
      {
        dist[lexi]=dist[y]+arr[y][i].second;
        //cout<<dist[lexi]<<endl;
        s.insert(make_pair(dist[lexi],lexi));
 
      }
    }
  }
}
 
}
int32_t main()
{
  int n,m;
  cin>>n>>m;
  vector<pair<int,int> >arr[n+1];int visit[n+1];
  int dist[n+1];
  //int visit[n+1];
  memset(visit,0,sizeof(visit));
  for(int i=1;i<n+1;i++)
  {
    dist[i]=1000000;
  }
 
for(int i=0;i<m;i++)
{
  int x,y,z;
  cin>>x>>y>>z;
  addedge(arr,x,y,z);
}
//dfs(arr,visit,dist,1);
int q;
cin>>q;
while(q--)
{
  int a;
  cin>>a;
  addedge(arr,0,a,0);
}
 
dfs(arr,visit,dist,0);
for(int i=1;i<=n;i++)
{
  cout<<dist[i]<<endl;
}
 
return 0;
  }
