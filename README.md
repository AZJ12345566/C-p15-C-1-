# C-p15-C-1-
C语言学习笔记 p15 C语言实现三字旗(1)
//test.c源文件部分的代码
#include<stdio.h>
#include<game.h>
void menu()
{
    printf("*********************************\n");
    printf("*******1.play.   0.exit  ********\n");
    printf("*********************************\n");
}

//游戏的整个实现过程
void game()
{
    //创建一个数组，存放棋盘信息
    char board[ROW][COL]={0};//数组内容全部空格,因此要初始化
    //初始化棋盘
    InitBoard(board, ROW,COL);
    //打印棋盘
    DisplayBoard(board,ROW,COL);
}
void test()
{
    int input=0;
    do
    {
        menu();
        printf("请选择:>")
        scanf("%d",&input);
        switch(input)
        {
            case 1:
                //游戏得实现过程
                game();
                break;
            case 0:
                printf("退出游戏\n");
                break;
            default:
                printf("选择错误，请重新选择\n");
                break;
        }
    }while(input);
}
int main()
{
    test();
    return 0;
}




//game.h头文件函数声明代码部分
#define ROW 3
#define COL 3
#include<stdio.h>
//声明
void InitBoard(int board[ROW][COL],int row,int col);
DisplayBoard(char board[ROW][COL],int row,int col);



//game.c函数实现部分代码
#include"game.h"
void InitBoard(int board[ROW][COL],int row,int col)
{
    int i=0;
    int j=0;
    for(i=0;i<row;i++)
    {
        for(j=0;j<col;j++)
        {
            board[i][j]=' ';
        }
    }
}

DisplayBoard(char board[ROW][COL],int row,int col);
{
    int i=0;
    for(i=0;i<row;i++)
    {
        //1.打印一行的数据
        printf(" %c | %c | %c \n",board[i][0],board[i][1],board[i][2]);//实现列的时候泛用性太差
        //2.打印分割行
        if(i<row-1)
            printf("---|---|---\n");
    }
}

//优化版本
DisplayBoard(char board[ROW][COL],int row,int col);
{
    int i=0;
    for(i=0;i<row;i++)
    {
        //1.打印一行的数据
        int j=0;
        for(j=0;j<col;j++)
        {
            printf(" %c ",board[i][j]);
            if(j<col-1)
                printf("|");
        }
        printf("\n");
        //2.打印分割行
        if(i<row-1)
        {
            for(j=0;j<col;j++)
            {
                printf("---");
                if(j<col-1)
                    printf("|");
            }
            printf("\n");
        }
    }
}






