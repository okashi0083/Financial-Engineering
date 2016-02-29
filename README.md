# Financial-Engineering Homework

Date : 2012/5/30

Purpose : Write a C++ program to calculate zero rate for given swap rate.

Step 1 : Enter swap rates each year
 

    int main(){
    float s1,s2,s3,s4,s5,s6,s7;
    float swap[7];

    cout<<"Enter swap rate of year1(s1=):"<<endl;
    cin>>s1;

    cout<<"Enter swap rate of year2(s2=):"<<endl;
    cin>>s2;

    cout<<"Enter swap rate of year3(s3=):"<<endl;
    cin>>s3;

    cout<<"Enter swap rate of year5(s5=):"<<endl;
    cin>>s5;

    cout<<"Enter swap rate of year7(s7=):"<<endl;
    cin>>s7;


    s4=(s3+s5)/2;
    s6=(s5+s7)/2;

    cout<<"swap rate of year4(s4)="<<s4<<endl;
    cout<<"swap rate of year6(s6)="<<s6<<endl;

Step 2 : Save those swap rate inforamtion into array type

    swap[0]=s1;
    swap[1]=s2;
    swap[2]=s3;
    swap[3]=s4;
    swap[4]=s5;
    swap[5]=s6;
    swap[6]=s7;

Step 3 : Use the formula to calculate zero rates each year

    float zero[7]={};
    float n=1/(1+s1);
    zero[0]=log(n)*(-1);
    cout<<"The zero rate of year1 is:"<<zero[0]<<endl;

    float m=1;
    for (int i=1; i<=6; i++)
    {
        for (int j=0;j<=i-1;j++)
        {
            m=m-(swap[i]*exp(-zero[j]));
            m=m/(1+swap[i]);
        }
        zero[i]=-log(m)/(i+1);
        cout<<"The zero rate of %d year is:"<<i+1<<zero[i]<<endl;
    }

    system("pause");
    return 0;
    }

