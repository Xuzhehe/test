#include <stdio.h>
#include <stdlib.h>
#define TRUE 1
#define FALSE 0

void AddStu();
void ScanStu();
void QueryStu();
void DeleteStu();
void SortStu();
int StartMenu()//主菜单
{
    int menu;
    printf("\n            |==============================================|");
    printf("\n            |=========欢*迎*来*到*学*生*管*理*系统=========|");
    printf("\n            |==============================================|");
    printf("\n            |----------------------------------------------|");
    printf("\n            |================请选择系统功能================|");
    printf("\n            |----------------------------------------------|");
    printf("\n            |==============================================|");
    printf("\n            |===|(1) 添加学生信息|====|(2) 浏览学生信息|===|");
    printf("\n            |===|(3) 查询学生信息|====|(4) 删除学生信息|===|");
    printf("\n            |===|(5)  按总分排序 |====|(6)   退出系统  |===|");
    printf("\n            |==============================================|");
    printf("\n            |=========*输入对应数字**回车确认选择*=========|");
    printf("\n            |==============================================|\n");
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
            case 1:AddStu; break;//跳转至“添加学生信息”
            case 2:ScanStu; break;//跳转至“浏览学生信息”
            case 3:QueryStu; break;//跳转至“查询学生信息”
            case 4:DeleteStu; break;//跳转至“删除学生信息”
            case 5:SortStu; break;//跳转至“按总分排序”
            case 6:doing=FALSE;printf("退出系统"); break;//退出系统
            default:printf("输入错误，请重新输入！"); break;
        }
    }
    return 0;
}
