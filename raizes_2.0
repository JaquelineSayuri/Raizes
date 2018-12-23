#include<stdio.h>
#include<locale.h>
#include<math.h>
#include<stdlib.h>

int descobre_divisores(int grau_inicial, int indice, int grau, float coef[grau_inicial*2+1]){	
    int tam=0;
    int i=sqrt(pow(coef[indice],2));								// Descobre a quantidade de divisores do termo do polinômio
    while(i>=-sqrt(pow(coef[indice],2))){
		if(coef[indice]==0){
			tam=20;
			break;
		}
        if(i!=0 && (int)(coef[indice])%i==0) tam++;
		i--;
    }
    return tam;
}

void preenche_divisores(int grau_inicial, int indice, int grau, float coef[grau_inicial*2+1], int num_div, int tam, int div_term[tam]){
	int i=sqrt(pow(coef[indice],2)), ii=0;
	while(i>=-sqrt(pow(coef[indice],2)) && ii<=num_div){			// Preenche um vetor com os divisores do termo do polinômio
		if(coef[indice]==0){
			div_term[ii]=0;
			break;
		}
		if(i!=0 && (int)(coef[indice])%i==0){
			div_term[ii]=i;
			ii++;
		}
		i--;
	}
}

void reposiciona(int tam, float vetor[tam], int grau){
	for(int i=0; i<=grau; i++)										// Traz elementos de um vetor para as primeiras posições
		vetor[i]=vetor[i+grau+2];
}

void descobre_raiz(int grau_inicial, int num_div_i, int num_div_d, int tam1, int tam2, int *j, int *grau, int *c, int div_term_i[tam1], int div_term_d[tam2], float coef[grau_inicial*2+1], float raizes[grau_inicial]){
	int i, ii;
	float y, pos_raiz;
	i=ii=0;
	while(ii<=num_div_i-1){
		(*c)=0;														// Descobre uma raiz pelo dispositivo de Briot-Ruffini e a armazena
		if(i<=num_div_d-1){
			coef[(*grau)+1]=coef[0];
			pos_raiz=div_term_i[ii]/div_term_d[i];
			coef[(*c)+(*grau)+2]=y=pos_raiz*coef[(*c)]+coef[(*c)+1];
			(*c)++;
			while((*c)<(*grau)){
				coef[(*c)+(*grau)+2]=y=pos_raiz*y+coef[(*c)+1];
				(*c)++;
			}
			if(y==0){
				raizes[(*j)]=pos_raiz;
				(*grau)--;
				break;
			}
			i++;
		}
		else{
			ii++;
			i=0;
		}
	}
}

void main(){
	setlocale(LC_ALL,"");
	
	int opcao;
		
	do{
		int grau, grau_inicial, i;
		printf("\n Informe o grau do polinômio: ");						// Obtem o grau do polinômio
		scanf("%d",&grau);
		grau_inicial=grau;
		
		float coef[grau*2+1];
		printf(" Informe os coeficientes:\n");							// Obtem os coeficientes
		for(i=0;i<=grau;i++)
			scanf("%f",&coef[i]);
		
		int num_div_i=descobre_divisores(grau_inicial, grau, grau, coef), tam1=num_div_i*2+1, div_term_i[tam1];
		int num_div_d=descobre_divisores(grau_inicial, 0, grau, coef), tam2=num_div_d*2+1, div_term_d[tam2];
		preenche_divisores(grau_inicial, grau, grau, coef, num_div_i, tam1, div_term_i);
		preenche_divisores(grau_inicial, 0, grau, coef, num_div_d, tam2, div_term_d);

		int  j, c;
		float raizes[grau];

		for(j=0; j<grau_inicial; j++){
			descobre_raiz(grau_inicial, num_div_i, num_div_d, tam1, tam2, &j, &grau, &c, div_term_i, div_term_d, coef, raizes);
			reposiciona(grau_inicial*2+1, coef, grau);					// Simplifica o polinômio a cada raiz descoberta usando Briot-Ruffini

			num_div_i=descobre_divisores(grau_inicial, grau, grau, coef);
			num_div_d=descobre_divisores(grau_inicial, 0, grau, coef);

			preenche_divisores(grau_inicial, grau, grau, coef, num_div_i, tam1, div_term_i);
			preenche_divisores(grau_inicial, 0, grau, coef, num_div_d, tam2, div_term_d);
		}

		printf("\nAs raízes são:");
		for(i=0;i<grau_inicial;i++)										// Printa as raízes
			printf(" %.2f",raizes[i]);
		
		printf("\n\n Deseja reiniciar o programa? sim(1) não(0) ");
		scanf("%d",&opcao);
		
	}while(opcao==1);
}
