# 基于图结构最短路径算法的校园导航（c++）

###### 课设:校园导游咨询系统V1.0 完成时间:2022年5月22日16:37:25

<u>合肥师范学院平面图：</u>

![平面图绘制png](file://C:\Users\10251\Desktop\大二上学期学习文件\2022.cpp\课程设计_敖文康_孙佳乐_张安齐_校园导游图\课程设计——21级计算机类—校园导游图\平面图绘制.png?msec=1688823785975)

<mark>！！！注意事项：</mark>

需要在D盘下创建login_Management_admin.txt文件或者修改成自定义路径作为登陆的账号存放的文件

![](file://C:\Users\10251\AppData\Roaming\marktext\images\2023-07-08-21-28-38-image.png?msec=1688823785973)

**核心代码：**

```
/*求出任意两点之间的最短距离*/
void ShortestPath_Floyd()
{
    for(int i=1;i<=12;i++)
    {
        for(int j=1;j<=12;j++)
        {
            D[i][j]=G.D[i][j];
            if(D[i][j]<Maxint&&i!=j)  Path[i][j]=j;  //两顶点有路,后继置为j
            else Path[i][j]=-1;
        }
    }
    for(int k=1;k<=12;k++)
    {
        for(int i=1;i<=12;i++)
        {
            for(int j=1;j<=12;j++)
            {
                if(D[i][k]+D[k][j]<D[i][j])     //存在更短的路径
                {   
                    D[i][j]=D[i][k]+D[k][j];    //更新值
                    Path[i][j]=Path[i][k];      //更改i的后继为k
                }
            }
        }
    }
}

/*打印路径的函数*/
void OutPath(int s,int e)
{
    int next=s;
    printf(">>路径为:\n");
    while(next!=e)
    {
        printf("%s-->",G.Scspot[next].data.name);
        next=Path[next][e];//当前的后继点的编号
    }
    printf("%s\n",G.Scspot[e].data.name);
}
```
