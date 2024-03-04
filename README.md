# Cryptography---19CS412-classical-techqniques


# Caeser Cipher
Caeser Cipher using with different key values

# AIM:

To develop a simple C program to implement Caeser Cipher.

## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include<stdio.h> 
#include<string.h> 
#include<conio.h> 
#include<ctype.h> 
void main()
{
char plain[10], cipher[10]; int key,i,length;
int result; clrscr();
printf("\n Enter the plain text:"); scanf("%s", plain);
printf("\n Enter the key value:"); scanf("%d", &key);
printf("\n \n \t PLAIN TEXt: %s",plain); printf("\n \n \t ENCRYPTED TEXT: ");
for(i = 0, length = strlen(plain); i < length; i++)
{
cipher[i]=plain[i] + key;
if (isupper(plain[i]) && (cipher[i] > 'Z')) cipher[i] = cipher[i] - 26;
if (islower(plain[i]) && (cipher[i] > 'z')) cipher[i] = cipher[i] - 26;
printf("%c", cipher[i]);
}
printf("\n \n \t AFTER DECRYPTION : "); for(i=0;i<length;i++)
{
plain[i]=cipher[i]-key; if(isupper(cipher[i])&&(plain[i]<'A')) plain[i]=plain[i]+26; if(islower(cipher[i])&&(plain[i]<'a')) plain[i]=plain[i]+26; printf("%c",plain[i]);
}
getch();
}
```
## OUTPUT:
![a1](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/119559366/6390595e-4d81-451b-b022-92f1d361b612)
## RESULT:
The program is executed successfully

---------------------------------

# PlayFair Cipher
Playfair Cipher using with different key values

# AIM:

To develop a simple C program to implement PlayFair Cipher.

## DESIGN STEPS:

### Step 1:

Design of PlayFair Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include<stdio.h> 
#include<conio.h> 
#include<string.h> 
#include<ctype.h> 
#define MX 5
void playfair(char ch1,char ch2, char key[MX][MX])
{
int i,j,w,x,y,z; FILE *out;
if((out=fopen("cipher.txt","a+"))==NULL)
{
printf("File Currupted.");
}
for(j=0;j<MX;j++)
{
if(ch1==key[i][j])
{
w=i; x=j;
}
else if(ch2==key[i][j])
{
y=i; z=j;

//printf("%d%d %d%d",w,x,y,z); if(w==y)
{
x=(x+1)%5;z=(z+1)%5;
printf("%c%c",key[w][x],key[y][z]);
fprintf(out, "%c%c",key[w][x],key[y][z]);
}
else if(x==z)
{
w=(w+1)%5;y=(y+1)%5;
printf("%c%c",key[w][x],key[y][z]);
fprintf(out, "%c%c",key[w][x],key[y][z]);
printf("%c%c",key[w][z],key[y][x]);
fprintf(out, "%c%c",key[w][z],key[y][x]);

fclose(out);
}
void main()
{
int i,j,k=0,l,m=0,n;
char   key[MX][MX],keyminus[25],keystr[10],str[25]={0}; char alpa[26]={'A','B','C','D','E','F','G','H','I','J','K','L'
,'M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z'}
;
clrscr(); printf("\nEnter key:"); gets(keystr);
printf("\nEnter the plain text:"); gets(str);
n=strlen(keystr);
//convert the characters to uppertext for (i=0; i<n; i++)
{
if(keystr[i]=='j')keystr[i]='i';
else if(keystr[i]=='J')keystr[i]='I'; keystr[i] = toupper(keystr[i]);
}
//convert all the characters of plaintext to uppertext for (i=0; i<strlen(str); i++)
{
j=0;
}
if(str[i]=='j')str[i]='i';
else if(str[i]=='J')str[i]='I'; str[i] = toupper(str[i]);

for(i=0;i<26;i++)
{
for(k=0;k<n;k++)
{
if(keystr[k]==alpa[i]) break;
else if(alpa[i]=='J') break;
}
if(k==n)
{
keyminus[j]=alpa[i];j++;
}
}
//construct key keymatrix k=0;
for(i=0;i<MX;i++)
{
for(j=0;j<MX;j++)
{
if(k<n)
{
key[i][j]=keystr[k]; k++;}
else
{
key[i][j]=keyminus[m];m++;
}
printf("%c ",key[i][j]);
}
printf("\n");
}
printf("\n\nEntered text :%s\nCipher Text :",str); for(i=0;i<strlen(str);i++)
{
if(str[i]=='J')str[i]='I'; if(str[i+1]=='\0') playfair(str[i],'X',key); else
{
if(str[i+1]=='J')str[i+1]='I'; if(str[i]==str[i+1]) playfair(str[i],'X',key);
else
{
playfair(str[i],str[i+1],key);i++;
}}
}
getch();
}
```
## OUTPUT:
![a2](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/119559366/8d44fb95-cad7-4dca-8ee2-a42c1d6f442a)

