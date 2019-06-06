# Cafe-management-Project
## Introduction

This programs aims to provide an effective Café management system. Every café needs to maintain a database of its items, customers and bills. Our project provides just that. This database can be created, modified and deleted. Motive of this program is to dilute the work of café staff and reduce work load.

With the help of classes item, customers and bill we maintain different databases with important details being private. Hence data hiding, data abstraction and data encapsulation have been effectively implemented. File handling is an integral part of this project as it is used to store data into files without which data is lost as the program terminates.

This program offers innumerous advantages over the manual system.

1.	The data entry is faster and easier than the manual system which saves significant amount of time.

2.	Searching a particular record just takes a few seconds while one would have to search many files in the manual system.

3.	The modification is less tedious.

4.	The records are much safer and can be organized and customized as per requirements which provides flexibility in the data design which is not possible in the manual system.

5.	It reduces the use of paper and hence helps the environment.

 
## Header Files

1.	#include<conio.h>

Functions used: getch( ) , getche( ) ,clrscr()

2.	#include<stdio.h>

Functions used: gets( ), rename( ), remove( ).

3.	#include<process.h> 

Function used: exit( ).

4.	#include<fstream.h>

Functions used: open( ), close( ), seekp( ).

5.	#include<string.h>

Functions used: strcpy( ).

 
## Classes and Objects

The program has three classes- item, customer and bill. Other than that it has a structure called minibill whose object is used in class bill. Then it also has three functions, itemmenu(), customermenu() and billmenu(), that are called in main function().

