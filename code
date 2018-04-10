#include<stdlib.h>
#include<stdio.h>
#include<pthread.h>
int i,j,k,p1,r1,allocate1[50][50],max1[50][50],need1[50][50],avail1[50],sequence1[50],x1=0,c1=0,count1=0,test1[50];

void *process(){
for(i=0;i<p1;i++)
{
    for(j=0;j<p1;j++)
    {
        count1=0;
        for(k=0;k<r1;k++)
        {
        if(test1[j]==0&&need1[j][k]<=avail1[k])
        {
            avail1[k]=avail1[k]+allocate1[j][k];
            count1++;
            if(count1==r1)
            {
                test1[j]=1;
                printf("Process %d has been allocated resources\n",j);           
                sequence1[c1]=j;
                c1++;
            }
        continue;
        }
        break;
        }
    }
}
for(i=0;i<p1;i++)
{
    if(test1[i]==0)
    {
    printf("System is in unsafe state : \n");
    x1=1;
    break;
    }
   
}
if(x1==0)
{
printf("System is in safe state : \n");
printf("Safe sequence : \n");
for(i=0;i<p1;i++)
{
    printf("P%d  ",sequence1[i]);
}
}
printf("\n");
}

//-----------------------------------------------------------------------------------

int main(){
int p,r;
printf("\nEnter total no. of processes : ");
scanf("%d",&p);
p1=p;
printf("\nEnter total no. of resources : ");
scanf("%d",&r);
r1=r;
int allocate[p][r],max[p][r],need[p][r],avail[r],sequence[p],x=0,c=0,count=0,test[p];
pthread_t t;
for (i=0;i<p;i++)
{
    test[i]=0;	
    test1[i]=test[i];	
}

for(i=0; i<p; i++)
{
  for(j=0; j<r; j++)
  {
    printf("\nEnter resource %d allocated to process %d : ",j+1,i+1);
    scanf("%d",&allocate[i][j]);
    allocate1[i][j]=allocate[i][j];
  }
system("clear");
}

for(i=0; i<p; i++)
{
   for(j=0; j<r; j++)
   {
    printf("\nEnter max no. of resource %d for process %d : ",j+1,i+1);
    scanf("%d",&max[i][j]);
    max1[i][j]=max[i][j];
   }
system("clear");
}

for(i=0; i<r; i++)
{
  printf("Enter available for resource %d : ",i+1);
  scanf("%d",&avail[i]);
  avail1[i]=avail[i];
}

for(i=0; i<p; i++) 
{
  for(j=0; j<r; j++)
  {
    need[i][j]=max[i][j] - allocate[i][j];
    need1[i][j]=need[i][j];
  }
}

printf("\nallocation matrix : ");
for(i=0; i<p; i++)
{
  printf("\nP%d : ",i);
  for(j=0; j<r; j++)
  {
    printf("\t");
    printf("%d",allocate[i][j]);
  }
  printf("\n");
}

printf("\nmax matrix : ");
for(i=0; i<p; i++)
{
  printf("\nP%d : ",i);
  for(j=0; j<r; j++)
  {
    printf("\t");
    printf("%d",max[i][j]);
  }
  printf("\n");
}

for(i=0; i<p; i++)
{
  printf("\nneed allocated to process %d : ",i);
  for(j=0; j<r; j++)
  {
    printf("\t");
    printf("%d",need[i][j]);
  }
  printf("\n");
}

for(i=0; i<r; i++)
{
  printf("\ninitially available resources  R%d: ",i);
  printf("%d",avail[i]);
  printf("\n");
}

pthread_create(&t,NULL,process,NULL);
pthread_join(t,NULL);
}
