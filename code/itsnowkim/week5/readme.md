# 16401 과자 나눠주기
이테코에서의 떡볶이 떡 자르는 문제랑 비슷한 문제였고, 동일하게 접근하여 풀면 된다. 책의 내용을 잘 읽었다면 쉽게 풀 수 있는 매우 정석적인 문제였다.

추가로 이진탐색의 핵심인 빠르게 탐색하는 거를 제대로 적용할 수 있는 문제가 아닌가 싶다. 좋았다.

# 2470 두 용액
이 문제 또한 매우 정석적인 문제였다. while문 내에서 두 포인터의 크기를 비교해서 최적의 값을 찾으면 break, 아니라면 마지막까지 간 이후 최적의 값을 출력하면 된다. 이 또한 매우 정석적인 접근으로 풀 수 있어서 마음에 들었고, 좋은 문제였다.

# 1561 놀이공원
이 문제가 가장 어려웠고, 결국 실패했다. 놀이기구의 개수보다 사람이 적은 경우 단순히 사람의 수를 출력하면 되지만, 아닌 경우 풀이법이 naive한 풀이밖에 떠오르지 않았다. (도저히 이분탐색으로 접근을 못하겠다.)
결국 풀이를 검색해봤는데,
이분탐색을 통해 아이들을 모두 태울 수 있는 시간을 찾고,
구현 시간~탐색한 시간-1분까지 몇 명의 아이를 태울 수 있는지 찾는 것이 핵심이다. 
이렇게 접근하면 구현 시간에 탑승하는 아이들을 계산하면서 제일 마지막에 탑승하는 놀이기구의 번호를 출력하면 된다.

상당히 난이도 있는 문제가 아니었다 싶다.