```
#include<fstream.h>

#include<conio.h>

#include<string.h>

#include<stdio.h>

#include<process.h>


void itemmenu();

void customermenu();

void billmenu();

//*************************Definition of class item************************** class item

{	int id;
	char name[20];

float price;

public:

void input();

void output();

void add(int );

void display_all();

int search_id(int);

void search_name(char*);

void modify(int);

void del_record(int);

char* retname(){ return name;}

int retid(){ return id;}

float retprice(){ return price;}

}i;

//*************************Definition of class customer********************** class customer

{	int custid;
	char custname[20];

char mobile[11];

public:

void input();

void output();

 

void add(int );

void display_all();

int search_id(int);

void search_name(char*);

void modify(int);

void del_record(int);

char* retcustname(){ return custname;}

int retcustid(){ return custid;}

char* retmobile(){ return mobile;}

}cu;

//*************************Definition of class bill************************** struct minibill //structure to avoid array of each of these data members in bill

{	char nm[20];

float prc;

int ino;

int qty;

};

class bill

{	int billno;

int amount;

minibill ibill[10];

char cuname[80];

int cuid;

char cumobile[11];

int numofitems;

long int tot_amount;

public:

void generate_bill();

void display_all_bill();

}b;

//*************************Void main function******************************** void main()

{	int a;

clrscr();

cout<<"\nHello! Welcome to Cafe Management System\n"; cout<<"Choose from following\n1.Item\n2.Customer\n3.Bill\n"; cout<<"4.Exit from the program "; cin>>a;

 

switch(a)

{	case 1: itemmenu();

break;

case 2: customermenu();

break;

case 3: billmenu();

break;

case 4: exit(0);

break;

}

getch();

}

//*************************Item menu function******************************** void itemmenu()

{	int a,no,c;

char name[80],ans;

do

{clrscr();

cout<<"Choose from the following in item\n1.Add an item\n"; cout<<"2.Display all items";

cout<<"\n3.Search an item on the basis of id\n"; cout<<"4.Search an item on the basis of name";

cout<<"\n5.Modify an item\n6.Delete an item\n7.Return to main menu	";

cin>>a;

switch(a)

{	case 1:

cout<<"How many items do you want to add??\n";

cin>>no;

i.add(no);

break;

case 2:

i.display_all();

break;

case 3:

cout<<"Enter id of item you want to search\n";

cin>>no;

c=i.search_id(no);

break;

case 4:

 

cout<<"Enter name of item you want to search\n";

gets(name);

i.search_name(name);

break;

case 5:

cout<<"Enter id of item you want to modify\n";

cin>>no;

i.modify(no);

break;

case 6:

cout<<"Enter id of item you want to delete\n"; cin>>no;

i.del_record(no);

break;

case 7:

main();

break;

}//switch

cout<<"Do you want to continue in item?\n";

ans=getche();

}while((ans=='y')||(ans=='Y'));

}

//*************************Customer menu function**************************** void customermenu()

{	int a,no,c;

char name[80],ans;

do

{clrscr();

cout<<"Choose from following\n1.Add a customer\n2.Display all customers";

cout<<"\n3.Search a customer on the basis of customer id\n"; cout<<"4.Search a customer on the basis of customer name"; cout<<"\n5.Modify record of a customer\n6.Delete record of a

customer\n";

cout<<"7.Return to main menu	";

cin>>a;

switch(a)

{	case 1:

cout<<"How many customers do you want to add??\n";

 

cin>>no;

cu.add(no);

break;

case 2:

cu.display_all();

break;

case 3:

cout<<"Enter id of customer you want to search\n";

cin>>no;

c=cu.search_id(no);

break;

case 4:

cout<<"Enter name of customer you want to search\n";

gets(name);

cu.search_name(name);

break;

case 5:

cout<<"Enter id of customer you want to modify\n";

cin>>no;

cu.modify(no);

break;

case 6:

cout<<"Enter id of customer you want to delete\n"; cin>>no;

cu.del_record(no);

break;

case 7:

main();

break;

}//switch

cout<<"Do you want to continue in customer?\n";

ans=getche();

}while((ans=='y')||(ans=='Y'));

}

//*************************Bill menu function******************************** void billmenu()

{	int a;

char ans;

do

 

{clrscr();

cout<<"\nChoose from following\n1.Make a new bill\n";

cout<<"2.Display all bills\n3.Return to main menu	";

cin>>a;

switch(a)

{	case 1:

b.generate_bill();

break;

case 2:

b.display_all_bill();

break;

case 3:

main();

break;

}//switch

cout<<"Do you want to continue in bill?\n";

ans=getche();

}while((ans=='y')||(ans=='Y'));

}


//*************************Functions of class item*************************** void item::input()

{	cout<<"\nEnter id of item ";

cin>>id;

cout<<"\nEnter name of item	";

gets(name);

cout<<"\nEnter price of item	";

cin>>price;

}

void item::output()

{	cout<<"\nId: "<<id<<"\nName: "<<name<<"\nPrice: "<<price<<"\n";

}

void item::add(int n)

{

int a;

ofstream fout;

fout.open("item.dat",ios::binary|ios::app);

for(a=0;a<n;a++)

{	i.input();

 

fout.write((char*)this,sizeof(i));

}

fout.close();

}

void item::display_all()

{	ifstream fin("item.dat",ios::binary|ios::in); while(fin.read((char*)this, sizeof(item)))

i.output();

fin.close();

}

int item::search_id(int val)

{	int flag=0;

ifstream fin("item.dat", ios::binary|ios::in); while(fin.read((char*)this, sizeof(item)))

{	if(val==i.retid())

{	flag=1;

cout<<"Item found\n";

i.output();

break;

}

}

if(flag==0)

cout<<"Sorry! item not found";

fin.close();

return flag;

}

void item::search_name(char*n)

{	ifstream fin;

fin.open("item.dat",ios::binary);

int flag=0;

while(fin.read((char*)this,sizeof(i)))

{	if(strcmpi(n,i.retname())==0)

{	cout<<"\nItem found\n";

i.output();

flag=1;

break;

}

}

if(flag==0)

 

cout<<"\nSorry! Item not found\n";

}

void item::modify(int val)

{	int x=0;

int flag=0;

fstream f;

f.open("item.dat",ios::binary|ios::out|ios::in);

while(f.read((char*)this,sizeof(i)))

{	x++;

if(val==i.retid())

{	flag=1;

f.seekg((x-1)*sizeof(i),ios::beg);

cout<<"\nEnter new details of item\n";

i.input();

f.write((char*)this,sizeof(i));

cout<<"Item has been modified\n";

break;

}

}

if(flag==0)

cout<<"\nSorry! Item not found\n";

f.close();

}

void item::del_record(int n)

{	ifstream fin("item.dat",ios::binary);

ofstream fout("temp.dat",ios::binary);

while(fin.read((char*)this,sizeof(i)))

{	if(n!=i.retid())

{	fout.write((char*)this,sizeof(i));

}

}

cout<<"Item has been deleted";

fin.close();

fout.close();

remove("item.dat");

rename("temp.dat","item.dat");

}
 


//*************************Functions of class customer***********************

 

void customer::input()

{	cout<<"\nEnter id of customer "; cin>>custid;

cout<<"\nEnter name of customer	";

gets(custname);

cout<<"\nEnter mobile number of customer "; gets(mobile);

}

void customer::output()

{	cout<<"\nId: "<<custid<<"\nName: "<<custname<<"\nMobile number: "; cout<<mobile<<"\n";

}

void customer::add(int n)

{	int a;

ofstream fout;

fout.open("customer.dat",ios::binary|ios::app);

for(a=0;a<n;a++)

{	cu.input();

fout.write((char*)this,sizeof(cu));

}

fout.close();

}

void customer::display_all()

{	ifstream fin("customer.dat",ios::binary|ios::in); while(fin.read((char*)this, sizeof(customer)))

cu.output();

fin.close();

}

int customer::search_id(int val)

{	int flag=0;

ifstream fin("customer.dat", ios::binary|ios::in); while(fin.read((char*)this, sizeof(customer)))

{	if(val==cu.retcustid())

{	flag=1;

cout<<"Customer found\n";

cu.output();

break;

}

}

 

if(flag==0)

cout<<"Sorry! customer not found";

fin.close();

getch();

return flag;

}

void customer::search_name(char*n)

{	ifstream fin;

fin.open("customer.dat",ios::binary);

int flag=0;

while(fin.read((char*)this,sizeof(cu)))

{	if(strcmpi(n,cu.retcustname())==0)

{	cout<<"\nCustomer found\n";

cu.output();

flag=1;

break;

}

}

if(flag==0)

cout<<"\nSorry! Customer not found\n";

}

void customer::modify(int val)

{	int x=0;

int flag=0;

fstream f;

f.open("customer.dat",ios::binary|ios::out|ios::in);

while(f.read((char*)this,sizeof(cu)))

{	x++;

if(val==cu.retcustid())

{	flag=1;

f.seekg((x-1)*sizeof(cu),ios::beg);

cout<<"\nEnter new details of customer\n";

cu.input();

f.write((char*)this,sizeof(cu));

cout<<"Customer have been modified";

break;

}

}

if(flag==0)

 

cout<<"\nSorry! customer not found\n";

f.close();

}

void customer::del_record(int n)

{	ifstream fin("customer.dat",ios::binary);

ofstream fout("temp.dat",ios::binary);

while(fin.read((char*)this,sizeof(cu)))

{	if(n!=cu.retcustid())

{	fout.write((char*)this,sizeof(cu));

}

}

cout<<"Customer is deleted";

fin.close();

fout.close();

remove("customer.dat");

rename("temp.dat","customer.dat");

}

//**************************Functions of class bill************************** void bill::generate_bill()

{	ofstream fout;

int n=0,val,flag1,flag;

char ans;

fout.open("bill.dat",ios::binary|ios::app);

cout<<"\nEnter bill number\t";

cin>>billno;

cout<<"\nEnter id of customer:	";

cin>>val;

flag1=cu.search_id(val);

if(flag1!=1)

{	cout<<"\nPlease first add record of this customer\n"; getch();

main();

}

strcpy(cuname,cu.retcustname());

cuid=cu.retcustid();

strcpy(cumobile,cu.retmobile());

tot_amount=0;

do

{	cout<<"\nEnter id of item you want to purchase\t";

 

cin>>ibill[n].ino;

flag=i.search_id(ibill[n].ino);

amount=0;

if(flag==1)

{	cout<<"Enter quantity of item\t";

cin>>ibill[n].qty;

ibill[n].prc= i.retprice();

strcpy(ibill[n].nm,i.retname());

amount +=ibill[n].qty*ibill[n].prc;

n++;

}

tot_amount+=amount;

cout<<"\nDo you want to purchase more items?? "; ans=getche();

}while(ans=='y');

clrscr();

cout<<"\n\n\nBill No\t"<<billno<<"\n";

cout<<"\nCustomer name: "<<cuname<<"\nCustomer id: "<<cuid;

cout<<"\nCustomer mobile number: "<<cumobile<<"\n\n\n"; cout<<"Id\t\tName\t\t Price\t\tQuantity\t\t Amount\n"; for(int o=0; o<n; o++)

{	cout<<ibill[o].ino<<"\t\t "<<ibill[o].nm<<"\t\t "; cout<<ibill[o].prc<<"\t\t"<<ibill[o].qty<<"\t\t\t"; cout<<ibill[o].qty*ibill[o].prc<<"\n";

}

cout<<"\n\nTotal Amount\t"<<tot_amount<<"\n";

numofitems=n;

fout.write((char*)this,sizeof(bill));

fout.close();

}


void bill::display_all_bill()

{ clrscr();

ifstream fin;

fin.open("bill.dat", ios::binary);

while(fin.read((char *)this,sizeof(b)))

{

cout<<"\n\n\nBill No\t"<<billno<<"\n";

cout<<"\nCustomer name: "<<cuname<<"\nCustomer id: "<<cuid;

 

cout<<"\nCustomer mobile number: "<<cumobile<<"\n\n\n"; cout<<"Id\t\tName\t\t Price\t\tQuantity\t\t Amount\n"; for(int o=0; o<numofitems; o++)

{	cout<<ibill[o].ino<<"\t\t "<<ibill[o].nm<<"\t\t "; cout<<ibill[o].prc<<"\t\t"<<ibill[o].qty<<"\t\t\t"; cout<<ibill[o].qty*ibill[o].prc<<"\n";

}

cout<<"\n\nTotal Amount\t"<<tot_amount<<"\n";

}

fin.close();

}
```


 
