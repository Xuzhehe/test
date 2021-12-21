#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define TRUE 1
#define FALSE 0

typedef struct student
{
    char ID[10];
    char Name[10];
    int score[5];
    int sum;
}STUDENT;
STUDENT stu[1000000];
int n=0;
void AddStu()
{
    system("cls");
    while(TRUE)
    {
    printf("             ==================添加学生信息=================\n");
    printf("请输入学号：");
    scanf("%s",stu[n].ID);
    printf("请输入姓名：");
    scanf("%s",stu[n].Name);
    printf("请输入高数成绩：");
    scanf("%d",&stu[n].score[0]);
    printf("请输入英语成绩：");
    scanf("%d",&stu[n].score[1]);
    printf("请输入医化成绩：");
    scanf("%d",&stu[n].score[2]);
    printf("请输入Linux成绩：");
    scanf("%d",&stu[n].score[3]);
    printf("请输入c语言成绩：");
    scanf("%d",&stu[n].score[4]);
    n++;
    printf("任意键继续，n退出:");
    getchar();
    if(getchar()=='n')
		{
			break;
		}
    }
}
void ScanStu()
{
    system("cls");
    int c ;
    printf("                            ==================浏*览*学*生*信*息=================\n");
    printf("-------------------------------------------------------------------------------------------------------------\n");
    for(c=0;c<n;c++)
    {
        printf("学号：%s\t 姓名：%s\t 高数成绩：%d\t 英语成绩：%d\t 医化成绩：%d\t Linux成绩：%d\t c语言成绩%d\n",stu[c].ID,stu[c].Name,stu[c].score[0],stu[c].score[1],stu[c].score[2],stu[c].score[3],stu[c].score[4]);

    }
}
void QueryStu()
{
        system("cls");
	int i,tp;
	char num1[10];
	char a[10];
	printf("1：按学号查找\t2：按姓名查找\t\n");
	while(TRUE)
	{
	    printf("请输入要查找的方式：");
	    scanf("%d",&tp);
	    switch(tp)
	    {
		case 1:
		printf("请输入该学生学号\n");
		scanf("%s",num1);
		for(i=0;i<n;i++)
		{

			if(strcmp(stu[i].ID,num1)==0)
			{
				printf("该学生的信息如下：\n");
				printf("学号为：%s\t\n",stu[i].ID);
				printf("姓名为：%s\t\n",stu[i].Name);
                              printf("高数成绩：%d\t 英语成绩：%d\t 医化成绩：%d\t Linux成绩：%d\t c语言成   绩%d\n",stu[i].score[0],stu[i].score[1],stu[i].score[2],stu[i].score[3],stu[i].score[4]);
			}
		}

		break;
		case 2:
		printf("请输入该学生姓名\n");
		scanf("%s",a);
		for(i=0;i<n;i++)
		{
			if(strcmp(stu[i].Name,a)==0)
			{
				printf("该学生的信息如下：\n");
				printf("学号为：%s\t\n",stu[i].ID);
				printf("姓名为：%s\t\n",stu[i].Name);
			        printf("高数成绩：%d\t 英语成绩：%d\t 医化成绩：%d\t Linux成绩：%d\t c语言成   绩%d\n",stu[i].score[0],stu[i].score[1],stu[i].score[2],stu[i].score[3],stu[i].score[4]);
			}

		}
		break;
		default:printf("输入错误，请重新输入！\n");break;
	    }
	printf("任意键继续，n退出:");
        getchar();
        if(getchar()=='n')
		{
			break;
		}
	}
}

