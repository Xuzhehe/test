#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define TRUE 1
#define FALSE 0

typedef struct student
{
    char ID[10];
    char Name[10];
    int score[5]
}STUDENT;
STUDENT stu[1000000];
int n=0;
void AddStu()
{
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
    int c ;
    for(c=0;c<n;c++)
    {
        printf("学号：%s\t 姓名：%s\t 高数成绩：%d\t 英语成绩：%d\t 医化成绩：%d\t Linux成绩：%d\t c语言成绩%d\n",stu[c].ID,stu[c].Name,stu[c].score[0],stu[c].score[1],stu[c].score[2],stu[c].score[3],stu[c].score[4]);

    }
}
void QueryStu()
{
	int i,tp;
	char num1[10];
	char a[10];
	float b;
	printf("请输入要查找的方式\n");
	printf("1：按学号查找\t2：按姓名查找\t");
	scanf("%d",&tp);
	switch(tp)
	{
		case 1:
		printf("请输入该学生学号\n");
		scanf("%s",&num1);
		for(i=0;i<n;i++)
		{

			if(strcmp(stu[i].ID,num1)==0)
			{
				printf("该学生的信息如下：\n");
				printf("学号为：%s\t\n",stu[i].ID);
				printf("姓名为：%s\t\n",stu[i].Name);

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
			}

		}
		break;

	}
}



void DeleteStu();
void SortStu();
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
    int n;
    int menu;
    int doing=TRUE;
    while(doing)//判断用户选择的功能，进行跳转
    {
        menu=StartMenu();
        switch(menu)
        {
            case 1:AddStu();system("pause");system("cls"); break;//跳转至“添加学生信息”
            case 2:ScanStu(); break;//跳转至“浏览学生信息”
            case 3:QueryStu(); break;//跳转至“查询学生信息”
            case 4:DeleteStu; break;//跳转至“删除学生信息”
            case 5:SortStu; break;//跳转至“按总分排序”
            case 6:doing=FALSE;printf("退出系统"); break;//退出系统
            default:printf("输入错误，请重新输入！"); break;
        }
    }
    return 0;
}
