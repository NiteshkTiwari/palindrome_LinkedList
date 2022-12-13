# palindrome_LinkedList
#include<iostream>
using namespace std;

class Node
{
    public:
    int data;
    Node* next;
    Node(int data)
    {
        this->data=data;
        next=NULL;
    }
};

Node* input()
{
    int data;
    cin>>data;
    Node* head=NULL;
    Node* tail=NULL;
     while(data!=-1)
     {
        Node* newNode=new Node(data);
        if(head==NULL)
        {
            head=newNode;
            tail=newNode;
        }
        else
        {
            tail->next=newNode;
            tail=tail->next;
        }
        cin>>data;
     }
     return head;
}
  Node* reverse(Node* head)
{
  Node* current=head;
  Node* prev=NULL;
  Node* nex;
  while(current!=NULL)
  {
    nex=current->next;
   current->next=prev;
   prev=current;
   current=nex;
   
  }
   
   return prev;
    
}
bool check_palindrome(Node* head)
{
    int length=0;
    Node* temp=head;
    while(temp!=NULL)
    {
        length++;
        temp=temp->next;
    }
    
    if(length%2==0)
    {
        length=length/2;
        temp=head;
        for(int i=0;i<length-1;i++)
        {
          temp=temp->next;
          
        }
        
        
        Node* h2=temp->next;
        temp->next=NULL;

        Node* h1=head;
        h2=reverse(h2);
        
        while(h2!=NULL)
        {
             if(h1->data!=h2->data)
             {
                return false;
             }
             h1=h1->next;
             h2=h2->next;
        }
       return true;
    }

    else{
        length=(length+1)/2;
         temp=head;
        for(int i=0;i<length-1;i++)
        {
          temp=temp->next;
          
        }
        Node* h2=temp->next;
        temp->next=NULL;

        Node* h1=head;
        h2=reverse(h2);
        
        while(h2!=NULL)
        {
             if(h1->data!=h2->data)
             {
               return false;
             }
             h1=h1->next;
             h2=h2->next;
        }
        return true;

    }
}
void print(Node* head)
{
    Node* temp=head;
    while(temp!=NULL)
    {
        cout<<temp->data<<" ";
        temp=temp->next;
    }
}
int main()
{
    Node* head=input();
    
    cout<<check_palindrome(head)<<endl;
}
