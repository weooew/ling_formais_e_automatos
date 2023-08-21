# ling_formais_e_automatos
[Conceitos Básicos:]()
  [Prefixo]()
  Sua tarefa é implementar uma função recursiva em python que decide se uma palavra x é prefixo de uma palavra y.

Complete o seguinte código:
```
def prefixo(x, y):
    ## Coloque seu código aqui

def main():
    x = input()
    y = input()
    print( prefixo(x,y) )


if __name__ == "__main__":
    main()
    ```

  ```
  def prefixo(x, y):
    if x == "": 
        return True
    if x != "" and y == "":
        return False
  
    if x[0]== y[0]:
        return prefixo(x[1:], y[1:])
    else:
        return False
    ## Coloque seu código aqui

def main():
    x = input()
    y = input()
    print( prefixo(x,y) )


if __name__ == "__main__":
    main()
  ```
  [Sufixo]()
  Sua tarefa é implementar uma função recursiva em python que devolve uma lista com todos os sufixos de uma palavra x.

Complete o seguinte código:
```
def sufixos(x):
    ## Cole seu código aqui
        
        
def main():
    x = input()
    
    print( sufixos(x) )


if __name__ == "__main__":
    main()
    ```
  ```
  def sufixo(x):
    if x == "": return "'']"
    if x != "": return "'"+ x + "', " + sufixo(x[1:])
        
def main():
    x = input()
    print ("[", end = '')
    print( sufixo(x) )


if __name__ == "__main__":
    main()
  ```
  [Sequência de Golumb]()
  Vamos utilizar uma função geradora para construir a sequência de Golumb.

Complete o seguinte código:

```
def golumb():

    yield 1
    yield 2
    yield 2
    
    #use o gerador para descobrir quantas vezes o número n deve ser repetido
    gerador = golumb()
        
     
            
        
def main():
    
    n = int(input())
    gerador = golumb()
    l = [ next(gerador) for i in range(n)]
    print(l)


if __name__ == "__main__":
    main()
```
    
  ```
  def golumb():

    yield 1
    yield 2
    yield 2
     #use o gerador para descobrir quantas vezes o número n deve ser repetido
    gerador = golumb()
    next(gerador)
    next(gerador)

    n = 3
    for a in gerador:
      for i in range(a):
        yield n
      n += 1    
            
        
def main():
    
    n = int(input())
    gerador = golumb()
    l = [ next(gerador) for i in range(n)]
    print(l)


if __name__ == "__main__":
    main()
  ```
  [Sequência de kolakoski]() ❌
  Note que o tamanho de cada bloco da sequência de Kolakoski forma a própria sequência de kolakoski.

Complete o seguinte código:

```
def kolakoski():

    yield 1
    yield 2
    yield 2

    # utilize a sequência para descobrir o tamanho dos blocos seguintes
    gerador = kolakoski()
            
        
def main():
    
    n = int(input())
    gerador = kolakoski()
    l = [ next(gerador) for i in range(n)]
    print(l)


if __name__ == "__main__":
    main()
  
  ```
  
