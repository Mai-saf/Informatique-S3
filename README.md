# Informatique-S3

#define LIGNES 5
#define COLONNES 6
#define FERME 0
#define OUVERT 1
#include<stdio.h>
#include<stdlib.h>
#include<time.h>


int creation_laby(int* laby, float proba){
 for (int i=0; i<LIGNES; i++){
  for (int j=0; j<COLONNES; j++){
   if ((rand()%10 <= proba) || (i==0 && j==1) || (i==1 && j==1) || (i==LIGNES-1 && j==COLONNES-2)){
   *(laby +(i*COLONNES)+j) = OUVERT;
   }
   else {
   *(laby +(i*COLONNES)+j) = FERME;
   // fermer les contours
   }
   if((i==0 && j!=1) || (j==0) || (j==COLONNES-1) || (i==LIGNES-1 
    && j!=COLONNES-2)){
    *(laby +(i*COLONNES)+j) = FERME;
  }
 }
  }
 return(1);
}



void affiche_laby(int * laby){
    for(int i = 0; i<LIGNES; i++){
        for (int j = 0; j< COLONNES; j++){
            if (*(laby +(i*COLONNES)+j) == FERME){
                printf("x");
                
            }else{
                printf(" ");
            }
        }
        printf("\n");
    }
    
}

int main(int argc, char* argv[]){
 int *laby = (int*) calloc(sizeof(int), LIGNES*COLONNES); // tout sur une ligne
 float proba = 9.5;
 creation_laby(laby, proba);
 affiche_laby(laby);
 return(1);
}
