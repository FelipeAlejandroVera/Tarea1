#include "stdbool.h"
#include <stdio.h>
float numero1;
float numero2;
float resultado;
float *puntero_numero1;
float *puntero_numero2;
float *puntero_resultado;
int operacion;
void introducir_datos();
void calcular();

int main(int argc, char* argv[]) {
  bool salir=false;
  char respuesta;
  numero1=0;
  numero2=0;
  resultado=0;
  puntero_numero1=&numero1;
  puntero_numero2=&numero2;
  puntero_resultado=&resultado;
  operacion=0;
  while(!salir){
    introducir_datos();
    calcular();
    printf("\n¿Quiere salir de la aplicacion? (s/n)");
    scanf("%c",&respuesta);
    scanf("%c",&respuesta);
    if(respuesta == 's' || respuesta == 'S')salir=true,printf("Adios");
  }
  return 0;
}

void introducir_datos() {
  printf("\n\nCALCULADORA\n");
  printf("\nIntroduzca el primer numero ");
  scanf("%f",puntero_numero1);
  printf("\nIntroduzca el segundo numero ");
  scanf("%f",puntero_numero2);
  printf("Introduzca la operacion que quiere efectuar\n");
  printf("\n1 - Sumar");
  printf("\n2 - Restar");
  printf("\n3 - Multiplicar");
  printf("\n4 - Dividir");
  printf("\n5 - Potencia");
  printf("\n6 - Promedio\n");
  printf("\n Operacion ");scanf("%d",&operacion);
}
float potencia(float base, int exponente) {
  float resultado = 1;
  int i;
  for (i = 0; i < exponente; ++i) {
    resultado *= base;
  }
  return resultado;
}
void calcular() {
  switch(operacion) {
    case 1:
     *puntero_resultado = *puntero_numero1 + *puntero_numero2;
     break;
    case 2:
     *puntero_resultado = *puntero_numero1 - *puntero_numero2;
     break;
    case 3:
     *puntero_resultado = *puntero_numero1 * *puntero_numero2;
     break;
    case 4:
     if(*puntero_numero2 != 0) *puntero_resultado = *puntero_numero1 / *puntero_numero2;
     break;
    case 5:
     *puntero_resultado = potencia(*puntero_numero1, (int)*puntero_numero2);
     break;
    case 6:
     *puntero_resultado = (*puntero_numero1 + *puntero_numero2)/2;
     break;
    }
  printf("\nEl resultado de la operacion es: %.3f\n",*puntero_resultado);
}