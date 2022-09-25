#  剑指 Offer II 066. 单词之和


实现一个 MapSum 类，支持两个方法，insert 和 sum：

MapSum() 初始化 MapSum 对象
void insert(String key, int val) 插入 key-val 键值对，字符串表示键 key ，整数表示值 val 。如果键 key 已经存在，那么原来的键值对将被替代成新的键值对。
int sum(string prefix) 返回所有以该前缀 prefix 开头的键 key 的值的总和。

class  MapSum {

private  class  Node{

public  int  val;

public  TreeMap<Character,Node> next;

public  Node(int  val)

{

this.val=val;

next=new  TreeMap<>();

}

public  Node()

{

this(0);

}

}

private  Node  root;

public  MapSum() {

root=new  Node();

}

public  void  insert(String  word, int  val) {

Node  cur=root;

for(int  i=0;i<word.length();i++)

{

char  c=word.charAt(i);

if(cur.next.get(c)==null)

{

cur.next.put(c,new  Node());

}

cur=cur.next.get(c);

}

cur.val=val;

}

public  int  sum(String  prefix) {

Node  cur=root;

for(int  i=0;i<prefix.length();i++)

{

char  c=prefix.charAt(i);

if(cur.next.get(c)==null){return  0;}

else{

cur=cur.next.get(c);

}

}

return  sum(cur);

  

}

public  int  sum(Node  node)

{

int  Sum=0;

if(node.next.keySet()==null){return  node.val;}

for(char  c:node.next.keySet())

{

Sum+=sum(node.next.get(c));

}

Sum+=node.val;

return Sum;

}

}

  

/**

* Your MapSum object will be instantiated and called as such:

* MapSum obj = new MapSum();

* obj.insert(key,val);

* int param_2 = obj.sum(prefix);

*/
~~~
