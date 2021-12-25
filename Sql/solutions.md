
## Question: https://www.hackerrank.com/challenges/binary-search-tree-1
## Answer: 

```
SELECT N, 
	CASE
		WHEN P IS NULL THEN 'Root'
		ELSE 
			CASE (SELECT COUNT(b.N) FROM BST AS b WHERE b.P=BS.N)
				WHEN 0 THEN 'Leaf'
				ELSE 'Inner'
			END
	END AS 'Node type'
FROM BST AS BS
ORDER BY N
```