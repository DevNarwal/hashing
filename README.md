#include<iostream>
#include<vector>
#include<list>
#include<algorithm>
using namespace std;
class Hashing{
    public:
    vector<list<int>> hashtable;
    int buckets;
    Hashing(int a){
        buckets=a;
        hashtable.resize(a);
    }
    int hashvalue(int key){
        return key%buckets;
    }
    void addkey(int key){
        int index= hashvalue(key);
        hashtable[index].push_back(key);
    }
    list<int> :: iterator searchkey(int key){
        int index=hashvalue(key);
        return find(hashtable[index].begin(),hashtable[index].end(),key);
    }
    void deletekey(int key){
        int index=hashvalue(key);
        if(searchkey(key)!=hashtable[index].end()){
            hashtable[index].erase(searchkey(key));
            cout<<key<<" is deleted ";
        }
        else{
            cout<<key<<" is not found ";
        }
    }
};
int main(){
    Hashing h(10);
    h.addkey(777);
    h.addkey(888);
    h.addkey(999);
    h.addkey(111);
    h.deletekey(111);

}


