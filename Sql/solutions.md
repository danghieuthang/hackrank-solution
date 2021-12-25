# 1.
## Question: https://www.hackerrank.com/challenges/binary-search-tree-1
## Answer: 

```sql
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
# 2. 
## Question: https://www.hackerrank.com/challenges/occupations
## Answer:
```sql
SELECT Doctor,Professor ,Singer , Actor 
FROM 
	(SELECT Name, Occupation, ROW_NUMBER() OVER (Partition BY Occupation ORDER BY name) as 'No'
	FROM occupations
	)	AS SourceTbl
	PIVOT
	(MAX(NAME) FOR Occupation IN (Doctor, Professor, Singer, Actor)) AS PivotTbl

```