# TallerprimerParcial

4. Explique cómo inicializar un valor grande, que ocupe más de 13 bits, en la arquitectura **SPARC V8**.

 * El valor grande en la arquitectura sparc v8 que ocupe mas de 13 bits se iniciliza
  con la instruccion **SETHI**, ya que esto nos permite almacenar hasta 22 bits en el formato 2. 
  
  **El lenguaje ensamblador que se utiliza es :**

 * Sethi const22,rd
 * Sethi %hi(value),rd

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
  * Si la instruccion branch tiene a=1 no ejecuta la instruccion que etsa por debajo
  solo salta.
  
  
