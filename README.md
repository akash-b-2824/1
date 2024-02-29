cq

 #include<stdio.h>  
#include<stdlib.h>  
#define SIZE 5  
char q[SIZE];  
int i,r=-1;  
int option,f=0;  
int j,count=0;  
void insert() {  
if(count==SIZE) 
 printf("\n Q is Full\n");  
else { 
 r=(r+1)%SIZE;  
 printf("\nEnter the item:");  
scanf(" %c",&q[r]);  
count++;  
}  
}  
void delet() { 
 if(count==0)   
printf("\nQ is empty\n");  
else  
{  
 printf("\nDeleted item is: %c",q[f]);  
count--;  
f=(f+1)%SIZE; }  
}  
void display()  
{ 
 if(count==0)   
printf("\nQ is Empty\n");  
else  
{  
i=f;  
for(j=1;j<=count;j++)  
{ 
  printf(" %c",q[i]);  
i=(i+1)%SIZE;  
}  
}  
}  
int main()  
{  
for(;;) 
 {   
printf("\n1.Insert 2.Delete\n 3.Display 4.Exit"); 
  printf("\nEnter your option:");  
scanf("%d",&option);  
switch(option)  
{  
case 1: insert();//Inserting items to Queue   
break;  
case 2: delet(); //Deleting items from Queue   
break;  
case 3:display(); //Displaying items from Queue  
 break;  
default:exit(0);  
} } } 























cal

To develop a C program that fulfills the specified requirements, including declaring a calendar as an array of 7 elements, dynamically allocating memory for strings, and implementing the create(), read(), and display() functions, you can use the following code:

#include <stdio.h>
#include <stdlib.h>
#define MALLOC(p,n,type)\
{\
p=(type*)malloc(n*sizeof(type));\
if(p==NULL)\
{\
printf("Insufficient Memory\n");\
exit(0);\
}\
}

typedef struct{
    char *dayName;
    char *date;
    char *activity;
}Day;


void create(Day *calendar) {
     int i;
    for (i = 0; i < 7; i++) {
        MALLOC(calendar[i].dayName,20,char);
	MALLOC(calendar[i].date,20,char);
        MALLOC(calendar[i].activity,100,char);
        }
    }



void read(Day *calendar) {
    int i;
    for (i = 0; i < 7; i++) {
        printf("Enter the name of the day for day %d: ", i + 1);
        scanf("%s", calendar[i].dayName);

        printf("Enter the date for day %d: ", i + 1);
        scanf("%s", calendar[i].date);

        printf("Enter the activity description for day %d: ", i + 1);
        scanf(" %[^\n]s", calendar[i].activity);
    }
}


void display(Day *calendar) {
    int i;
    printf("Weekly Activity Report:\n");
    for (i = 0; i < 7; i++) {
        printf("Day %d:\n", i + 1);
        printf("Day Name: %s\n", calendar[i].dayName);
        printf("Date: %s\n", calendar[i].date);
        printf("Activity: %s\n", calendar[i].activity);
        printf("\n");
    }
}

int main() {
    Day *calendar;
    int i;
    MALLOC(calendar,7,Day);
    create(calendar);
    read(calendar);
    display(calendar);
    for (i = 0; i < 7; i++) {
        free(calendar[i].dayName);
        free(calendar[i].activity);
    }
    return 0;
}


