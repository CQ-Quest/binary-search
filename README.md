折半查找思想：只适合有序的排序中查找，也就是说，折半查找要求查找表为有序表。  
    将待查关键字与有序表中间位置的记录进行比较，若相等，则查找成功。  

特点：对有序的待排序列查找效率高，且比顺序查找效率高；  
       只适用于顺序储存结构！！！  
平均查找性能与最坏查找性能接近；  

	Key code:  
		int BinarySearch(int a[],int i,int n){  
			int low=1,mid;  
			int high=n;  
			while(low<=high){  
				mid=(low+high)/2;  
				if(i=a[mid]){  
					return mid;  
				}  
					else if(i>a[mid])  
					low=mid+1;  
					else high=mid-1;   
				}   
				return  0;  
		}  

以下为优化：

version1:
![](https://github.com/CQ-Quest/binary-search/blob/master/binary%20search1.png)
这种适用于答案落在左半区间，一般适用于求解最小化最大值。  
当区间[l, r]的更新操作是r = mid; l = mid + 1;时，计算mid时不需要加1。  
		int bsearch_1(int l, int r)    
		{    
		    while (l < r) //l=r结束    
		    {    
			int mid = l + r >> 1;    
			if (check(mid)) r = mid;    
			else l = mid + 1;    
		    }    
		    return l;    
		}    
_______________________________________________________________
version2  
![](https://github.com/CQ-Quest/binary-search/blob/master/binary%20search2.png)  
这种适用于答案落在右半区间，一般适用于求解最大化最小值。    
当区间[l, r]的更新操作是r = mid - 1; l = mid;时，计算mid时需要加1。  

		int bsearch_2(int l, int r)  
		{  
		    while (l < r)//l=r结束  
		    {  
			int mid = l + r + 1 >> 1;  
			if (check(mid)) l = mid;  
			else r = mid - 1;   
		    }  
		    return l;  
		}  
