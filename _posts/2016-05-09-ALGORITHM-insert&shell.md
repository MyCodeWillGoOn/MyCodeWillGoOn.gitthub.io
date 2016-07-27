---
layout: post
title:  "7�ֳ����㷨ʵ�������������&shell����"
date:  2016-05-11
categories: ALGORITHM
---

7�ֳ����㷨ʵ�������������&shell����

---

- Ŀ¼
{:toc}

#### Insert: ֱ�Ӳ��룬shell��

##### ֱ�Ӳ��룺���� ���� �Ѿ��������������

```java
	public static void insertSort(int[] a){
		for(int i=1;i<a.length;i++){
			int m=a[i];
			int j;
			for(j=i-1; j>=0&&m<a[j];j--){
				a[j+1]=a[j];
			}
			a[j+1]=m;
		}		
	}
```

#####  shell��	

�������Ϊ����Ϊdk�������У�Ȼ���������,�ֱ��������һ����dk=1�����������򣬣�dk Ϊ������ 

```java
	private static void sortShell(int a[], int dk) {
		for (int i = 0; i < dk; i++) {
			for (int j = i; j < a.length; j += dk) {
				int min=j;
				for (int k = j + dk; k < a.length; k += dk) {					
					if(a[min]>a[k]){
						min=k;
					}
				}
				if(min!=j){
					int temp=a[min];
					a[min]=a[j];
					a[j]=temp;
				}
			}
		}
	}
```

#####  Merge����n����������n�����У�Ȼ�������鲢�������ϳɳ���Ϊn������

```java
//�����ڵ��������� ���֣�merge��һ����һ��
	private static void sortUnit(int[] a, int left,int mid,int right) {
		int len1=mid-left+1;
		int len2=right-mid;//
		int array1[],array2[];
		//�����������ȡ����
		array1= new int[len1];
		for(int i=0;i<len1;i++){
			array1[i]=a[i+left];
		}		
		array2= new int[len2];
		for(int i=0;i<len2;i++){
			array2[i]=a[i+mid+1];
		}
		
		int j=left,m=0,n=0;
		while(m<len1&&n<len2){ //
			if(array1[m]>array2[n]){
                a[j++]=array2[n++];				
		    }else{
		    	a[j++]=array1[m++];
		    }
		}
		for(;m<len1;m++){ //ʣ�µ�
			a[j++]=array1[m++];	
		}
		for(;n<len2;n++){
			a[j++]=array2[n++];	
		}			
	}
	public static void sort(int a[],int start,int end){
		if(start>=end)
			return;
		int mid=start+(end-start)/2;
		sort(a,start,mid);
		sort(a,mid+1,end);
		sortUnit(a,start,mid,end);
	}
```