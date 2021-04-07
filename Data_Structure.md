#Data Structure in C

803复习笔记自用.

----

#C7 图

##C7.1定义和相关术语

###ADT

ADT Graph{
  数据对象V:V是具有相同特性的数据元素的集合,称为顶点集.
  数据关系R:
    R = {VR}
    VR = {<v,w> | v,w \in V,且P(v,w),<v,w>表示从v到w的弧,P(v,w)定义了弧<v,w>的意义或信息}

  基本操作P:
  CreateGraph(&G,V,VR);
  DestroyGraph(&G,V,VR);
  LocateVex(G,u);
  GetVex(G,v);
  PutVex(&G,v,value);
  FirstAdjVex(G,v);
  NextAdjVex(G,v,w);
  InsertVex(&G,v);
  DeleteVex(&G,c);
  InsertArc(&G,v,w);
  DeleteArc(&G,v,w);
  DFSTraverse(G,Visit());
  BFSTraverse(G,Visit());
}ADT Graph

Graph函数在21年和20年大题都出现,20分.其中多为考察函数功能和补写函数.

(v,w)如果是有序的则叫有序图,反之则叫无序图.

对于L=1/2·n(n-1)的无向图称为完全图.

对于L=n(n-1)的有向图称为完全有向图.

如果序列顶点中不出现重复的顶点则称该路径为简单路径,对简单回路同理.

*生成树*:一个连通图的生成树是一个极小连通子图,它含有图中的全部顶点,但只有足以构成一颗树的n-1条边.

一个有向生成森林由若干棵有向树组成,它含有图中全部顶点,但只有足以构成若干棵不相交的有向树的弧.

##C7.2存储结构

从代码上看比较抽象,需要较多的具体例子会后续添加.

主要有四种表示方法:分别是*数组(邻接阵)表示法*、*邻接表表示法*、*十字链表表示法*、*邻接多重表表示法*

*数组(邻接阵)表示法*
```cpp
#define INFINITY
#define MAX_ VERTEX_ NUM20
typedef enum{DG,DN,UDG,UDN} GraphKind;
typedef struct ArcCell{
  VRType adj;
  InfoType * info;
}
typedef struct{
  VertexType vex[MAX_ VERTEX_ NUM];
  AdjMatrix arcs;
  int vexnum,arcnum;
  GraphKind kind;
}MGraph;


Status CreateGraph(MGraph &G){
  scanf(&G.kind);
  switch(G.kind){
    case DG : return CreateDG(G);
    case DN : return CreateDN(G);
    case UDG : return CreateUDG(G);
    case UDN : return CreateUDN(G);
    default : return ERROR;
  }
}
```