void DeleteStu()
{
	 system("cls");
     int i;
     printf("学生名单：\n");
     printf("*************************************************\n");
     for(i=0;i<n;i++)
	 {
	 	printf("姓名：%s\t学号：%s\t\n",stu[i].Name,stu[i].ID);
	 }
	 printf("\n");
	 printf("*************************************************\n");
     while(TRUE)
     {
         char id[10];
         int a,i;
         printf("请输入学生学号：");
         scanf("%s",id);
         for(i=0;i<n;i++)
		{

			if(strcmp(stu[i].ID,id)==0)
			{
			    a=i;
				printf("该学生的信息如下：\n");
				printf("学号为：%s\t\n",stu[i].ID);
				printf("姓名为：%s\t\n",stu[i].Name);
                printf("高数成绩：%d\t 英语成绩：%d\t 医化成绩：%d\t Linux成绩：%d\t c语言成绩%d\n",stu[i].score[0],stu[i].score[1],stu[i].score[2],stu[i].score[3],stu[i].score[4]);
                printf("是否删除（确认请按y):");
                getchar();
                if(getchar()=='y')
                {
                    for(i=a;i<n-1;i++)
                    {
                       stu[i]=stu[i+1];
                    }
                    n--;
                printf("删除成功！\n");
                }
			}
		}
		getchar();
		printf("任意键继续，n退出:");
        if(getchar()=='n')
		{
			break;
		}
     }
}

void SortStu()
{
    system("cls");
    int i,t,j,k;
    char m[10],a[10];
    for(i=0;i<n;i++)
    {
        stu[i].sum=stu[i].score[0]+stu[i].score[1]+stu[i].score[2]+stu[i].score[3]+stu[i].score[4];
    }
    for(k=0;k<n;k++)
   {
       for (i=0;i<n-1;i++)
    {
        if(stu[i].sum<stu[i+1].sum)
        {
            t=stu[i].sum;
            stu[i].sum=stu[i+1].sum;
            stu[i+1].sum=t;
            strcpy(m,stu[i].ID);
            strcpy(stu[i].ID,stu[i+1].ID);
            strcpy(stu[i+1].ID,m);
            strcpy(a,stu[i].Name);
            strcpy(stu[i].Name,stu[i+1].Name);
            strcpy(stu[i+1].Name,a);
        }
    }
    }
    for(j=0;j<n;j++)
    {
        printf("第%d名,学号为：%s\t，姓名为：%s\t，总分为%d\n",j+1,stu[j].ID,stu[j].Name,stu[j].sum);
    }
}

int StartMenu()//主菜单
{
    int menu;
    printf("\n            |===============================================|");
    printf("\n            |=========欢*迎*来*到*学*生*管*理*系*统=========|");
    printf("\n            |===============================================|");
    printf("\n            |----------------------------------------------=|");
    printf("\n            |================请选择系统功能=================|");
    printf("\n            |-----------------------------------------------|");
    printf("\n            |===============================================|");
    printf("\n            |===|(1) 添加学生信息|=====|(2) 浏览学生信息|===|");
    printf("\n            |===|(3) 查询学生信息|=====|(4) 删除学生信息|===|");
    printf("\n            |===|(5)  按总分排序 |=====|(6)   退出系统  |===|");
    printf("\n            |===============================================|");
    printf("\n            |=========*输入对应数字*|*回车确认选择*=========|");
    printf("\n            |===============================================|\n");
    printf("您选择的是：");
    scanf("%d",&menu);
    getchar();//清除空格缓存
    return menu;//返回选择的功能
}

int main()
{
    int menu;
    int doing=TRUE;
    while(doing)//判断用户选择的功能，进行跳转
    {
        menu=StartMenu();
        switch(menu)
        {
            case 1:AddStu();system("pause");system("cls"); break;//跳转至“添加学生信息”
            case 2:ScanStu(); system("pause");system("cls");break;//跳转至“浏览学生信息”
            case 3:QueryStu(); system("pause");system("cls");break;//跳转至“查询学生信息”
            case 4:DeleteStu(); system("pause");system("cls");break;//跳转至“删除学生信息”
            case 5:SortStu(); system("pause");system("cls");break;//跳转至“按总分排序”
            case 6:doing=FALSE;printf("退出系统"); break;//退出系统
            default:printf("输入错误，请重新输入！"); break;
        }
    }
    return 0;
}
