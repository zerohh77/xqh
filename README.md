#include <iostream>
#include <bits/stdc++.h>
#define M 23333333
using namespace std;
class huffman
{
public:
    huffman();
    void select();
    void display();
    bool check();
private:
    int num[1000];
    int n;
};
huffman::huffman()
{
    cout << "请输入权值个数："<<endl;
    cin >> n;
    cout << "请输入权值："<<endl;
    for (int i=0; i<n; i++)
        cin >> num[i];
    sort(num,num+n);
};
void huffman::select()
{
    int min_num1=M,min_num2=M,tag1,tag2;
    for (int i=0;i<n;i++)
    {
        if (num[i]<min_num1)
        {
            min_num1=num[i];
            tag1=i;
        }
    }
    for(int i=0;i<n;i++)
    {
        if (num[i]<min_num2 && i!=tag1)
        {
            min_num2=num[i];
            tag2=i;
        }
    }
    num[tag2]+=num[tag1];
    num[tag1]=M;
}
void huffman::display()
{
    for(int i=0;i<n;i++)
    {
        if (num[i]!=M)
            printf("%d\t",num[i]);
        else
            printf(" \t");
    }
    cout << endl;
}
bool huffman::check()
{
    for (int i=0;i<n;i++)
    {
        if (num[i]!=M)
            return true;
    }
    return false;
}
int main()
{
    huffman T;
    int flag=1;
    while(T.check())
    {
        T.display();
        T.select();
    }
    return 0;
}
