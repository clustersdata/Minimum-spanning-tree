# Minimum-spanning-tree

Minimum spanning tree

#include <iostream>
  
#include <math.h>

#include <algorithm>
  
using namespace std;

#define M 501

#define LIM 20000000

struct edg{

	int u,v;
  
	int w;
  
}all_e[M*M/2];

bool operator < (const edg &a,const edg &b){

	return a.w<b.w;  
  
}

int set[M];

inline bool uni(int set[],int a,int b){ 

	int ac=0,a2=a,b2=b,bc=0;
  
	while(set[a]!=0) {a=set[a];ac++;}
  
	if(a2!=a) set[a2]=a;
  
	while(set[b]!=0) {b=set[b];bc++;}
  
	if(b2!=b) set[b2]=b;  
  
	if(a==b) return false;
  
	if(ac<bc) set[a]=b;
  
	else set[b]=a;
  
	return true;
  
}

int main(){

	int i,j,k,n,m,u,v,t;
  
	cin >> t;
  
	for(k=0;k<t;k++){
  
	memset(set,0,sizeof(set));
  
	cin >> n;
  
	int ei=0;
  
	for(i=1;i<=n;i++){
  
		for(j=1;j<=n;j++){
    
			if(t!=0){
      
				edg e;
        
				e.u=i;e.v=j;
        
				scanf("%d",&e.w);
        
				if(i<j)
        
					all_e[ei++]=e;
          
			}
      
		}
    
	}
  
	sort(&all_e[0],&all_e[ei]);
  
	int count=0;
  
int size=ei;

	int max=0;
  
	for(i=0;i<size && count < n-1;i++){
  
		if(uni(set,all_e[i].u,all_e[i].v)){
    
			count++;
      
			if(all_e[i].w>all_e[max].w) max=i;
      
		}
    
	}
  
	printf("%d\n",all_e[max].w);
  
	}
  
	return 0;
  
}

