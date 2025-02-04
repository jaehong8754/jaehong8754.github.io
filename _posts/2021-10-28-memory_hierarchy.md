---
layout: single
title:  "메모리 계층"
---

# 메모리 계층

<img src="/assets/images/2021-10-28-memory_hierarchy/메모리계층.PNG" height="400px" title="메모리계층"/>

</br>

ALC가 레지스터에서 찾는 데이터가 없으면 L1 캐쉬에서 찾는다.

L1 캐쉬에서 찾는 데이터가 없으면 L2 캐쉬에서 찾는다.

L2 캐쉬에서 찾는 데이터가 없으면 메인 메모리에서 찾는다.

메인 메모리에서 찾는 데이터가 없으면 하드디스크에서 찾는다.

하드디스크에서 데이터를 찾았다면 메인메모리에 준다.

메인메모리에서 L2 캐쉬에 데이터를 준다.

L2 캐쉬에서 L1 캐쉬에 데이터를 준다.

L1 캐쉬에서 레지스터에 데이터를 준다.

ALU는 레지스터 데이터를 사용한다.


L1 캐쉬, L2 캐쉬에서 찾아도 연산에 필요한 데이터가 존재할 확률이 90%


</br></br>

# 캐쉬와 캐쉬 알고리즘

</br>

## 컴퓨터 프로그램의 일반적인 특성

Temporal Locality : 프로그램 실행시 한번 접근이 이뤄진 주소의 메모리 영역은 자주 접근한다.

Spatial Locality : 프로그램 실행시 접근하는 메모리 영력은 이미 접근이 이루어진 영역의 근처일 확률이 높다.

</br>

레지스터로 값을 가져오기 위해서 L1 캐쉬를 찾아보는데 만약 데이터가 있다면 캐쉬 힛(Cache Hit) 데이터가 없다면 캐쉬 미스(Cache Miss) 라고 한다.

L1 캐쉬에서 캐쉬 미스가 발생하고 L2 캐쉬에서 찾았다면 L2 캐쉬에 있던 데이터들을 L1 캐쉬로 옮기게 되는데 그 데이터만 옮기는것이 아니라 스페이셜 로컬리티를 고려하여 블록 단위로 L1 캐쉬로 이동하게 된다.

또한 꽉찬 L1 캐쉬에 데이터를 저장하려면 기존에 있던 데이터를 교체 하는데 블록 교체 알고리즘에 따라 블록을 교체하게 된다. 
