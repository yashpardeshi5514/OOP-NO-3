#include<iostream>
#include<cstring>
#include<exception>
using namespace std;
class publication
{
protected:
string title;
float price;
public:
publication()
{
title="";
price=0.0;
}
publication(string t,float p)
{
title=t;
price=p;
}
};
class books: public publication
{
int pages;
public:
books()
{
int pagecount=0;
}
books(string t,float p,int pc):publication (t,p)
{

int pagecount=pc;
}
void getb();
void displayb();
};
class tape:public publication
{
float min;
public:
void CD()
{
float time=0.0;
}
void CD(string t,float p,float tim)
{
min=tim;
}
void gett();
void displayt();
};
void books::getb()
{
cout<<"Enter the details of the book:"<<endl;
cout<<"Enter the title of the book:"<<flush;
cin.ignore (1,'\n');
getline(cin,title);
cout<<"Enter the price of the book:"<<flush;
cin>>price;
cout<<"Enter the pages of the book:"<<flush;
cin>>pages;

try
{
if(pages>500&&pages<1500)
{
if(pages>100&&price<2000)
{
displayb();
}
}
else throw(pages);
}
catch(int i)
{
cout<<"Caught exception in function of book"<<endl;
cout<<"You entered an invalid data"<<endl;
title="0";
price=0.0;
pages=0;
displayb();
throw;
}
}
void books::displayb()
{
cout<<"The book you entered is:"<<endl<<endl;
cout<<"The entered title is:"<<title<<endl;
cout<<"The entered price is:"<<price<<endl;
cout<<"The entered pages are:"<<pages<<endl;
}
void tape::gett()
{

cout<<"Enter the details of the tape:"<<endl;
cout<<"Enter the title of the tape:"<<flush;
cin.ignore(1,'\n');
getline(cin,title);
cout<<"enter the pages of the tape:"<<flush;
cin>>price;
cout<<"enter the pages of the playing time (in minutes):"<<flush;
cin>>min;
try
{
if(min>30.00&&min<90.00)
{
if(price>500&&price<1000)
{
displayt();
}
}
else throw(min);
}
catch(float f)
{
cout<<"caught exception in the function of tape"<<endl;
cout<<"you entered an invalid data"<<endl;
title="0";
price=0.0;
min=0.0;
displayt();
throw;
}
}
void tape::displayt()

{
cout<<"the details of tape you entered is:"<<endl<<endl;
cout<<"the entered title is:"<<title<<endl;
cout<<"the entered price is:"<<price<<endl;
cout<<"the entered play time is:"<<min<<endl;
}
int main()
{
books b;
tape t;
int choice;
cout<<"Do want to buy a book(press 1) or a tape (press 2):"<<flush;
cin>>choice;

switch(choice)
{
case 1:try
{
b.getb();
}
catch(int i){
cout<<"caught exception in int main()"<<endl;
}
break;
case 2:try
{
t.gett();
}
catch(float f){
cout<<"caught exception in int main()"<<endl;
}

break;
default: cout<<"Entered bad choice!!Try again!!"<<endl;
}
return 0;
}
