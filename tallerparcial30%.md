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
%g0 = rd1[00000].
imm = 5 =[0000000000 101].

lenguage ensamblador.

 * MOV 5,%l0
 
```
* **|10|10001|000010|00000|1|1111111111010|**
```

formato 3 = Op[10].
%l0 = rd[10000]. 
OR = op3[000010].
%g0 = rd1[00000].
imm = -6 = rd2[1111111111010].

lenguage ensamblador.

 * MOV -6,%l0
 
```
* **|10|01000|000000|10001|0|00000000|10000|**
 
 ```
formato 3 =  Op[10].
%o0 = Rd[01000].
Add = Op3[000000].
%L1 = Rs1[10001].
imm = 0 =i[o].
Rs2(10000)--> %L0 

lenguaje ensamblador
ADD %l1,%l0,%O0
 ```
 
  
  
  *Lenguaje de alto nivel 
  
  int main():
  {
  
    int x=5;
    int y=-6;
    
   return x+y;
   }
   
   
   
   
   
 











