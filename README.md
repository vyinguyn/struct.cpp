# struct.cpp
#include <stdio.h>
#include <stdlib.h>
#define MAX 100
struct sinhvien{
	int masv;         
	char hoten[50];
	float TK;
	float GK;
	float CK;
	float TH;
	float DTB;     
	}; sinhvien SV[MAX];

void nhapmangSV(sinhvien SV[], int &n)
{
     for (int i=0;i<n;i++)
     {
         printf("\nNhap MSSV thu : %d\t",i+1 );
         printf("\nMSSV: ");        scanf("%d", &SV[i].masv);
         printf("\nHo ten SV: ");
         fflush(stdin);
         gets(SV[i].hoten);
         printf("\nDiem TK : ");scanf("%f", &SV[i].TK);
         printf("\nDiem GK : ");scanf("%f", &SV[i].GK);
         printf("\nDiem CK : ");scanf("%f", &SV[i].CK);
         printf("\nDiem TH : ");scanf("%f", &SV[i].TH);
     }
}


void xuatmangSV(sinhvien SV[], int n)
 {
     for(int i=0;i<n;i++)
     {
     printf("\nSinh vien thu %d", i+1);
     printf("\n");
     printf("\nMSSV sinh vien:%d", SV[i].masv);
     printf("\nHo ten sinh vien:");
	 printf(SV[i].hoten);       
     printf("\nDiem TK: %.2f", SV[i].TK);
     printf("\nDiem GK: %.2f", SV[i].GK);
     printf("\nDiem CK: %.2f", SV[i].CK);               
     printf("\nDiem TH: %.2f", SV[i].TH);                       
     SV[i].DTB=((((2*SV[i].TK+3*SV[i].GK+5*SV[i].CK)/10)*2)+SV[i].TH)/3;
     printf("\nDiem TB: %.2f", SV[i].DTB);
     printf("\n");
   }
   
}

void  xuatSVHL(sinhvien SV[], int n)
{

    int k=0;
    for(int i=0;i<n;i++)
    {
		SV[i].DTB=((((2*SV[i].TK+3*SV[i].GK+5*SV[i].CK)/10)*2)+SV[i].TH)/3;
		if(SV[i].DTB<4.0)
        {  
		printf("\nSTT\tMSSV\tHo ten\t\t\tDiem TB\n");         
		k++;
		printf("%d",k);
		printf("\t%d", SV[i].masv);
		printf("\t");
		printf(SV[i].hoten);    
		printf("\t\t\t%.2f\n", SV[i].DTB);                   
        }
        else 
        printf("\tKhong co sinh vien hoc lai \n");
     }
}
void  xuatDSDT(sinhvien SV[], int n)
{

    int k=0;
    printf ("***Danh sach diem PPLT***\n");
    printf ("|=======================================================================|\n");
    for(int i=0;i<n;i++)
    {
		SV[i].DTB=((((2*SV[i].TK+3*SV[i].GK+5*SV[i].CK)/10)*2)+SV[i].TH)/3;	  
		printf("\nSTT\tHO TEN\tMA SV\t TK\t GK\t CK\t TH\t Diem TB\t Ghi Chu\n");         
		k++;
		printf("%d",k);
		printf("\t");
		printf(SV[i].hoten); 
		printf("\t%d", SV[i].masv);
		printf("\t%.2f", SV[i].TK); 
		printf("\t%.2f", SV[i].GK);
		printf("\t%.2f", SV[i].CK);
		printf("\t%.2f", SV[i].TH);   
		printf("\t%.2f", SV[i].DTB);
		if(SV[i].DTB<4.0)
        {
		printf("\t Hoc lai\n");                   
        }
        else 
        printf("\t   \n");
     }
}
int xuatds(sinhvien SV[],int n)
{
	printf("**Danh sach da nhap**\n");
	printf("||---------------------------------------------------------------------||\n");
	printf("||Stt\tMSSV\tHo va ten\tDiem GK\t	Diem CK\t	Diem TB||\n");
	printf("||---------------------------------------------------------------------||\n");
	printf("||---------------------------------------------------------------------||\n");
	for(int i=0;i<n;i++)
		{
	printf("|| ");
	printf("%d ",i+1);
	printf("\t%d ",SV[i].masv);
	printf("\t%s ",SV[i].hoten);
	printf("\t\t%.2f ",SV[i].GK);
	printf("\t\t%.2f ",SV[i].CK);
	printf("\t\t%.2f ||\n",SV[i].DTB);
		}
	printf("||----------------------------------------------------------------------||\n");
}
void timSVtheoma(sinhvien SV[], int n)
{
    int ma;
    printf("\nNhap MSSV can tim: ");
    scanf("%d",&ma);
    for(int i=0;i<n;i++)
    {
     if(SV[i].masv==ma)
       {
       printf("\n");
       printf("\nMSSV :%d", SV[i].masv);
       printf("\nHo ten : %s",SV[i].hoten);    
       printf("\nDiem TK: %.2f", SV[i].TK);
       printf("\nDiem GK: %.2f", SV[i].GK);
       printf("\nDiem CK: %.2f", SV[i].CK);               
       printf("\nDiem TH: %.2f", SV[i].TH);                       
       printf("\nDiem TB: %.2f", SV[i].DTB);
       printf("\n");
       }
     }
 }
void swap(sinhvien &a,sinhvien &b)
{
    sinhvien t;
     t=a;
     a=b;
     b=t;
}

void sapxep(sinhvien SV[], int n)
 {
    for(int i=0;i<n;i++)
        for(int j=0;j<n-1;j++)
       {
            if(SV[i].DTB>SV[j].DTB)
                 swap(SV[i], SV[j]);
       }  
 }
  
int main()
{
	int n,x;
	printf("Nhap so sinh vien:\n");
	scanf("%d",&n);
	nhapmangSV(SV,n);

	while(1)
	{
	printf("\t---------------Menu---------------\n");
	printf("1. Hien thi danh sach sinh vien hoc lai.\n");
	printf("2. Tim sinh vien.\n");
	printf("3. Danh sach sinh vien da sap xep.\n");
   	printf("4. Danh sach diem thi PPLT.\n");
   	printf("5. Exit.\n");
   	printf("\t Chon 1 trong 5 tuy chon tren\n");
   	scanf("%d",&x);
   	switch(x)
   	{
   	case 1:
			printf("\nDanh sach sinh vien hoc lai:\n");
   			xuatSVHL(SV,n);
   			xuatds(SV,n);
   			break;
	case 2:
			printf("\nTim sinh vien theo ma\n");
			timSVtheoma(SV,n);
			break;
	case 3:
  			printf("\nMang SV sau khi sap xep:\n");
			sapxep(SV,n);
    		xuatmangSV(SV,n);
    		break;
	case 4:
		printf("\n\t Danh sach diem thi PPLT\n");
		xuatDSDT(SV,n);
		break;
	case 5:
		return 0;
   	}
	}
 }

                                                                                                                                  