[Autômato Finito Determinístico:]()
  [Strings terminadas em 011]()
  ```
  #Código Python 
# Automato que aceita string binarias com a substring 01
# 
#   
edges = { # função de transição
(1, '0') : 2,
(1, '1') : 1,
(2, '0') : 2,
(2, '1') : 3,
(3, '0') : 2,
(3, '1') : 4,
(4, '0') : 2,
(4, '1') : 1,
}

current = 1 # estado inicial
accepting = [4] # estados finais

# Função que roda o autômato
def dfa(string, current, edges, accepting):
    if string == "":
        return current in accepting
    else:
        letter = string[0]
        remainder = string[1:]
        if (current, letter) in edges:
            newstate = edges[(current, letter)]
            return dfa(remainder, newstate, edges, accepting)
        return False


string = input()
print (dfa(string, current, edges, accepting))
  ```
  [String com 011 como substring]()
  ```
  #Código Python 
# Automato que aceita string binarias com a substring 01
# 
#   
edges = { # função de transição
(1, '1') : 1,
(1, '0') : 2,
(2, '0') : 2,
(2, '1') : 3,
(3, '0') : 3,
(3, '1') : 3       
}

current = 1 # estado inicial
accepting = [3] # estados finais

# Função que roda o autômato
def dfa(string, current, edges, accepting):
    if string == "":
        return current in accepting
    else:
        letter = string[0]
        remainder = string[1:]
        if (current, letter) in edges:
            newstate = edges[(current, letter)]
            return dfa(remainder, newstate, edges, accepting)
        return False


string = input()
print (dfa(string, current, edges, accepting))
  ```
  
  [String que quando interpretadas são múltiplos de 5]()
  ```
  #Código Python 
# Automato que aceita string binarias com a substring 01
# 
#   
edges = { # função de transição
(1, '0') : 1,
(1, '1') : 2,
(2, '0') : 3,
(2, '1') : 4,
(3, '0') : 5,
(3, '1') : 1,
(4, '0') : 2,
(4, '1') : 3,
(5, '0') : 4,
(5, '1') : 5,
(6, '0') : 7,
(6, '1') : 2,
(7, '0') : 7,
(7, '1') : 7,
}

current = 6 # estado inicial
accepting = [1] # estados finais

# Função que roda o autômato
def dfa(string, current, edges, accepting):
    if string == "":
        return current in accepting
    else:
        letter = string[0]
        remainder = string[1:]
        if (current, letter) in edges:
            newstate = edges[(current, letter)]
            return dfa(remainder, newstate, edges, accepting)
        return False


string = input()
print (dfa(string, current, edges, accepting))
  
  ```
  
[Autômato Finito não-Determinístico:]()
  [Contêm a substring 00]()
  ```
# Exemplo de NFA que aceita as strings binárias com o penúltimo dígito igual a 1
edges = {  (0,'0') : [0,1],
           (0,'1') : [0],
           (1,'0') : [2],
           (1,'1') : [0],
           (2,'0') : [2],
           (2,'1') : [2],
}
initial   =  0 # estado inicial
accepting = [2] # conjunto de estado final

def nfa(string, current, edges, accepting): 
    if string == "":
        return  current in accepting        
    else:
        c = string[0]
        if (current,c) in edges:
            for next in edges[(current,c)]:
                if nfa(string[1:], next, edges, accepting):
                    return True
        return False
        

string = input()
print ( nfa(string, initial, edges, accepting) )
  
  ```
  [Terminam em 00 ou 11]()
  ```
# Exemplo de NFA que aceita as strings binárias com o penúltimo dígito igual a 1
edges = {  (0,'0') : [0,1],
           (0,'1') : [0,3],
           (1,'0') : [2],
           (3,'1') : [4],
}
initial   =  0 # estado inicial
accepting = [2,4] # conjunto de estado final

def nfa(string, current, edges, accepting): 
    if string == "":
        return  current in accepting        
    else:
        c = string[0]
        if (current,c) in edges:
            for next in edges[(current,c)]:
                if nfa(string[1:], next, edges, accepting):
                    return True
        return False
        

string = input()
print ( nfa(string, initial, edges, accepting) )

  ```
  [Strings que começam ou terminam em 01]()
```
# Exemplo de NFA que aceita as strings binárias com o penúltimo dígito igual a 1
edges = {  (0,'0') : [0,3],
           (0,'1') : [3],
           (1,'1') : [2],
           (2,'0') : [2],
           (2,'1') : [2],
           (3,'0') : [3,4],
           (3,'1') : [3],
           (4,'1') : [5],
           
}
initial   =  0 # estado inicial
accepting = [2,5] # conjunto de estado final

def nfa(string, current, edges, accepting): 
    if string == "":
        return  current in accepting        
    else:
        c = string[0]
        if (current,c) in edges:
            for next in edges[(current,c)]:
                if nfa(string[1:], next, edges, accepting):
                    return True
        return False
        

string = input()
print ( nfa(string, initial, edges, accepting) )
```

