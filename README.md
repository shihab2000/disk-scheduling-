# disk-scheduling-cscan
#include<stdio.h>
void main()
{
	int a[30],n,i,k=0,j,head,seek=0,seek2,temp;
	printf("ENTER THE  NUMBER OF REQUEST : ");
	scanf("%d",&n);
	printf("ENTER THE HEAD POSITION : ");
	scanf("%d",&head);
	printf("ENTER THE SEQUENCE  :");
	for(i=1;i<=n;i++)
		scanf("%d",&a[i]);
	a[n+1]=head;
	printf("ENTER THE TOTAL DISK SIZE: ");
	scanf("%d",&a[n+2]);
	a[0]=0;
	 
	k=n+2;
	 for(i=0;i<=k;i++)
	 {
		 for(j=i;j<=k;j++)
		 {
			 if(a[i]>a[j])
			 {
				 temp=a[i];
				 a[i]=a[j];
				 a[j]= temp;
			 }
		 }
	 }


    int lr,hloc;
	printf("ENTER 0 FOR LEFT AND 1 FOR RIGHT : ");
	scanf(" %d",&lr);

   if(lr == 0)
	 {
		 for(i=0;i<=n+1;i++)
	      {   
			  if(a[i]==head)
			      hloc=i;
		  }  
			   
		  for(i=hloc;i>=0;i--)
		  {
			    printf("%d-->",a[i]);  
			    if(i!=0)
			    seek=seek+abs(a[i]-a[i-1]); 
		   }    
	    for(i=n+2;i>hloc;i--)
			{
			  printf("%d-->",a[i]); 
			  if(i==n+2)
			     seek=seek+a[i];
			  else 
			     seek=seek+abs(a[i+1]-a[i]); 
	         }
 
       	printf("\n total seek time =%d",seek);
       }

   if(lr == 1)
    {
		for(i=0;i<n+1;i++)
	      {   
			  if(a[i]==head)
			      hloc=i;
		  }  
	    for(i=hloc;i<=n+2;i++)
			{
			  printf("%d-->",a[i]); 
			  if(i<n+2)
			       seek2=seek2+abs(a[i+1]-a[i]); 
			  else
			      seek2=seek2+a[i];
			}
	    for(i=0;i<hloc;i++)
	    {
		   printf("%d-->",a[i]); 
		    if(i!=0)
			  seek2=seek2+abs(a[i]-a[i-1]); 
		}
		           	
      printf("\n total seek time in right = %d",seek2);
    }
	
	}
 
