# Lista-7
"""1"""
import matplotlib.pyplot as plt
import pandas as pd

x= [(3/1000)*i-3/2 for i in range(1001)]
y= [k**8 -3*k**4  +2*k**3  -2*k**2 -k +2 for k in x]
#Falta usar o pandas
plt.plot(x,y)
plt.title("""Lista 7
Questão 1""")
plt.show()

"""2"""
def entre(l: list, n: float):
    if n>=l[0] and n<=l[1]:
        return True
    else:
        return False

def merge_intervals(l: list):
    ja_foi=[]
    r=[]
    for i in l:
        if i not in ja_foi:
            r_=[k for k in i]
            ja_foi.append(i)
            for q in l:
                if entre(r_,q[1]) or entre(r_,q[0]):
                    ja_foi.append(q)
                    if q[1]>=r_[1]:
                        r_[1]=q[1]
                    if q[1]<=r_[1]:
                        r_[0]=q[0]
            r.append(r_)
    return r

algo=[ [ 2 , 6 ] , [ 1 , 3 ] , [ 8 , 10 ] , [ 15 , 18 ] ]
print(merge_intervals(algo))
algo_2=[ [ 1 , 4 ] , [ 4 , 5 ] ]
print(merge_intervals(algo_2))
"""3."""
def missing_int(l: list):
  ordem=[ l[0] + i for i in range(len(l))]
  for k in range(len(l)):
    if l[k]!=ordem[k]:
      return ordem[k]
  return l[len(l)-1]+1
  
print(missing_int([5,6,7,9]))# 8
print(missing_int([5]))# 6
print(missing_int([5,6,7,8,9]))# 10
print(missing_int([-3,-2,0]))# -1


"""4"""
"""4. Escreva uma fun ̧c ̃ao is palindrome que dado o n ́o inicial de uma lista
encadeada simples (e.g. exerc ́ıcio 3 da lista 6), retorne verdadeiro se ela
for um pal ́ındromo e falso caso contr ́ario."""
# Eu usei ocodigo da lista 5 para fazer uma gambiarra e fazer o exercicio

class node:
    def __init__(self, algo):
        self.aqui= algo
        self.ali= None

class Linked_list:
    def __init__(self):
        self.head = None
        
    def ad(self, novo):
        n=node(novo)
        if self.head==None:
            self.head= n
        else:
            pointer= self.head
            while pointer.ali!= None:
                pointer = pointer.ali
            pointer.ali= n
            """ Adiciona elementos no final da lista"""
    
    def __str__(self):
        if self.head is None:
            return "HeadNone" 
        r= str(self.head.aqui)
        point= self.head
        while point.ali!=None:
            r+= " -> " + str(point.ali.aqui)
            point= point.ali
        return r

    def inverter(self):
        Inv=Linked_list()
        lista_normal=[self.head.aqui]
        pontinho = self.head
        while pontinho.ali is not None:# complexidade n
            lista_normal.append(pontinho.ali.aqui)
            pontinho = pontinho.ali
        for i in range(len(lista_normal)):# complexidade n
            Inv.ad(lista_normal[len(lista_normal)-1-i])# ad tem complexidade n
        return Inv
        # complexidade O(n^2), pois utiliza-se o metodo ad, de complexidade n, dentro de for, também de complexidade n.
        
        
lista= Linked_list()
lista.ad(15)
lista.ad(10)
lista.ad(1)
lista.ad(2)
lista.ad(3)
lista.ad(4)
lista.ad(5)
lista.ad(6)
print(lista)  
print(lista.inverter())

listo= Linked_list()
listo.ad(15)
listo.ad(10)
listo.ad(1)
listo.ad(2)
listo.ad(2)
listo.ad(1)
listo.ad(10)
listo.ad(15)
print(listo)  
print(listo.inverter())

def is_palindrome(l):
    l_list=str(l).split(" -> ")
    inv_list=str(l.inverter()).split(" -> ")
    print(l_list)#teste
    print(inv_list)#teste
    for i in range(len(l_list)):
        if l_list[i]!=inv_list[i]:
            print(inv_list[i])
            print(l_list[i])
            return "Is not palindrome"
    return "Is palindrome"

print(is_palindrome(lista))# is not palindrome
print(is_palindrome(listo))# is palindrome