[Autômato Finito não-Determinístico com transição epsilon:]()
  [Contêm pelo menos dois 0's ou exatamente dois 1's]()
  ```
  # Strings binárias que começam ou terminam com 01
edges = { (0, '') :  [4,1],
          (1, '0') : [1,2], 
          (1, '1') : [1],
          (2, '0') : [3],
          (3, '0') : [3],
          (3, '1') : [3],
          (4, '0') : [4],       
          (4, '1') : [5],
          (5, '0') : [5],       
          (5, '1') : [6],
          (6, '0') : [6],       
          (6, '1') : [7],
          (7, '0') : [7],       
          (7, '1') : [7],
          
}
initial   = 0
accepting = [3, 6] 

def epsilon_nfa(string, current, edges, accepting): 
    #print ("current: " + str(current) + "string: " + string )    
    if string == "":
        return  current in accepting       
    else:
        if (current, '') in edges:
          for next in edges[(current,'')]:
            if epsilon_nfa(string, next, edges, accepting):
                    return True
        c = string[0]
        if (current,c) in edges:
            for next in edges[(current,c)]:
                if epsilon_nfa(string[1:], next, edges, accepting):
                    return True
        
        return False
        

string = input()
print (epsilon_nfa( string , initial, edges, accepting) )    
  ```
  [Tenha 1 nos últimas quatro posições]()
  ```
  # Strings binárias que começam ou terminam com 01
edges = { (0,'0') : [0],
   (0,'1') : [0,1],
   (1,'') : [2],
   (1,'0') : [2],
   (1,'1') : [2],
   (2,'') : [3],
   (2,'0') : [3],
   (2,'1') : [3],
   (3,'') : [4],
   (3,'0') : [4],
   (3,'1') : [4],
}
initial   = 0
accepting = [1,2,3,4] 

def epsilon_nfa(string, current, edges, accepting): 
    #print ("current: " + str(current) + "string: " + string )    
    if string == "":
        return  current in accepting       
    else:
        if (current, '') in edges:
          for next in edges[(current,'')]:
            if epsilon_nfa(string, next, edges, accepting):
                    return True
        c = string[0]
        if (current,c) in edges:
            for next in edges[(current,c)]:
                if epsilon_nfa(string[1:], next, edges, accepting):
                    return True
        
        return False
        

string = input()
print (epsilon_nfa( string , initial, edges, accepting) )  

  ```
  [Todos exceto 01, 101, 0100]()
  ```
# Strings binárias que começam ou terminam com 01
edges = { (0, '0') :  [1],
          (0, '1') : [2],
          (1, '0') : [3],
          (1, '1') : [4],
          (2, '0') : [9],
          (2, '1') : [3],
          (3, '0') : [3],
          (3, '1') : [3],
          (4, '0') : [5],
          (4, '1') : [3],       
          (5, '0') : [6],
          (5, '1') : [8],       
          (6, '0') : [7],
          (6, '1') : [7],       
          (7, '0') : [7],
          (7, '1') : [7],       
          (8, '0') : [8],
          (8, '1') : [8],
          (9, '0') : [11],
          (9, '1') : [10],       
          (10, '0') : [12],
          (10, '1') : [12],
          (11, '0') : [11],
          (11, '1') : [11],
          (12, '0') : [12],
          (12, '1') : [12],       
          
 }
initial   = 0
accepting = [1,2,3,5,7,8,9,11,12] 

def epsilon_nfa(string, current, edges, accepting): 
    #print ("current: " + str(current) + "string: " + string )    
    if string == "":
        return  current in accepting       
    else:
        if (current, '') in edges:
          for next in edges[(current,'')]:
            if epsilon_nfa(string, next, edges, accepting):
                    return True
        c = string[0]
        if (current,c) in edges:
            for next in edges[(current,c)]:
                if epsilon_nfa(string[1:], next, edges, accepting):
                    return True
        
        return False
        

string = input()
print (epsilon_nfa( string , initial, edges, accepting) ) 
  ```

