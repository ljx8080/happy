happy
=====
#include<stdio.h>
char mark[4]={'+','-','*','/'};
float cal(float x,float y,int mark)
{
  switch(mark)
  {
    case 0:return x+y;
    case 1:return x-y;
    case 2:return x*y;
    case 3:return x/y;
  }
}
float calculate_A(float a,float b,float c,float d,int mark1,int mark2,int mark3)
{
  float r1,r2,r3;
  r1=cal(a,b,mark1);
  r2=cal(r1,c,mark2);
  r3=cal(r2,d,mark3);
  return r3;
}
float calculate_B(float a,float b,float c,float d,int mark1,int mark2,int mark3)
{
  float r1,r2,r3;
  r1=cal(b,c,mark2);
  r2=cal(a,r1,mark1);
  r3=cal(r2,d,mark3);
  return r3;
}
float calculate_C(float a,float b,float c,float d,int mark1,int mark2,int mark3)
{
  float r1,r2,r3;
  r1=cal(c,d,mark3);
  r2=cal(b,r1,mark2);
  r3=cal(a,r2,mark1);
  return r3;
}
float calculate_D(float a,float b,float c,float d,int mark1,int mark2,int mark3)
{
  float r1,r2,r3;
  r1=cal(b,c,mark2);
  r2=cal(r1,d,mark3);
  r3=cal(a,r2,mark1);
  return r3;
}
float calculate_E(float a,float b,float c,float d,int mark1,int mark2,int mark3)
{
  float r1,r2,r3;
  r1=cal(a,b,mark1);
  r2=cal(c,d,mark3);
  r3=cal(r1,r2,mark2);
  return r3;
}
float get(int a,int b,int c,int d)
{
  int mark1,mark2,mark3;
  float flag=0;
  for(mark1=0;mark1<4;mark1++)
  {
    for(mark2=0;mark2<4;mark2++)
    {
      for(mark3=0;mark3<4;mark3++)
      {
        if(calculate_A(a,b,c,d,mark1,mark2,mark3)==24)
        {
          printf("((%d%c%d)%c%d)%c%d=24\n",a,mark[mark1],b,mark[mark2],c,mark[mark3],d);
          flag=1;
        }
        if(calculate_B(a,b,c,d,mark1,mark2,mark3)==24)
        {
          printf("(%d%c(%d%c%d))%c%d=24\n",a,mark[mark1],b,mark[mark2],c,mark[mark3],d);
          flag=1;
        }
        if(calculate_C(a,b,c,d,mark1,mark2,mark3)==24)
        {
          printf("%d%c(%d%c(%d%c%d))=24\n",a,mark[mark1],b,mark[mark2],c,mark[mark3],d);
          flag=1;
        }
        if(calculate_D(a,b,c,d,mark1,mark2,mark3)==24)
        {
          printf("%d%c((%d%c%d)%c%d)=24\n",a,mark[mark1],b,mark[mark2],c,mark[mark3],d);
          flag=1;
        }
        if(calculate_E(a,b,c,d,mark1,mark2,mark3)==24)
        {
          printf("(%d%c%d)%c(%d%c%d)=24\n",a,mark[mark1],b,mark[mark2],c,mark[mark3],d);
          flag=1;
        }
      }
    }
  }
  return flag;
}
int main()
{
  int a,b,c,d;
  printf("Please input 4 numbers(1~13):");
  scanf("%d%d%d%d",&a,&b,&c,&d);
    if((a>=1&&a<=13)&&(b>=1&&b<=13)&&(c>=1&&c<=13)&&(d>=1&&d<=13))
    {
      get(a,b,c,d);
    }
      else
      {
        printf("Input illege,please input again(1~13)");
      }
  return;
}

