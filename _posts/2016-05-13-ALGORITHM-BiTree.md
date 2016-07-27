---
layout: post
title:  "����������&����"
date:  2016-05-13
categories: ALGORITHM:
---

BiTree:

---

- Ŀ¼
{:toc}

#### ������

```java
class BiTree{  
	private String data;
	private BiTree letf;
	private BiTree right;	
	public BiTree(String data){
		this.letf = null;
		this.right = null;
		this.data = data;
		}
        ��geter/setter
}
```

#### ����������

```java
static String str = "ab#d##c#e##";
	public static BiTree craetBiTree(BiTree node){ //����
	    char c = str.charAt(i++); 
		if(c =='#'){
			node = null;
		}else{
			node = new BiTree(c+"");
			node.setLetf(craetBiTree(node.getLetf()));
			node.setRight(craetBiTree(node.getRight()));		
		}
		return node;	
	}
public static void preOderTraverse(BiTree node){ //ǰ��
		if(node != null){
			System.out.println(node.getData());
			preOderTraverse(node.getLetf());
			preOderTraverse(node.getRight());
		}
	}
	public static void inOderTraverse(BiTree node){// 
		if(node != null){			
			inOderTraverse(node.getLetf());
			System.out.println(node.getData());
			inOderTraverse(node.getRight());
		}
	}
	public static void postOderTraverse(BiTree node){
		if(node != null){			
			postOderTraverse(node.getLetf());
			postOderTraverse(node.getRight());
			System.out.println(node.getData());
		}
	}
```

#### ��֪������ +ǰ��������������򣩣�

����ǰ���ȳ��ֵ�Ϊroot�����ϵĽ�����ֳɣ�root�ҡ���ߵݹ�,��root���

```java
	public static void preAndInToPostOder(char mids[],char pres[],
int start,int end){
		int rootIndex=0;
		if(start>end)
			return;
		for(int i=0;i<pres.length;i++){ ��������Ѱ�ң����ڵ�
			for(int j=start;j<=end;j++){
				if(pres[i]==mids[j]){
					rootIndex = j;
					i=pres.length;break;
				}
			}
		}
		//������������������������list�ȴ���
		System.out.println(mids[rootIndex]);		
		preAndInToPostOder(mids, pres, rootIndex+1,end); root�ұ�
		preAndInToPostOder(mids, pres, start, rootIndex-1); root���	
	}
```

#### ��֪������ +������ǰ����

����ȡ������㣬��Ϊroot�ڵ㣬Ȼ����������Ѱ�ң�������ֳɣ�root���ұ����α���

```java
public static void postAndInToPreOder(char mids[],char post[],
int start,int end){
		int rootIndex=0;
		if(start>end)
			return;
		for(int i=post.length-1;i>=0;i--){
			for(int j=start;j<=end;j++){
				if(post[i]==mids[j]){
					rootIndex = j;
					i=-1;break;
				}
			}
		}
		System.out.println(mids[rootIndex]);ֱ����������е�root�ڵ�
		postAndInToPreOder(mids, post, start, rootIndex-1); root���
		postAndInToPreOder(mids, post, rootIndex+1,end);    root�ұ�
	}
```
