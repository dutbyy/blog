##MaximalClique（极大团）

### 一、团、极大团、最大团

1. 团：一个无向图的子图，且是完全图(图中的每两个点都有边)。

2. 极大团：一个无向图的子图，是一个团，且不是任意一个团的真子集。

3. 最大团：含有节点最多的极大团。



###二、极大团的算法

​	寻找极大团最简单的思想：

 	1. 生成所有子图
 	2. 判断子图是否是团
 	3. 去掉不是极大团的子图

####1. Bron-Kerbosch

 1. 集合**R**，记录当前极大团中的点。

 2. 集合**P**，记录可能还能加入的点。（和R中所有点都有边的点)

 3. 集合**X**，记录已经加入过某个极大团的点。

```python
#Bron-Kerbosch Algorithm(Version 1)
R={}   #已确定的极大团顶点的集合
P={v}  #未处理顶点集，初始状态是所有结点
X={}   #已搜过的并且属于某个极大团的顶点集合

def BronKerbosch(R, P, X):
   if P and X are both empty:
       report R as a maximal clique
   for each vertex v in P:
       BronKerbosch1(R ⋃ {v}, P ⋂ N(v), X ⋂ N(v))
       P := P \ {v}
       X := X ⋃ {v}
```

