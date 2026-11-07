#include <stdio.h>
#include <time.h>
#include <unistd.h>
#include <stdlib.h>
void afficher (char m[9][9],int* nr,int nx,int r, int x){
    int i, j;
    system("color");
    printf("i/j");
    for(i=0; i<9; i++){
        printf("\t%d", i);
    }
    printf("\n");
    for(i=0; i<9; i++){
        printf("%d", i);
        for(j=0; j<9; j++){
        	if(m[i][j]=='V'){
            printf("\t \x1b[32m %c \x1b[0m", m[i][j]);
			} 
            else{
            printf("\t \x1b[31m %c \x1b[0m", m[i][j]);
        }
        }
        printf("\n");
    }
    printf("\n n%d=%d \t\t n%d=%d \n\n",r,nr,x,nx);
}
void play(char m[9][9],int* nr,int* nx,int r, int x){
	int ix,jx,ir,jr,i;   
	afficher(m,nr,nx,r,x);
	do{
		printf("la jouer %d,donner postion i et j de chachette",x);
		printf("\n i=");
		scanf("%d",&ix);
		printf("j=");
		scanf("%d",&jx);
	}while( ix <0 || ix>8 || jx<0 || jx>8 || m[ix][jx]== 'F');
	system("cls");
	afficher(m,nr,nx,r,x);
	do{
		printf("la jouer %d,donner postion i et j de rechercher a chachette",r);
		printf("\n i=");
		scanf("%d",&ir);
		printf("j=");
		scanf("%d",&jr);
	}while( ir<0 || ir>8);
	if(ix==ir && jx==jr){
		(*nx)--;
		printf("la positon valid \n ");
	    printf("\n - Point perdu pour joueur %d !\n", x);
		for (i=0;i<9;i++){
			m[ir][i]='F';
			m[i][jr]='F';
		}
	}
	else{
		printf("la positon invalid \n "); 
		m[ir][jr]='F';
	}
}
void draw_heart() {
    int size = 15;
    int i, j;
    system("color");
    printf("\x1b[31m");
    for (i = size / 2; i <= size; i += 2) {
        for (j = 1; j < size - i; j += 2) {
            printf(" ");
        }
        for (j = 1; j <= i; j++) {
            printf("*");
        }
        for (j = 1; j <= size - i; j++) {
            printf(" ");
        }
        for (j = 1; j <= i; j++) {
            printf("*");
        }
        printf("\n");
    }

    for (i = size; i >= 1; i--) {
        for (j = i; j < size; j++) {
            printf(" ");
        }
        for (j = 1; j <= (i * 2) - 1; j++) {
            printf("*");
        }
        printf("\n ");
    }
    printf("\x1b[0m");
}

int main(){
    int i, j,n1=3,n2=3,x;
    char m[9][9];   
system("color");
printf(" \n \n \n");
printf("\x1b[32m");
printf("\t                 *** \n");
printf("\t                 *** \n");
printf("\t                 *** \n");
printf("\t                 *** \n");
printf("\t                 ***  \n");
printf("\t                 ***  \n");
printf("\t                 ***  \n");
printf("\t                 ***  \n");
sleep(2);
system("cls");
printf(" \n \n \n");
printf("\t         ***************\n");
printf("\t                       * \n");
printf("\t                       * \n");
printf("\t                       * \n");
printf("\t         ***************\n");
printf("\t         *  \n");
printf("\t         *  \n");
printf("\t         *  \n");
printf("\t         ****************\n");
sleep(2);
system("cls");
printf(" \n \n \n");
printf("\t         ***************\n");
printf("\t                       *\n");
printf("\t                       * \n");
printf("\t                       *  \n");
printf("\t         ***************\n");
printf("\t                       *  \n");
printf("\t                       *  \n");
printf("\t                       * \n ");
printf("\t         ***************\n");
printf("\x1b[0m \x1b[31m");
sleep(2);
system("cls");
printf(" \n \n \n");
printf("\t         *****************     ****************\n");
printf("\t         *                     **            **\n");
printf("\t         *                     **            **\n");
printf("\t         *                     **            **\n");
printf("\t         *      *********      **            **\n");
printf("\t         *               *     **            **\n");
printf("\t         *               *     **            **\n");
 printf("\t         *               *     **            **\n");
printf("\t         ***************       ****************\n");
printf("\x1b[0m");
sleep(2);
system("cls");
printf(" \n \n \n");
    for(i=0; i<9; i++){
        for(j=0; j<9; j++){
            m[i][j] = 'V';
        }
    }
    srand(time(NULL));
    x=1;
    if ((rand()%2)==1)
    x=-1;
    while(n1>0 && n2>0){
    	if (x>0){
    		play(m,n2,n1,2,1);    		
		}
		else
		{
    		play(m,n1,n2,1,2);
		}
		x=x*-1;
	sleep(4);
	system("cls");
	}
	draw_heart();
	
	if (n1>n2){   
		printf("\tla jouer 1 est ganant ");
	}
	else{
		printf("\t la jouer  2 est ganant ");
	}
    return 0;
}
