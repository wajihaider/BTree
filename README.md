BTree
=====

this code will show you how to insert and print inorder,postorder values in tree  

#include<iostream>
using namespace std;

class btree
{
private:
  struct treenode
	{
		treenode *left;
		treenode *right;
		int data;
	};

	treenode *root;

public:
	btree();
	void insert(int);
	bool isempty();
	void print();
	void inorder(treenode *);
	void postorder(treenode *);
	void print2();
};

btree::btree()
{
	root=NULL;
}

bool btree::isempty()
{
	return root==NULL;
}

void btree::insert(int d)
{
	treenode *t=new treenode();
	treenode *parent;
	treenode *curr;
	t->data=d;
	t->left=NULL;
	t->right=NULL;
	parent=NULL;

	if(isempty())
	{
		root=t;
	}
	else
	{
		curr=root;

		while(curr)
		{
			parent=curr;
			if(t->data>curr->data)
			{
				curr=curr->right;
			}
			else
				curr=curr->left;
		}
			if(t->data<parent->data)
			{
				parent->left=t;
			}
			else
				parent->right=t;
		
	}
}

void btree::print()
{
	inorder(root);
}

void btree::inorder(treenode *p)
{
	if(p!=NULL)
	{
		if(p->left)
		
			inorder(p->left);
			cout<<" "<<p->data<<" ";
		
		 if(p->right)
		
			inorder(p->right);
		
	}
	else
		return;
}

void btree::postorder(treenode *q)
{
	if(q!=NULL)
	{
		
		 if(q->right)
		
			postorder(q->right);
		cout<<" "<<q->data<<" ";

		if(q->left)
		
			postorder(q->left);
	
		
	}
	else
		return;
}

void btree::print2()
{
	postorder(root);
}

int main()
{
	btree r;
	int a,b;
	do
		{
			cout<<"\npress 1 for insert\npress 2 for inorder show\npress 3 for postorder show \npress 4 for exit\n";
			cin>>a;
			switch(a)
			{
			case 1:
				cout<<"Enter a number ==> ";
				cin>>b;
				r.insert(b);
				break;
		
				break;
			case 2:
				r.print();
				break;
			case 3:
				r.print2();
				break;
			
			default:
				break;
			}
		}
		while(a!=4);
	system("pause");
	return 0;
}



