# Bus-reservation-syatem
In this project i had made asytem for  bus reservation where we have two types of system one for adminstrator and one for customer






Source Code




#include <conio.h>
#include <cstdio>
#include <iostream>
#include <string.h>
#include <cstdlib>
using namespace std;
static int p = 0;
class b
{
    protected:
    char busn[5], driver[10], arrival[5], depart[5], from[10], to[10], seat[8][4][10];
public:    void start()
    {
    cout<<"                     Welcome to Bus Manegement  System                    "<<endl;
    cout<<"                    ______By-Abhinav and Aakash_______                   "<<endl<<"\n\n";
    }
    void install();
    void allotment();
};
class a:public b
{

public:

  void empty();
  void show();
  void avail();
  void position(int i);
}
bus[10];
void vline(char ch)
{
  for (int i=80;i>0;i--)
  cout<<ch;
}
void b::install()
{
  char ans;


  cout<<"Enter bus no: ";
  cin>>bus[p].busn;
  cout<<"\nEnter Driver's name: ";
  cin>>bus[p].driver;
  cout<<"\nArrival time: ";
  cin>>bus[p].arrival;
  cout<<"\nDeparture: ";
  cin>>bus[p].depart;
  cout<<"\nFrom: \t\t\t";
  cin>>bus[p].from;
  cout<<"\nTo: \t\t\t";
  cin>>bus[p].to;
  bus[p].empty();
  p++;


}
void b::allotment()
{
  int seat;
  char number[5];
  top:
  cout<<"Bus no: ";
  cin>>number;
  int n;
  for(n=0;n<=p;n++)
  {
    if(strcmp(bus[n].busn, number)==0)
    break;
  }
  while(n<=p)
  {
    cout<<"\nSeat Number: ";
    cin>>seat;
    if(seat>32)
    {
      cout<<"\nThere are only 32 seats available in this bus.";
    }
    else
    {
    if (strcmp(bus[n].seat[seat/4][(seat%4)-1], "Empty")==0)
      {
        cout<<"Enter passanger's name: ";
        cin>>bus[n].seat[seat/4][(seat%4)-1];
        break;
      }
    else
      cout<<"The seat no. is already reserved.\n";
      }
      }
    if(n>p)
    {
      cout<<"Enter correct bus no.\n";
      goto top;
    }
  }

void a::empty()
{
  for(int i=0; i<8;i++)
  {
    for(int j=0;j<4;j++)
    {
      strcpy(bus[p].seat[i][j], "Empty");
    }
  }
}
void a::show()
{
  int n;
  char number[5];
  cout<<"Enter bus no: ";
  cin>>number;
  for(n=0;n<=p;n++)
  {
    if(strcmp(bus[n].busn, number)==0)
    break;
  }
while(n<=p)
{
  vline('*');
  cout<<"Bus no: \t"<<bus[n].busn
  <<"\nDriver: \t"<<bus[n].driver<<"\t\tArrival time: \t"
  <<bus[n].arrival<<"\tDeparture time:"<<bus[n].depart
  <<"\nFrom: \t\t"<<bus[n].from<<"\t\tTo: \t\t"<<
  bus[n].to<<"\n";
  vline('*');
  bus[0].position(n);
  int a=1;
  for (int i=0; i<8; i++)
  {
    for(int j=0;j<4;j++)
    {
      a++;
      if(strcmp(bus[n].seat[i][j],"Empty")!=0)
      cout<<"\nThe seat no "<<(a-1)<<" is reserved for "<<bus[n].seat[i][j]<<".";
    }
  }
  break;
  }
  if(n>p)
    cout<<"Enter correct bus no: ";
}
void a::position(int l)
{
  int s=0;p=0;
  for (int i =0; i<8;i++)
  {
    cout<<"\n";
    for (int j = 0;j<4; j++)
    {
      s++;
      if(strcmp(bus[l].seat[i][j], "Empty")==0)
        {
          cout.width(5);
          cout.fill(' ');
          cout<<s<<".";
          cout.width(10);
          cout.fill(' ');
          cout<<bus[l].seat[i][j];
          p++;
        }
        else
        {
        cout.width(5);
        cout.fill(' ');
        cout<<s<<".";
        cout.width(10);
        cout.fill(' ');
        cout<<bus[l].seat[i][j];
        }
      }
    }
  cout<<"\n\nThere are "<<p<<" seats empty in Bus No: "<<bus[l].busn;
  }
void a::avail()
{
  for(int n=0;n<p;n++)
  {
    vline('*');
    cout<<"Bus no: \t"<<bus[n].busn<<"\nDriver: \t"<<bus[n].driver
    <<"\t\tArrival time: \t"<<bus[n].arrival<<"\tDeparture Time: \t"
    <<bus[n].depart<<"\nFrom: \t\t"<<bus[n].from<<"\t\tTo: \t\t\t"
    <<bus[n].to<<"\n";
    vline('*');
    vline('_');
  }
}
int main()
{
    b x;
    x.start();
    char a,ans,count=0;
    label1:
    cout<<"Who you are Adminstrator(if admin enter m) or Customer(if customer enter z)\n\n";
    cin>>a;
    if(a=='m')
    {

        char password[20],a[20]="abhi";
        cout<<"\n\nEnter Password:";label:
        cin>>password;
        int d=strcmp(password,a);
        if (d==0)
    {

system("cls");
int w;
do
{

    //system("cls");
  cout<<"\n\n\n\n\n";
  cout<<"\t\t\t1.New/Change Route\n\t\t\t"
  <<"2.Reservation\n\t\t\t"
  <<"3.Seats Available\n\t\t\t"
  <<"4.Buses Available. \n\t\t\t"
  <<"5.Exit";
  cout<<"\n\t\t\tEnter your choice:-> ";
  cin>>w;
  switch(w)
  {
    case 1:  bus[p].install();
      break;
    case 2:  bus[p].allotment();
      break;
    case 3:  bus[0].show();
      break;
    case 4:  bus[p].avail();
      break;

  }

  cout<<"WANT TO WORK MORE AS ADMIN IF YES(Enter y) IF NO(Enter n)";
  cin>>ans;
}
while(ans=='y');
    }
    else
    {
        count++;
        cout<<"wrong password";
        if(count<3)
        cout<<"\nInput password again";
        else
            cout<<"\nYou have crossed the limits";
        goto label;
    }
    }
    if(ans=='n' || a=='n')
    {
system("cls");
int s;
cout<<"\t\t\tNow you are at reservation window";
while(1)
{

    //system("cls");
  cout<<"\n\n\n\n\n";
  cout<<"\t\t\t1.Buses Available. \n\t\t\t"
  <<"2.Reservation\n\t\t\t"
  <<"3.Seats Available\n\t\t\t"
  <<"4.Exit";
  cout<<"\n\t\t\tEnter your choice:-> ";
  cin>>s;
  switch(s)
  {
    case 1:  bus[0].avail();
      break;
    case 2:  bus[p].allotment();
      break;
    case 3:  bus[0].show();
      break;
    case 4:  goto label1;
  }
}
    }
    system("cls");
    cout<<"____________________    Thanks & Good By !!!!!!    ___________________________";

return 0;
}