## RESULT:
The program is executed successfully


---------------------------

# Hill Cipher
Hill Cipher using with different key values

# AIM:

To develop a simple C program to implement Hill Cipher.

## DESIGN STEPS:

### Step 1:

Design of Hill Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include<stdio.h> 
#include<conio.h> 
#include<string.h> 
int main(){
unsigned int a[3][3]={{6,24,1},{13,16,10},{20,17,15}};
unsigned int b[3][3]={{8,5,10},{21,8,21},{21,12,8}};
int i,j, t=0;
unsigned int c[20],d[20]; char msg[20];
clrscr();
printf("Enter plain text\n "); scanf("%s",msg); for(i=0;i<strlen(msg);i++)
{	c[i]=msg[i]-65;
printf("%d ",c[i]);
}
for(i=0;i<3;i++)
{	t=0;
for(j=0;j<3;j++)
{
t=t+(a[i][j]*c[j]);
}
d[i]=t%26;
}
printf("\nEncrypted Cipher Text :"); for(i=0;i<3;i++)
printf(" %c",d[i]+65); for(i=0;i<3;i++)
{
t=0;
for(j=0;j<3;j++)
{
t=t+(b[i][j]*d[j]);
}
c[i]=t%26;
}
printf("\nDecrypted Cipher Text :"); for(i=0;i<3;i++)
printf(" %c",c[i]+65); getch();
return 0;
}
```
## OUTPUT:
![Picture1](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/119559366/17cdfbe2-ece8-44c8-8ae6-c581aaeab6d3)

## RESULT:
The program is executed successfully

-------------------------------------------------

# Vigenere Cipher
Vigenere Cipher using with different key values

# AIM:

To develop a simple C program to implement Vigenere Cipher.

## DESIGN STEPS:

### Step 1:

Design of Vigenere Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include<stdio.h> 
#include<conio.h>
#include<ctype.h> 
#include<string.h> 
void encipher(); 
void decipher(); 
void main()
{
int choice; clrscr(); while(1)
{
printf("\n1. Encrypt Text"); printf("\t2. Decrypt Text"); printf("\t3. Exit"); printf("\n\nEnter Your Choice : "); scanf("%d",&choice);
if(choice == 3) exit(0);
else if(choice == 1) encipher();
else if(choice == 2) decipher();
else
printf("Please Enter Valid Option.");
}
}
void encipher()
{
unsigned int i,j;
char input[50],key[10]; printf("\n\nEnter Plain Text: ");
scanf("%s",input); printf("\nEnter Key Value: "); scanf("%s",key);
printf("\nResultant Cipher Text: "); for(i=0,j=0;i<strlen(input);i++,j++)
{
if(j>=strlen(key))
{	j=0;
}
printf("%c",65+(((toupper(input[i])-65)+(toupper(key[j])- 65))%26));
}}
void decipher()
{
unsigned int i,j;
char input[50],key[10]; int value;
printf("\n\nEnter Cipher Text: "); scanf("%s",input);
printf("\n\nEnter the key value: "); scanf("%s",key);
for(i=0,j=0;i<strlen(input);i++,j++)
{
if(j>=strlen(key))
{	j=0;	}
value = (toupper(input[i])-64)-(toupper(key[j])-64); if( value < 0)
{ value = value * -1;
}
printf("%c",65 + (value % 26));
}}
```
## OUTPUT:
![Picture2](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/119559366/8d2dfd23-358e-4332-bc87-c1b4df6cc5a6)

## RESULT:
The program is executed successfully

-----------------------------------------------------------------------

# Rail Fence Cipher
Rail Fence Cipher using with different key values

# AIM:

To develop a simple C program to implement Rail Fence Cipher.

## DESIGN STEPS:

### Step 1:

Design of Rail Fence Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include<stdio.h> 
#include<conio.h> 
#include<string.h> 
void main()
{
int i,j,k,l;
char a[20],c[20],d[20]; clrscr();
printf("\n\t\t RAIL FENCE TECHNIQUE"); printf("\n\nEnter the input string : "); gets(a);
l=strlen(a);

/*Ciphering*/ for(i=0,j=0;i<l;i++)
{
if(i%2==0) c[j++]=a[i];
}
for(i=0;i<l;i++)
{
if(i%2==1) c[j++]=a[i];
}
c[j]='\0';
printf("\nCipher text after applying rail fence :"); printf("\n%s",c);

/*Deciphering*/ if(l%2==0)
k=l/2;
else
k=(l/2)+1;
for(i=0,j=0;i<k;i++)
{
d[j]=c[i]; j=j+2;
}
for(i=k,j=1;i<l;i++)
{
d[j]=c[i]; j=j+2;
}
d[l]='\0';
printf("\nText after decryption : "); printf("%s",d);
getch();
}
```
## OUTPUT:
![o](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/119559366/f6ec83fd-3084-4bd1-93a3-feb40fa5696e)

## RESULT:
The program is executed successfully