[Expressão Regular:]()
  [Linguagem definida pela expressão regular ab*ba(ab)*]()
  ```
edges = {
   (0,'a') : [1],
   (1,'b') : [2],
   (2,'b') : [2],
   (2,'a') : [3],
   (3,'a') : [4],
   (4,'b') : [3],
   (4,'a') : [5], 
}

accepting = [3]
initial = 0

def dfa(string, current, edges, accepting):
    if string == "":
        return current in accepting
    else:
        letter = string[0]
        remainder = string[1:]
        newstate = edges.get((current, letter), [])  # Use get() with a default value of an empty list
        if newstate:
            return dfa(remainder, newstate[0], edges, accepting)  # Access the first state in the list
        return False

string = input()
print(dfa(string, initial, edges, accepting))


  ```
  [DFA para linguagem definida pela expressão regular (ab)*(ba)*]()
```
edges = {
   (0,'a') : [1],
   (1,'b') : [2],
   (2,'b') : [2],
   (2,'a') : [3],
   (3,'a') : [4],
   (4,'b') : [3],
   (4,'a') : [5], 
}

accepting = [3]
initial = 0

def dfa(string, current, edges, accepting):
    if string == "":
        return current in accepting
    else:
        letter = string[0]
        remainder = string[1:]
        newstate = edges.get((current, letter), [])  # Use get() with a default value of an empty list
        if newstate:
            return dfa(remainder, newstate[0], edges, accepting)  # Access the first state in the list
        return False

string = input()
print(dfa(string, initial, edges, accepting))
```

  
  [expressão regular {a^m b^n | m+n é par}]()❌
solver.py
  ```
from regexp import *

def main():
    str = input()
    E = Empty()
    print( E.matches(str) )


if __name__ == "__main__":
    main()
 ```

