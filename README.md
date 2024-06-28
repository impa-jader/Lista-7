# Lista-7
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
