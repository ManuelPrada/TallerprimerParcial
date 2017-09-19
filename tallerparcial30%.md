# TallerprimerParcial

1. Describa la Taxonomía de Flynn

   La taxonomía de Flynn se clasifica en cuatro arquitecturas de computadoras, que se basan en el número de instrucciones 	     concurrentes y en los flujos de datos:
 
  * **SISD:** Una instrucción, un dato: se aplica en monoprocesadores
  * **SIMD:** Una instrucción, multiples datos: se aplica en procesadores vectoriales y matriciales
  * **MISD:** Multiples instrucciones, un dato: no se utiliza
  * **MIMD:** Multiples instrucciones, multiples datos: se utiliza en memorias compartidas con SMP, NUMA y con memoria distiuida con         cluster
  
 
 2. Diga cuáles son los 4 principios del diseño
 
   * La simplicidad favorece la regularidad
   * Entre más pequeño más rápido
   * Hacer el caso común más rápido
   * Buenos diseños demandandan grandes compromisos
   
   
 3. Explique los tres formatos que se usan en la arquitectura SPARC V8, y que instrucciones usan los formatos correspondientes a la arquitectura SPARC V8
 
* **Formato 1:** Este formato se utiliza para las instrucciones Call
 
 			| op |  Disp 30 |
	
* **Formato 2:** Este formato lo utilizan las instruciones Branches(Bicc, FBfcc, CBccc), SETHI

			| op | rd | op2 | imm 22 |
			| op |  a | cond | op2 | disp22 |

* **Formato 3:** Este formato lo utilizan las instrucciones aritmeticas, de memorias lógicas, shift y jump and link

                        | op | rd | op3 | rs1 | i=1 | simm 13 |
			| op | rd | op3 | rs1 | 1=0 | unused (zero) | rs2 |
		
			

4. Explique cómo inicializar un valor grande, que ocupe más de 13 bits, en la arquitectura **SPARC V8**.

 * El valor grande en la arquitectura sparc v8 que ocupe mas de 13 bits se iniciliza
  con la instruccion **SETHI**, ya que esto nos permite almacenar hasta 22 bits en el formato 2. 
  
  **El lenguaje ensamblador que se utiliza es :**
 
```
 * Sethi const22,rd
 * Sethi %hi(value),rd

 
```
 
* Ejemplo :  15600
 
```
 |00000000000000000011110011110000|      0000000000000000001111 22 mas signnificativos  15
                                       
				         0011110000 = Or = 240
					 
|00|10011|100|0000000000000000001111|

Sethi 15,%l3
Or %l3,240,%l0
 
```


5. Como puedo reescribir la instrucción **(OR y SUBcc)** cuando inicializo y  comparó 2 registros.

 
``` 

  * La instruccion OR se reescribe con la intruccion MOV
  
  OR %g0, 3 , %l2   ==  MOV 3, %l2
  
  * la instruccion SUBcc se puede reescribe con la función CMP
  
  SUbcc %l0,%l1,g0 ==  CMP %l0,%l1
  
``` 
6. ¿Qué instrucciones utilizan el delay slot antes de saltar?

  * BRANCH
  * CALL
  * JUMP AND LINK

7. ¿Qué significa el bit **a**, en el formato 2 de las instrucciones **BRANCH**?
  
  * Si la instruccion branch tiene a=0 es por que ejecuta por debajo y luego salta.
  * Si la instruccion branch tiene a=1 no ejecuta la instruccion que esta por debajo
  solo salta.
  
8. ¿Por que la instrucción **CALL** utilizar el registro %o7 ---> registro 15.?
```
  Lo utuliza  para guardar la direccion a donde devera volver el procedimimento llamado 
  al terminar su ejecucion. 
  
  ```
  9. convertir el programa en lenguaje de máquina a lenguaje ensamblador y luego a lenguaje de alto nivel el siguiente programa:
```
10100000000100000010000000000101
10100010000100000011111111111010
10010000000001000100000000010000
```
   
*  **|10|10000|000010|00000|1|0000000000101|**
```


formato 3 = Op[10].
%l0 = rd[10000]. 
OR = op3[000010].
%g0 = rs1[00000].
imm = 5 =[0000000000 101].

lenguage ensamblador.

 * MOV 5,%l0
 
```
* **|10|10001|000010|00000|1|1111111111010|**
```

formato 3 = Op[10].
%l0 = rd[10001]. 
OR = op3[000010].
%g0 = rs1[00000].
imm = -6 = rd2[1111111111010].

lenguage ensamblador.

 * MOV -6,%l1
 
```
* **|10|01000|000000|10001|0|00000000|10000|**
 
 ```
formato 3 =  Op[10].
%o0 = Rd[01000].
Add = Op3[000000].
%L1 = Rs1[10001].
imm = 0 =i[o].
%L0 = Rs2(10000)

lenguaje ensamblador
ADD %l1,%l0,%O0
 ```
 
  
  
  * Lenguaje de alto nivel 
  
  int main():{
  
    int x=5;
    int y=-6;
    
   return x+y;
   }
   
   
  10. Convierta el siguiente código a lenguaje ensamblador, máquina **SPARC V8** y hexadecimal.

