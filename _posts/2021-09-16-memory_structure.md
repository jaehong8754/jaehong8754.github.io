---
layout: single
title:  "[python3]병렬처리2"
---

# 파이썬에서 병렬처리2

# 이전 병렬처리 포스트에서 확인된것을 보며 정리를 해보았다.

## 1. GIL이란? 왜 파이썬은 GIL을 사용할까?
파이썬은 메모리 관리를 위해 reference_count와 garbage collect를 사용한다.
reference_count는 생성되는 객체가 참조될 때 증가하고, 참조가 삭제될 때 감소한다.

```python
import sys
class class_reference_count_test():
  def __init__(self):
        pass
a = class_reference_count_test()
print("reference_count_test :", str(sys.getrefcount(a)))
b = a
print("reference_count_test :", str(sys.getrefcount(a)))
c = a
print("reference_count_test :", str(sys.getrefcount(a)))
c = 0
print("reference_count_test :", str(sys.getrefcount(a)))
b = 0
print("reference_count_test :", str(sys.getrefcount(a)))
```
    reference_count_test : 2
    reference_count_test : 3
    reference_count_test : 4
    reference_count_test : 3
    reference_count_test : 2

> 
<br/>
파이썬은 garbage collect에서 사용하지 않거나 reference_count 0인 객체 메모리를 회수한다.
<br/>
즉, c언어에서는 프로그래머가 직접 malloc과 free를 했다면 파이썬은 Python Memory Manager가 관리를 해주기때문에 메모리를 직접 생성하고 해제하는 과정이 필요없다.
<br/>
