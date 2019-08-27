# hello-world
#include<iostream>
#include<stdio.h>
#include<stdlib.h>
using namespace std;
struct node
{
	int data;
	struct node *next;
};
struct node*t=NULL;
void opr_on_lst(void);
insert_at_beg(struct node*start,int itm)
{
	if(start==NULL)
	{
		start=(struct node*)malloc(sizeof(struct node));
		start->data=itm;
		start->next=NULL;
		t=start;
	}
	else
	{
		struct node* temp;
		temp=start;
		start=(struct node*)malloc(sizeof(struct node));
		start->next=temp;
		start->data=itm;
	}
	t=start;
}
insert_at_end(struct node*start,int itm)
{
	if(start==NULL)
	{   
		start=new (node);
		start->data=itm;
		start->next=NULL;
	    t=start;
	}
	else
	{
		struct node *p;
		while(start!=NULL)
		{
			p=start;
			start=start->next;
		}
		p->next=(struct node*)malloc(sizeof(struct node));
		p->next->data=itm;
		p->next->next=NULL;
	}
}
insert_at_pos(struct node*start,int key,int ele)
{

		struct node *temp=start,*p,*t;
		while(temp!=NULL)
		{
			p=temp;
			if(temp->data==key)
			break;
			temp=temp->next;
		}
		if(temp==NULL)
		cout<<"\n=> Key Not Found:";
		else if(temp->next!=NULL)
		{
		 t=new (node);
		 t->next=p->next;
		 p->next=t;
		 t->data=ele;
	    }
	    else
	    {
	    	insert_at_end(p,ele);
		}
}
del_first_nd(struct node*start)
{
	if(start==NULL)
	cout<<"\n=> No Elements Present In the List::";
	else
	{
		struct node *temp;
		temp=start;
		t=start->next;
		free(temp);
	}
}
del_last_nd(struct node*start)
{
	if(start==NULL)
	cout<<"\n=> No Elements Present In the List::";
	else
	{
		struct node *p,*temp;
		while(start->next!=NULL)
		{
			p=start;
			start=start->next;
		}
		temp=p->next;
		p->next=NULL;
		free(temp);
	}
}
del_at_pos(struct node*start,int key)
{
	if(start->data==key)
	del_first_nd(start);
	else
	{
	
		while(start!=NULL)
		{
			if(start->next->data==key)
			break;
			else
			start=start->next;
		}
		if(start->next->next==NULL)
		{
			struct node *t;
			t=start->next;
			start->next=NULL;
			free(t);
		}
		else
		{
			struct node*temp;
			temp=start->next;
			start->next=temp->next;
			free(temp);
		}
	}
}
dispose_lst(struct node*start)
{
	struct node *temp;
	while(start!=NULL)
	{
		temp=start;
		start=start->next;
		free(temp);
	}
	t=NULL;
	cout<<"\n=> List Disposed ";
	cout<<"\n_______________________";
}
travel(struct node*start)
{
	system("cls");
	if(start==NULL)
	cout<<"\n=>List is Empty:";
	else
	{
    	cout<<"\nThe Status of the list::\n\n";
    	while(start!=NULL)
    	{
	     cout<<start->data<<" ";
	     start=start->next;
   	    }
    }
    cout<<"\n_____________________________________";
}
struct node*Insertion(struct node*start)
{
	
	int ch,itm=1,dg=1;
	do{
	do
	{
	 itm=1;
	 cout<<"\n=> *Enter the write choice !!!";
	 cout<<"\n=> 1.Create node:";
	 cout<<"\n=> 2.Add at Begning:";
	 cout<<"\n=> 3.Add Node at Last:";
	 cout<<"\n=> 4.Add Node at given position:";
	 cout<<"\n=> 5.Main Menu:";
	 cout<<"\n=> 6.Display Details:";
	 cout<<"\n=> 7.Exit:";
	 cout<<"\n________________________________";
	 cout<<"\n=> *Enter Choice No._";
	 cin>>ch;
	 system("cls");
    }while(ch<1||ch>7);
    switch(ch)
    {
    	case 1:
    		cout<<"\nEnter the Data <press 9999 to stop>:\n";
    		cout<<"______________________________________\n";
			while(itm!=9999)
    		  {
    			cin>>itm;
    			if(itm==9999)
    			{
    			 cout<<"\nDetails Added Successfully";
    			 cout<<"\n__________________________\n";
				 break;
    		    }
    	       	else
    		 	{
    			 insert_at_end(t,itm);
				}
		      }	
			break;
    	case 2:
    		int data;
    		cout<<"\nEnter the Data:";
    		cin>>data;
    		insert_at_beg(t,data);
    		break;
    	case 3:
    		cout<<"\nEnter the Data:";
    		cin>>itm;
    		insert_at_end(t,itm);	
    		break;
    	case 4:
    		int key,ele;
    		travel(t);
    		cout<<"\n=> Enter the element after which you want insert the given element::";
    		cin>>key;
    		cout<<"\n=> Enter the Data to insert::";
    		cin>>ele;
    		insert_at_pos(t,key,ele);
    		break;
    	case 5:
    		opr_on_lst();    		
    		break;
    	case 6:
    		travel(t);
    		break;
    	case 7:
    		exit(0);
	}
 }while(1);
}
Deletion(struct node*start)
{
	int ch;
	do
	{
		do
		{
			
			cout<<"\n=> **Enter the right choice:";
			cout<<"\n=> 1.Delete First Node:";
			cout<<"\n=> 2.Delete Last Node:";
			cout<<"\n=> 3.Delete Node At given Position:";
			cout<<"\n=> 4.Dispose the List:";
            cout<<"\n=> 5.Display:";
			cout<<"\n=> 6.Main Menu:";
			cout<<"\n=> 7.Exit:";
			cout<<"\n___________________________________";
			cout<<"\n=> Enter choice No.__";
			cin>>ch;
			system("cls");
		}while(ch<1||ch>7);
		switch(ch)
		{
			case 1:
				del_first_nd(t);
				break;
			case 2:
				del_last_nd(t);;
				break;
			case 3:
				travel(t);
				int elem;
				cout<<"\n=> Enter the Element which you want to Delete:";
				cin>>elem;
				del_at_pos(t,elem);
				break;
			case 4:
				dispose_lst(t);
				break;
			case 5:
				travel(t);
				break;
			case 6:
				opr_on_lst();
				break;
			case 7:
				exit(0);
		}
	}while(1);
}
void opr_on_lst(void)
{
	
	int ch;
	do{
	do
	{
		
		cout<<"\n=> *Enter the choice !!!";
		cout<<"\n=> 1.Insertion";
		cout<<"\n=> 2.Deletion";
		cout<<"\n=> 3.Search";
		cout<<"\n=> 4.Show Details";
		cout<<"\n=> 5.Exit";
		cout<<"\n=> *Enter Choice No._";
		cin>>ch;
		system("cls");
	 }while(ch<1||ch>5);
    switch(ch)
    {
    	case 1:
    		Insertion(t);
			break;
    	case 2:
    		Deletion(t);
    		break;
    	//case 3:   
		  //  Search();
		    //break;
		case 4:
		    travel(t);
			break;
		case 5:
		    exit(0);
	}
 }while(1);  
}
int main()
{
 opr_on_lst();
 return 0;
}
