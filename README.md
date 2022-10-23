# Display_Number_of_days
a program which shows the days from the start  of year to date specified. Hold the number of days for  each month in an array. Allow the user to enter the  month and the day of the year. Then the program  should display the total days till the day.
#include<iostream>
using namespace std;
struct date
{
       int d,m,y;
};
const int monthdays[12]={31,28,31,30,31,30,31,31,30,31,30,31};
int countleapyear(date d)
{
    int years=d.y;
    if(d.m<=2)
    years--;
    return years/4-years/100+years/400;
}
int getdifference(date dt1,date dt2)
{
    long int n1=dt1.y*365+dt1.d;
    for(int i=0;i<dt1.m-1;i++)
    n1+=monthdays[i];
    n1+=countleapyear(dt1);
    long int n2=dt2.y*365+dt2.d;
    for(int i=0;i<dt2.m-1;i++)
    n2+=monthdays[i];
    n2+=countleapyear(dt2);
    return(n2-n1);
}    
int main()
{
    int t1,m1,s1;
    cout<<"Enter start date(DD MM YYYY): ";
    cin>>t1>>m1>>s1;
    int t2,m2,s2;
    cout<<"Enter end date(DD MM YYYY): ";
    cin>>t2>>m2>>s2;
    date dt1={t1,m1,s1};
    date dt2={t2,m2,s2};
    cout<<"Difference between two dates is: "<<getdifference(dt1,dt2);
    return 0;
}
