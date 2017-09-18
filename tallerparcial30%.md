# TallerprimerParcial

4. Explique cómo inicializar un valor grande, que ocupe más de 13 bits, en la arquitectura **SPARC V8**.

 * El valor grande en la arquitectura sparc v8 que ocupe mas de 13 bits se iniciliza
  con la instruccion **SETHI**, ya que esto nos permite almacenar hasta 22 bits en el formato 2. 
  
  **El lenguaje ensamblador que se utiliza es :**

 * Sethi const22,rd
 * Sethi %hi(value),rd


* Ejemplo : 



5. Como puedo reescribir la instrucción **(OR y SUBcc)** cuando inicializo y  comparó 2 registros.

R= 

  * La instruccion OR se reescribe con la intruccion MOV
  
  OR %g0, 3 , %l2   ==  MOV 3, %l2
  
  * la instruccion SUBcc se puede reescribe con la función CMP
  
  SUbcc %l0,%l1,g0 ==  CMP %l0,%l1
  
6. ¿Qué instrucciones utilizan el delay slot antes de saltar?

  * BRANCH
  * CALL
  * JUMP AND LINK

7. ¿Qué significa el bit **a**, en el formato 2 de las instrucciones **BRANCH**?
  
  * Si la instruccion branch tiene a=0 es por que ejecuta por debajo y luego salta.
  * Si la instruccion branch tiene a=1 no ejecuta la instruccion que esta por debajo
  solo salta.
  
8. ¿Por que la instrucción **CALL** utilizar el registro %o7 ---> registro 15.?

  * Lo utuliza  para guardar la direccion a donde devera volver el procedimimento llamado 
  al terminar su ejecucion. 
  
  9. convertir el programa en lenguaje de máquina a lenguaje ensamblador y luego a lenguaje de alto nivel el siguiente programa:
```
10100000000100000010000000000101
10100010000100000011111111111010
10010000000001000100000000010000
```
   
*  **|10|10000|000010|00000|1|0000000000101|**

 * MOV 5,%l0
 
 * int x=5;

* **|10|10001|000010|00000|1|1111111111010|**

 * MOV 2,%l1
 
* **10010000000001000100000000010000**
 
  * ADD %l1,%l0,%O0
  
  * int x, y;
   
   * int sum(x,y)
   
   return x+y;
   }
   
   int main(){
   
   Using namespace std ;
   
   cout <<"la suma  de 17 y 16 es;" <<sum(17,16)<<endl;
   
   return 0;
   }
   
   
 











