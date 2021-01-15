#include <iostream>
#include <list>
using namespace std;
class node
{
public:
    string key;
    int num_of_node;
    void set_key(string key1)
   {
        key=key1;
   }
    void set_num(int n)
    {
        num_of_node=n;
    }
};
class Graph
{
public:
        int numVertices;
        list<string> *adjLists;
        bool *visited;
        string key1,key2;
public:
        Graph(int V);
        void addEdge(node obj1,node obj2);
        void DFS(int vertex);
        int connected_components();
        void Insert_String(int numVertices);
        bool compare(node obj1,node obj2);
};

Graph::Graph(int vertices)
{
        numVertices = vertices;
        adjLists = new list<string>[vertices];
        visited = new bool[vertices];
}
  bool Graph::compare(node obj1,node obj2)
{
int count1 = 0;
for(int j=0; j<obj1.key1.length(); j++)
{
if(obj1.key1[j]!=obj2.key2[j])
count1++;
}
if(count1==0||count1==1)
return true;
else
return false;
}
Void Graph::Insert_String(int numVertices)
{
    node obj[numVertices];
    string key[numVertices];
    for(int i=0; i<numVertices; i++)
{
        cin>>obj[i].key[i];
        if(i>1)
          {
                if(compare(obj[i-1].key[i-1],obj.key[i]))                    addEdge(obj[i-1].num_of_node,obj[i].num_of_node)
}
}
void Graph::addEdge(node obj1,node obj2)
{
        adjLists[obj1.num_of_node].push_front(obj2.num_of_node);
}
int Graph::connected_components()
{
 bool* visited = new bool[numVertices];
 int count = 0;
 for (int v = 0; v < numVertices; v++)
       visited[v] = false;
   for (int v = 0; v < numVertices; v++)
    {
        if (visited[v] == false)
     {
                DFS(v);
               count += 1;
}
}
    return count;
}
void Graph::DFS(int vertex)
{
    visited[vertex] = true;
    list<int> adjList = adjLists[vertex];
    list<int>::iterator i;
    for (i = adjList.begin(); i != adjList.end(); ++i)
        if (!visited[*i])
               DFS(*i);
}
int main()
{
    int n;
    cin>>n;
    Graph g(n);
    g.Insert_String(n);
    int x = g.connected_components();
    cout<<x;
    return 0;
}
