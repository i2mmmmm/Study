https://school.programmers.co.kr/learn/courses/30/lessons/273712

더 이상 업그레이드할 수 없는 아이템의  
아이템 **ID**(ITEM_ID), **아이템 명**(ITEM_NAME), **아이템의 희귀도**(RARITY)를 출력하는 SQL 문을 작성해 주세요.  
이때 결과는 아이템 **ID를 기준으로 내림차순** 정렬해 주세요.


```
SELECT I.ITEM_ID, I.ITEM_NAME, I.RARITY
FROM ITEM_INFO I LEFT JOIN ITEM_TREE T
ON I.ITEM_ID = T.PARENT_ITEM_ID
WHERE T.ITEM_ID IS NULL
ORDER BY I.ITEM_ID DESC
```