```
a).
c
 int main(){
 int a = 8;
 int b = -16800;
 int c = 33; 
 if((a+b)<=b*32){
 	c=a+(b*2);
	}
else{
	return b;
}
	return a+c;
}
 ```
  ```
numero negativo 
-16800
 
 lo pasamos a positivo 
 
 16800
 
  |00000000000000000100000110100000|     1111111111111111101111 = 22 bits mas significativos = 4194287      
  |11111111111111111011111001011111|
  |                               1|     1001100000 = Or = 608
  ----------------------------------
  |11111111111111111011111001100000|
  
  
   a).%l0
   
   b).%l1
   
   c).%l2
   
 main=
 
 0x0000 mov 8 , %l0          |10|10000|000010|00000|1|0000000001000|
 0x0004 sethi 4194287 , %l1  |00|10001|100|1111111111111111101111|
 0x0008 or %l1 ,608,%l1      |10|10001|000010|10001|1|0001001100000|
 0x000c mov 33,%l2           |10|10010|000010|00000|1|0000000100001|
 0x0010 add %l0,%l1,%l3      |10|10011|000000|10000|0|00000000|10001|
 0x0014 SLL %l3,5,%l4        |10|10100|100101|10011|1|00101|
 0x0018 cmp %l3,%l4          |10|00000|010100|10011|0|00000000|10100|
 0x001c Branch G. a TRUE     |00|1|1010|010|0000000000000000000100|
 0x0020 SLL %l1,1,%l5        |10|10101|100101|10001|1|00001|
 0x0024 add %l0,%l5,%l2      |10|10010|000000|10000|0|00000000|10101|
 0x0028 BA a Exit            |00|1|1000|010|0000000000000000000010|
 
etiqueta
  0x002c mov,%l1,%O0         |10|01000|000010|O0000|0|00000000|10001|
  
 salir
  0x0030 add %l0,%l2,%O1     |10|01001|000000|10000|0|00000000|10010|
 
  
   ```
  ```
  b
  
  
 c.
int main(){
	int a = 8;
	int b = -10;
	if(a!=b){
		return c/8;
}
else{
	return b;
}
}

numero negativo 
 -10

nuero positivo 
10 

|00000000000000000000000000001010|       
|00000000000000000100000110100000|      
|11111111111111111111111111110101|
|                               1|
|--------------------------------|				
|11111111111111111111111111110110|

a = %l0
b = %l1
c = %l2


main=

0x0000 mov 8,%lo        |10|10000|000010|00000|1|0000000001000|
0x0004 mov -10,%l1      |10|10001|000010|00000|1|1111111110110|
0x0008 mov 0,%l2        |10|10010|000010|00000|1|0000000000000|
0x000c cmp %l0,%l1      |10|00000|010100|10000|0|00000000|10001|
0x0010 BE a TRUE        |00|1|0001|010|0000000000000000000011|
0x0014 SRL %l2,3,%O0    |10|01000|100110|10010|1|00011|
0x0018 BA a Exit        |00|1|1000|010|0000000000000000000010|
TRUE
0x001c mov %l1,%O1      |10|01001|000010|00000|0|00000000|10001|
Exit
0x0020 NOP              |00|00000|100|0000000000000000000000|

```
```
 c
int main(){
	int a = -21180;



|0000000000000000101001010111100|   1111111111111111101011 22 mas significativos es=4194283
|1111111111111111010110101000011|     
|                              1|    101000100 = Or  = 324
|-------------------------------|
|1111111111111111101011101000100|                                 


c

a = %l0
main:
0x0000 sethi 4194283,%l0  |00|10000|100|1111111111111111101011|
0x0004 or %l0,324,%l0     |10|10000|000010|10000|1|0000101000100|
 
``` 
 
 ```

11. Convierta el siguiente código a lenguaje ensamblador, máquina **SPARC V8** y hexadecimal.
 ```c
int test(int a, int b, int c){
	int z;
	z = a - b + c*4;
	return z + 2;
}

int main(){
	int p = 4, y = 2, c = -128;
	int x = test(p,y,c);
	return x + 45;
}
 ```
 
  x = %i0 y = %i1 z = %i2 c = %L0  a = %L1    
  
  
  



