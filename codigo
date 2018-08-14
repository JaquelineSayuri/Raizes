/*  ENTRADA DE DADOS: Grau do polinômio, coeficientes.
	SAÍDA DE DADOS: Raízes do polinômio.
	PROCESSAMENTO:  Perguntar o grau do polinômio;
					Perguntar os coeficientes;
					Encontrar as possíveis raízes;
					Fazer divisão de polinômios pelo algoritmo de Briot-Ruffini para descobrí-las;
					Printá-las.
*/			

#include<stdio.h>
#include<locale.h>
#include<math.h>

int main(){
	
	setlocale(LC_ALL,"");
	
	int opcao;
		
	do{
		int grau;											// Informa o grau do polinômio
		printf("\n Informe o grau do polinômio: ");
		scanf("%d",&grau);
		
		int i=0;											// Cria um vetor com os coeficientes
		int coef[grau+1];
		printf(" Informe os coeficientes:\n");
		while(i<=grau){
			scanf("%d",&coef[i]);
			i++;
		}
		
		int x=0;											// Descobre o tamanho e cria um vetor que conterá os divisores do termo independente
		i=coef[grau];
		if(i<0){
			i=i*-1;
			while(i>=coef[grau]){
				if(i!=0){
					if(coef[grau]%i==0) x++;
				}
			i--;
			}	
		}
		else{
			while(i>=-coef[grau]){
				if(i!=0){
					if(coef[grau]%i==0) x++;
				}
				i--;
			}
		}
		float p[x];
		
		int np=x;											// Preenche o vetor com os divisores do termo independente
		i=coef[grau];
		if(i<0){
			i=i*-1;
			while((i>=coef[grau])&&(x>=0)){
			if(i!=0){
				if(coef[grau]%i==0){
					p[x-1]=i;
					x--;
				}
			}
			i--;
			}
		}
		else{
			while((i>=-coef[grau])&&(x>=0)){
			if(i!=0){
				if(coef[grau]%i==0){
					p[x-1]=i;
					x--;
				}
			}
			i--;
			}	
		}
	
		x=0;												// Descobre o tamanho e cria um vetor que conterá os divisores do termo de maior grau
		i=coef[0];
		if(i<0){
			 i=i*-1;
			 while(i>=coef[0]){
				if(i!=0){
					if(coef[0]%i==0) x++;
				}
				i--;
			}	
		}
		else{
			while(i>=-coef[0]){
				if(i!=0){
					if(coef[0]%i==0) x++;
				}
				i--;
			}
		}
		float q[x];
	
		int nq=x;											// Preenche o vetor com os divisores do termo de maior grau
		i=coef[0];
		if(i<0) i=i*-1;
		while((i>=-coef[0])&&(x>=0)){
			if(i!=0){
				if(coef[0]%i==0){
					q[x-1]=i;
					x--;
				}
			}
			i--;
		}
		
		int ii=0, c, nr=0;									// Testa todas as possíveis raízes pelo dispositivo de Briot-Ruffini, conta quantas são
		float pq, y;										// e cria um vetor para armazená-las
		i=0;
		while(ii<=np-1){
			c=0;
			if(i<=nq-1){
				pq=p[ii]/q[i];
				y=pq*coef[c]+coef[c+1];
				c++;
				while(c<grau){
					y=pq*y+coef[c+1];
					c++;
				}
				if(y==0) nr++;
				i++;
			}
			else{
				ii++;
				i=0;
			}
		}
		float r[nr];
		
		int z=0;
		i=0; ii=0;											// Preenche o vetor com as raízes
		while(ii<=np-1){
			c=0;
			if(i<=nq-1){
				pq=p[ii]/q[i];
				y=pq*coef[c]+coef[c+1];
				c++;
				while(c<grau){
					y=pq*y+coef[c+1];
					c++;
				}
				if(y==0){
					r[z]=pq;
					z++;
				}
				i++;
			}
			else{
				ii++;
				i=0;
			}
		}
		
		int v=1, t=0;										// Printa as raízes sem repetí-las
		printf("\n As raízes são: %f",r[0]);
		while(v<nr){
			z=v;
			while((z<nr)&&(z!=0)){
				if(r[z]==r[z-1]) t=1;
				z--;
			}
			if(t==0) printf(" %f",r[v]);
			v++;
		}
		
		printf("\n\n Deseja reiniciar o programa? sim(1) não(0) ");
		scanf("%d",&opcao);
		
	}while(opcao==1);
	
	return 0;
}
