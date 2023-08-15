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
  [DFA para linguagem definida pela expressão regular (ab)*(ba)*]()
  [expressão regular {a^m b^n | m+n é par}]()❌
  [expressão regular exceto epsilon, 01 e 001]()❌
  [expressão regular quatro símbolo da direita para esquerda é 1}]()❌
  [conjunto de palavras com no máximo um par de 1's consecutivos]()❌

[Propriedades de fechamento]()
  [Complemento]()
  [União de Linguagens Regulares]()
  
[Lema do Bombeamento:]()
  [L =  wwR]()❌
  [na(w) < nb(w)]()❌
  [na(w) = 2nb(w)]()❌

[Gramática Livre do Contexto:]()
  [Linguagem formada por 0's e 1's, ter 2 zeros consecutivos]()
  [Linguagem formada por {a,b,c} com pelo menos um a e pelo menos um b]()
  [Linguagem formada por 0's e 1's, com no máximo um par de 1's consecutivos]()
  [Linguagem {a^i b^j c^k | i >= 0, j >=0, k = i+j}]()
  [O conjunto de todas as strings formadas por a's e b's com a mesma quantidade de a's e b's]()

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
