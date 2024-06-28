# Lista-7

"""3. MISSING INT"""
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