regexp.py
  ```
class Reg: 
  def matches(w) -> bool:
    pass  
  
class Epsilon(Reg):
  def __init__(self):
    self.re1 = ""
  def __str__(self) -> str:
    return "e"
  def matches(self, w) -> bool:
    return w == ""
  

class Empty(Reg):
  def __init__(self):
    self.re1 = []
  def __str__(self) -> str:
    return "{}"
  def matches(self, w) -> bool:
    return w == []
  
  
class Literal(Reg):
  def __init__(self, a):
    self.re1 = a
  def __str__(self) -> str:
    return str(self.re1)    
  def matches(self, w) -> bool:
    return w == self.re1    
  def language(self):
    yield self.re1
class Or(Reg):
  def __init__(self, re1, re2):
    self.re1 = re1
    self.re2 = re2          
  def __str__(self):
     return "(" + str(self.re1) + "+" + str(self.re2) + ")"
  def matches(self, w):
    return self.re1.matches(w) or self.re2.matches(w)
 
    
    
        

class Concat(Reg):
  def __init__(self, re1, re2):
    self.re1 = re1
    self.re2 = re2    
  def __str__(self):
    return str(self.re1) + str(self.re2)
  def matches(self, w):
    for pos in range( len(w) +1):
      #print(w[0:pos] + "," + w[pos:])
      if self.re1.matches( w[0:pos] ) and self.re2.matches(w[pos:] ):
        return True
    return False
  

  

class Star(Reg):
  def __init__(self, re1):
    self.re1 = re1
  def __str__(self):
    return "(" + str(self.re1) + ")*"
  def matches(self, w):
    if w == "" :
      return True
    if len(w) == 1:
      return self.re1.matches(w)    
    else:
      for pos in range( len(w) + 1):
        if self.re1.matches( w[0:pos] ) and self.matches(w[pos:] ):
          return True
      return False
  ```
  [expressão regular exceto epsilon, 01 e 001]()❌
  [expressão regular quatro símbolo da direita para esquerda é 1}]()❌
  [conjunto de palavras com no máximo um par de 1's consecutivos]()❌

[Propriedades de fechamento]()
  [Complemento]()
As propriedades de fechamento são ferramentas utéis para mostrar que uma linguagem L é regular.

As propriedades de fechamento são vários teoremas da seguinte forma “se certas linguagens são regulares e uma linguagem L é formada a partir delas por certas operações (por exemplo, L é a união de duas linguagens regulares ou L é complemento de uma linguagem regular), então L é regular.”.

Por exemplo, a operação de complemento preserva a regularidade. Se uma linguagem L é regular então L¯ também será regular.

Prova: Se L é regular então existe um autômato finito determinístico A=(Q,Σ,δ,q0,F) tal que L(A)=L. A partir desse autômato, podemos construir um autômato A=(Q,Σ,δ,q0,Q−F). Observe que toda palavra aceita por A não será aceita por B e toda palavra aceita por B não será aceita por A.

Faça um programa que recebe um autômato para uma linguagem L e construa um autômato para L¯.

Entrada

A primeira linha é formada por uma tupla (Q1,δ1,q1,F1) com as informações do autômato, conjunto de estados, função de transição, estado inicial e estado final, respectivamente.

Entrada

([1, 2, 3], {(1, '1'): 1, (1, '0'): 2, (2, '0'): 2, (2, '1'): 3, (3, '0'): 3, (3, '1'): 3}, 1, [3])
  ```
  def main():
    
    (states, edges, initial, final) = eval(input())
    
    states2 = [1,2,3]
    edges2 = {
        (1, '1'): 1, 
        (1, '0'): 2, 
        (2, '0'): 2,
        (2, '1'): 3,
        (3, '1'): 3,
        (3, '0'): 3
    }
    initial2 = 1
    final2 = [1,2]
    
    teste(states2, edges2, initial2, final2) 
  ```
  [União de Linguagens Regulares]()
As propriedades de fechamento são ferramentas utéis para mostrar que uma linguagem L é regular.

As propriedades de fechamento são vários teoremas da seguinte forma “se certas linguagens são regulares e uma linguagem L é formada a partir delas por certas operações (por exemplo, L é a união de duas linguagens regulares ou L é complemento de uma linguagem regular), então L é regular.”.

Por exemplo, a operação de união preserva a regularidade. Se uma linguagem L1 e L2 são regulares então L=L1∪L2 também será regular.

Faça um programa que recebe dois autômatos para uma linguagem L1 e L2 utilizando um alfabeto Σ e construa um autômato para L1∪L2.

Consulte o seguinte o material sobre as propriedade de fechamento

Entrada

A primeira linha possui uma lista com o alfabeto Σ dois autômatos

A primeira linha é formada por uma tupla (Q1,δ1,q1,F1) com as informações do autômato do primeiro autômato: conjunto de estados, função de transição, estado inicial e estado final, respectivamente.

A segunda linha é formada por uma tupla (Q1,δ1,q1,F1) com as informações do autômato do primeiro autômato: conjunto de estados, função de transição, estado inicial e estado final, respectivamente.

Considere que os dois autômatos estão definidos no mesmo alfabeto Σ.

Entrada

['0','1']
([1, 2, 3], {(1, '1'): 1, (1, '0'): 2, (2, '0'): 2, (2, '1'): 3, (3, '0'): 3, (3, '1'): 3}, 1, [3])
([1, 2], {(1, '1'): 1, (1, '0'): 2, (2, '0'): 1, (2, '1'): 2}, 1, [1])

```
def main():
    
    sigma = eval(input())
    (states1, edges1, initial1, final1) = eval(input())
    (states2, edges2, initial2, final2) = eval(input())
    
    #adicionando um par ordenado relacionando
    #os dois autômatos 
    states3 = [(1,1), (1,2), (2,1), (2,2), (3,1), (3,2)]
    for x in states1:
        for y in states2:
            states3.append( (x,y) )
    
    
    edges3 = {}
    edges3[ ((1,1), '0')] = (2,2)
    edges3[ ((1,1), '1')] = (1,1)
    edges3[ ((1,2), '0')] = (2,1)
    edges3[ ((1,2), '1')] = (1,2)
    edges3[ ((2,1), '0')] = (2,2)
    edges3[ ((2,1), '1')] = (3,1)
    edges3[ ((2,2), '0')] = (2,1)
    edges3[ ((2,2), '1')] = (3,2)
    edges3[ ((3,1), '0')] = (3,1)
    edges3[ ((3,1), '1')] = (3,1)
    edges3[ ((3,2), '0')] = (3,1)
    edges3[ ((3,2), '1')] = (3,2)
    
    
    final3 = [(1,1), (2,1), (3,1), (3,2)]
    for x in final1:
        for y in final2:
            final3.append( (x,y) )
    
    initial3 = (initial1, initial2)
    
    teste(states3, edges3, initial3, final3)
```

  
[Lema do Bombeamento:]()
  [L =  wwR]()❌
  O Lema do Bombeamento é uma ferramenta útil para mostrar que uma linguagem L não é regular. Ele foi primeiramente provado por Rabin e Scott in 1959 e redescoberto por Bar-Hillel, Perles e Shamir em 1961.

A contrapositiva do Lema do Bombeamento pode ser apresentado da seguinte forma:

Para todo n≥1 temos que

Existe w∈L com |w|≥n tal que

Para todo x,y,z∈Σ* com w=xyz, |y|≥0 e |xy|≤n temos que

Existe i≥0 tal que xyiz∉L

então

L não é regular.

O Lema do Bombeamento pode ser apresentado como um jogo. Dado uma linguagem L.

    O primeiro jogador escolhe um n≥1 qualquer

    O segundo jogador escolher uma palavra w tal que |w|≥n

    O primeiro jogador particiona w em x,y,z tal que |xy|≤n e |y|>0

    O segundo jogador ganha se para cada particionamento de w ele encontra um i tal que xyiz∉L.

Considere a seguinte linguagem:

L={arbscr+s|r≥0,s≥0}

No nosso exemplo, o jogador 1 será o computador. Digamos que o computador escolher 3. Você deve definir uma palavra w∈L tal que |w|≥n. Por exemplo,

w=aaabccc.

O computador vai particionar w de todas as maneiras possíveis:

    x=ε,y=a,z=aabccc
    x=ε,y=aa,z=abccc
    x=ε,y=aaa,z=bccc
    x=a,y=a,z=abccc
    x=a,y=aa,z=bccc
    x=aa,y=a,z=bccc

Para esta linguagem, em todas as partições, o segundo jogador pode escolher i=0:

    x=ε,y=a,z=aabccc,xy0z=aabccc∉L
    x=ε,y=aa,z=abccc,xy0z=abccc∉L
    x=ε,y=aaa,z=bccc,xy0z=bccc∉L
    x=a,y=a,z=abccc,xy0z=aabccc∉L
    x=a,y=aa,z=bccc,xy0z=accc∉L
    x=aa,y=a,z=bccc,xy0z=aabccc∉L

jogador2.py

def chooseString(m):
  # vamos escolher a palavra $w = a^mb^m$
  w = "a"*m + "b"*m
  print(w)
  partition(m,w)

def main():
  # o jogador 2 le o valor de m 
  m = int( input() )
  # o jogador 2 escolhe uma palavra usando o valor de m
  chooseString(m)

if __name__ == '__main__':
  main()  

utils.py

from language import L

def pumpingOut(x,y,z):
    # O jogador 2 recebe uma particao
    # deve escolher uma maneira de bombear a string para fora da linguagem
    i = 0
    p = x + y*i + z
    return not L(p)

As ações do jogador 1 estão implementadas no Moodle.

Considere esta outra linguagem:

L={wwR|w∈{a,b}*}

ou seja, uma palavra w qualquer seguida pelo seu reverso.

Digamos que m=3.

Você pode escolher a seguinte palavra w∈L tal que |w|≥n:

w=aaabbaaa

Todas as partições possíveis de w:

    x=ε,y=a,z=aabbaaa
    x=ε,y=aa,z=abbaaa
    x=ε,y=aaa,z=bbaaa
    x=a,y=a,z=abbaaa
    x=a,y=aa,z=bbaaa
    x=aa,y=a,z=bbaaa

Em todas as partições, o segundo jogador pode escolher i=0

Implemente a função que escolhe a palavra e estratégia de escolha do i tal que para toda partição x,y,z, xyiz∉L para a linguagem

L={wwR|w∈{a,b}*}
Arquivos requeridos
utils.py
```
from language import L

def pumpingOut(x,y,z):
    # O jogador 2 recebe uma particao
    # deve escolher uma maneira de bombear a string para fora da linguagem
    i = 0
    p = x + y*i + z
    return not L(p)
```
jogador2.py
```
from jogador1 import partition
from language import L

def chooseString(m):
  # vamos escolher a palavra $w = a^mb^m$
  w = "a"*m + "b"*m
  partition(m,w)


def main():
  # o jogador 2 le o valor de m 
  m = int( input() )
  # o jogador 2 escolhe uma palavra usando o valor de m
  chooseString(m)

if __name__ == '__main__':
  main()     
```
  [na(w) < nb(w)]()❌
O Lema do Bombeamento é uma ferramenta útil para mostrar que uma linguagem L não é regular. Ele foi primeiramente provado por Rabin e Scott in 1959 e redescoberto por Bar-Hillel, Perles e Shamir em 1961.

A contrapositiva do Lema do Bombeamento pode ser apresentado da seguinte forma:

Para todo n≥1 temos que

Existe w∈L com |w|≥n tal que

Para todo x,y,z∈Σ* com w=xyz, |y|≥0 e |xy|≤n temos que

Existe i≥0 tal que xyiz∉L

então

L não é regular.

O Lema do Bombeamento pode ser apresentado como um jogo. Dado uma linguagem L.

    O primeiro jogador escolhe um n≥1 qualquer

    O segundo jogador escolher uma palavra w tal que |w|≥n

    O primeiro jogador particiona w em x,y,z tal que |xy|≤n e |y|>0

    O segundo jogador ganha se para cada particionamento de w ele encontra um i tal que xyiz∉L.

Implemente a função que escolhe a palavra e estratégia de escolha do i tal que para toda partição x,y,z, xyiz∉L para a linguagem

L={w|na(w)<nb(w)}

onde nc(w) representa a quantidade de ocorrência do caractere c na palavra w.

  
  [na(w) = 2nb(w)]()❌
O Lema do Bombeamento é uma ferramenta útil para mostrar que uma linguagem L não é regular. Ele foi primeiramente provado por Rabin e Scott in 1959 e redescoberto por Bar-Hillel, Perles e Shamir em 1961.

A contrapositiva do Lema do Bombeamento pode ser apresentado da seguinte forma:

Para todo n≥1 temos que

Existe w∈L com |w|≥n tal que

Para todo x,y,z∈Σ* com w=xyz, |y|≥0 e |xy|≤n temos que

Existe i≥0 tal que xyiz∉L

então

L não é regular.

O Lema do Bombeamento pode ser apresentado como um jogo. Dado uma linguagem L.

    O primeiro jogador escolhe um n≥1 qualquer

    O segundo jogador escolher uma palavra w tal que |w|≥n

    O primeiro jogador particiona w em x,y,z tal que |xy|≤n e |y|>0

    O segundo jogador ganha se para cada particionamento de w ele encontra um i tal que xyiz∉L.

Implemente a função que escolhe a palavra e estratégia de escolha do i tal que para toda partição x,y,z, xyiz∉L para a linguagem

L={b5w|na(w)=2nb(w)}

onde nc(w) representa a quantidade de ocorrência do caractere c na palavra w.



  
[Gramática Livre do Contexto:]()
  [Linguagem formada por 0's e 1's, ter 2 zeros consecutivos]()


    Definição: Uma gramática livre-do-contexto é uma tupla (V,Σ,R,S), onde: 1. V é um conjunto finito de símbolos variáveis, 1. Σ é um conjunto finito de símbolos terminais, 1. R⊆V×(V∪Σ)* é um conjunto finito de regras, 1. S∈V é a variável inicial.

Observe que formalmente um regra A→w é um par (A,w)∈R, que indica a possibilidade de substituição da variável A∈V por uma cadeia w∈(V∪Σ)*.

Considere a seguinte linguagem:

L={anbn|n≥0}

A seguinte gramática livre-do-contexto G pode ser projetada para a linguagem L:

S→aSb|ε

A gramática G pode ser implementada da seguinte maneira usando a classe GLC:

from glc import GLC

def main():
    V = {'S'}
    Sigma = {'a','b'}
    R = {('S','aSb'),
     ('S',''),
    }
    S = 'S'
    G = GLC(V,Sigma,R,S)
    teste(G)

Projete uma gramática livre-do-contexto para a seguinte linguagem regular:

L = O conjunto de todas as palavras em {0,1}* com dois zeros consecutivos.

Por exemplo, 00,100,1001,1010011∈L

Complete o seguinte código:

from glc import GLC

def main():
    V = {}
    Sigma = {}
    R = {
    }
    S = 
    G = GLC(V,Sigma,R,S)
    teste(G)
```
from glc import GLC

def main():
    V = {'A', 'B'}
    Sigma = {'0', '1'}
    R = {('A', '0A'),
        ('A', '1A'),
        ('A', '00B'),
        ('B', '0B'),
        ('B', '1B'),
        ('B', '0'),
        ('B', '1'),
        ('B', '')}
    start = 'A'
    G = GLC(V,Sigma,R,start)
    G.check()
    teste(G) 
```

  
  [Linguagem formada por {a,b,c} com pelo menos um a e pelo menos um b]()
```
from glc import GLC

def main():
    V = {'A', 'Z'}
    Sigma = {'a', 'b', 'c'}
    R = {('A', 'ZaZbZ'),
        ('A', 'ZbZaZ'),
        ('Z', 'ZaZ'),
        ('Z', 'ZbZ'),
        ('Z', 'ZcZ'),
        ('Z', '')}
    start = 'A'
    G = GLC(V,Sigma,R,start)
    G.check()
    teste(G)

```
  
  [Linguagem formada por 0's e 1's, com no máximo um par de 1's consecutivos]()
```
from glc import GLC

def main():
    V = {'A', 'B', 'C'}
    Sigma = {'0', '1'}
    R = {
        ('A', '0A'),
        ('A', '1'),
        ('A', '10A'),
        ('A', ''),
        ('A', '11B'),
        ('B', '11C'),
        ('B', '01B'),
        ('B', '0B'),
        ('B', '')
    }
    start = 'A'
    G = GLC(V, Sigma, R, start)
    G.check()
    teste(G) 
```
  
  [Linguagem {a^i b^j c^k | i >= 0, j >=0, k = i+j}]()
  ```
from glc import GLC

def main():
    V = {'A'}
    Sigma = {'a', 'b', 'c'}
    R = {('A', 'aAc'),
        ('A', 'bAc'),
        ('A', ''),}
    start = 'A'
    G = GLC(V,Sigma,R,start)
    G.check()
    teste(G)
  ```
  [O conjunto de todas as strings formadas por a's e b's com a mesma quantidade de a's e b's]()
  ```
from glc import GLC

def main():
    V = {'S'}
    Sigma = {'a','b'}
    R = {('S','bSa'),
        ('S','aSb'),
        ('S','baS'),
        ('S','abS'),
        ('S','')}
    start = 'S'
    G = GLC(V,Sigma,R,start)
    teste(G)
  ```

[Autômato de Pilha:]()
  [Nenhum prefixo tem mais 1's do que 0's]()❌
  [L = {a^i b^j c^k | i=j, i=k}]()❌
  [Linguagem formada por 0's e 1's que possui o dobro de 0's do que 1's]()❌
  [Converta uma GLC para PDA]()❌

Avaliação Final:
  [Autômato Deterministico para palavras que começam ou terminam com 0]()❌
  [Autômato não-determinístico em que o digito final não apareceu antes]()❌
  [Expressão regular para strings binárias que tenha 1 nas últimas quatro posições]()❌
  [Lema do Bombeamento nenhum prefixo tem mais 1's do que 0's]()❌
  [Gramática livre de contexto L = {a^i b^j | i < j < 2i}]()❌
