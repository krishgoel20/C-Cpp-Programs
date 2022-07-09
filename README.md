// C Program

/* Numeric addresses for computers on the international network, 'Internet' has four parts, separated by periods, of the form xxx.yyy.zzz.mmm where xxx, yyy, zzz, and 
mmm are positive integers. Locally, computers are usually known by a nickname as well.

    Sample Data
IP address   NickName
111.22.3.44   platte
555.66.7.88   wabash
111.22.5.66   green
0.0.0.0       none

A pair of computers are said to be in same locality when the first two
components of the addresses are same. write a C program to store the computer network details using a structure and pass this structure as an argument to a function 
that displays a list of messages identifying each pair of computers from the same locality. In the messages, the computers should be identified by their nicknames. 
In this example, the message to be displayed will be Machines platte and green are on the same local network. For example, given IP address and nickname of machines 
as follows :

101.33.2.1   Atlas
101.33.56.80 Horizon
101.43.45.74 Pluto

Print 'Machines Atlas and Horizon' are on the same local network. */

#include <stdio.h>
#include <string.h>

struct Machine_Network
{
    char IP_address[20];
    char NickName[10];
};

int Check_Network_Similarity(struct Machine_Network[],int );

int main()
{
    int n=0;
    int ret;
    
    printf("Enter the no. of machines: ");
    scanf("%d",&n);
    
    struct Machine_Network M_N[n];
    
    for (int i=0;i<n;i++)
    {
        printf("Enter the IP Address and Nickname of Machine %d: ",i+1);
        scanf("%s %s",&M_N[i].IP_address,&M_N[i].NickName);
    }

    ret = Check_Network_Similarity(M_N,n);
    return 0;
}

int Check_Network_Similarity(struct Machine_Network M_N[],int n)
{
    const char IP[3] = ".";
    char *token1;
    char *token2;
    // char *token3, *token4;
    
    for (int j=0;j<n;j++) // loop on no. of machines
    {
        token1 = strtok(M_N[j].IP_address,IP);
        printf("\nToken 1 in machine <%d> is: <%s>\n",j+1,token1);
    
        token1 = strcat(token1,".");
        printf("\nToken 1 now is = <%s>\n",token1);
        
        for (int k=j+1;k<n;k++)
        {
            token2 = strtok(M_N[k].IP_address,IP);
            token2 = strcat(token2,".");
            printf("\nToken 2 is <%s>",token2);
            
            if (strcmp(token1,token2)==0)
            {
                printf("\nMachines %s and %s are on the same local network.\n",M_N[j].NickName,M_N[k].NickName);
            }
            
            else
            {
                printf("\nMachines %s and %s are on different networks.\n",M_N[j].NickName,M_N[k].NickName);
            }
        }
    }
    return 0;
}

// C++ Program

/* In a library, the books are arranged vertically in the rack, one above the other. The book(s) can be added or removed only from the top and not in the middle. 
You have been assigned to add 10 books and remove the books until the book rack is empty. Develop the program using generic functions. */

#include <iostream>
#include <string.h>

using namespace std;

struct Bookrack
{
    int book_num;
    char book_name[20];
};

template <class T,class U>
void addbook_Bookrack(T a,U b,Bookrack &br1)
{
    br1.book_num = a;
    strcpy(br1.book_name,b);
    strcat(br1.book_name,"a");
}

void display_Bookrack(Bookrack &br1)
{
    cout<<br1.book_num;
    cout<<br1.book_name;
}

void removebook_Bookrack(Bookrack b[])
{
    for (int loop_r=10;loop_r>0;loop_r--)
    {
        strcpy(b[loop_r].book_name,"NULL");
        cout<<"\n "<<loop_r;
    } 
}

int main()
{
    Bookrack b[10];
    
    for (int loop_a=0;loop_a<10;++loop_a)
        addbook_Bookrack(loop_a+1,"\nBook ",b[loop_a]);

    for (int count=0;count<10;++count)
        display_Bookrack(b[count]);
    
    removebook_Bookrack(b);
        
    return 0;
}
