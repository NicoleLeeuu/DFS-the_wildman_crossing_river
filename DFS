#include<iostream>
#include<vector>
#include<unordered_set>
#include<cmath>
using namespace std;
int operatora[8]={1,2,3,0,0,0,1,2};//做某操作时传教士变化数量 
int operatorb[8]={0,0,0,1,2,3,1,1};//做某操作时野人变化数量 
struct state{
	int al,bl,ar,br;
	bool operator==(state s2){
		if(this->al==s2.al&&this->ar==s2.ar&&this->bl==s2.bl&&this->br==s2.br) return true;
		else return false;
	}
};
vector<state> v;
bool Can(state s,int a,int b,int flag){  //判断现在状态是否能做某操作，flag表示左右，1往右，0往左 
	bool vis=false;
	for(int i=0;i<v.size()-1;i++){  //看看之前的轨迹里是否走过该情况，若有，则不走 
		if(v[i]==s) vis=true;
	}
	if(vis) return false;
	//看看变化后的量是否正常，能不能做该操作 
	if(flag==1){ 
		if(s.al>=a&&s.bl>=b&&((s.ar+a)>=(s.br+b)||(s.ar+a)==0||(s.br+b)==0)&&((s.al-a)>=(s.bl-b)||(s.al-a)==0||(s.bl-b)==0)) return true;//&&(a>=b||a==0)不知道是否需要 
	}
	else{
		if(s.ar>=a&&s.br>=b&&((s.al+a)>=(s.bl+b)||(s.al+a)==0||(s.bl+b)==0)&&((s.ar-a)>=(s.br-b)||(s.ar-a)==0||(s.br-b)==0)) return true;//&&(a>=b||a==0)不知道是否需要 
	}
	return false;
}
int m,n;
void DFS(state s,int flag){
	flag==0?flag=1:flag=0;
	if(s.ar==m&&s.br==n){ //找到了一种方法 
		for(int i=0;i<v.size();i++) printf("(%d,%d,%d,%d)%s",v[i].al,v[i].bl,v[i].ar,v[i].br,i==v.size()-1?"\n":"->");
		//打印出一条路径 
		return;
	} 
	for(int i=0;i<8;i++){
		state next;
		if(Can(s,operatora[i],operatorb[i],flag)){
			state now;
			if(flag==1){   
				now.al=s.al-operatora[i];
				now.ar=s.ar+operatora[i];
				now.bl=s.bl-operatorb[i];
				now.br=s.br+operatorb[i];
				now.depth=s.depth+1;
			}
			else{
				now.ar=s.ar-operatora[i];
				now.al=s.al+operatora[i];
				now.br=s.br-operatorb[i];
				now.bl=s.bl+operatorb[i];
				now.depth=s.depth+1;
			} 
			v.push_back(next);//存下下一个状态 
		    DFS(next,flag); //遍历下一个状态 
	    	v.pop_back(); //pop掉该状态 
		}
		
	}
	
}
int main(){
	cin>>m>>n;
	state s;
	s.al=m;s.bl=n;s.ar=0;s.br=0;s.depth=0; 
	v.push_back(s);
	DFS(s,0);
}
