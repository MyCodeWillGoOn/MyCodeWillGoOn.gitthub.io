---
layout: post
title:  "�ַ���"
date:  2016-05-15
categories: STRING
---

�ַ���

---

- Ŀ¼
{:toc}

#### 1.����ѭ����λ��
 
![1](/image/s1.png)
![2](/image/s2.png)

##### LCS������������У�:Longest Common Subsequence

![3](/image/s3.png)
![4](/image/s4.png)
![5](/image/s5.png)

#### Ӧ�ã�

##### 1: ������str1�����������:

���Ƚ��������򣬵õ�str2��
��str1��str2����������м���

##### 2.������str������������

�Ƚ�str��ת�õ�str2
��str1��str2����������м���




#### �ַ���ȫ�ţ����ظ�����

Permutation("123".toCharArray(),3,1);
N����ȫ�� N! = N*(N-1)*��.
�򣬵�һ��λ����n������ n�֡��ڶ���λ���ϣ�ʣ�µ�n-1��������n-1��

```java
public static void Permutation(char a[],int size,int n){
		if(n==size-1){
			print(a);			
			return ;
		}
		for(int i=n;i<size;i++){
			swap(a,i,n);
			Permutation(a,size,n+1);
			swap(a,i,n);
		}
}
```

#### �ַ���ȫ�ţ����ظ�����

```java
public static void Permutation(char a[],int size,int n){
		if(n==size-1){
			print(a);			
			return ;
		}
		for(int i=n;i<size;i++){
			//��a[i]�� [n,i)֮������Ƚ�
			if(isDuplicate(a,n,i)){ 
				continue;
			}				
			swap(a,i,n);
			Permutation(a,size,n+1);
			swap(a,i,n);
		}
}
```

�������ݲ���---��Hash����10�ڸ�Url������ĳ��urlλ��
Tire����һ�������ı���ͳ����Ƶ�����ֵ�ǰ10����
