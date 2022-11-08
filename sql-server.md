## LATERAL JOIN (CROSS APPLY OR OUTER APPLY)

## SELECT with VALUES clause
```
SELECT
   FirstName,
   LastName
FROM
   (VALUES 
        (1, 'Peter', 'Griffin'),
        (2, 'Homer', 'Simpson'),
        (3, 'Ned', 'Flanders')
   ) AS Idiots(IdiotId, FirstName, LastName)
WHERE IdiotId = 2;
```
### With CTE alternative
```
with parms (tag) as (
  values ('tag1'), ('tag2'), ('tag3')
)
select t.*
from the_table t
  join params p on p.tag = t.tag;
```


VALUES with a MERGE statement
```
DECLARE @Changes TABLE(Change VARCHAR(20));

MERGE INTO Idiots AS Target  
USING ( VALUES 
            (3, 'Ned', 'Okily Dokily!'), 
            (4, 'Lloyd','Christmas'), 
            (5, 'Harry', 'Dunne')
        ) AS Source ( IdiotId, FirstName, LastName )  
ON Target.IdiotId = Source.IdiotId
AND Target.FirstName = Source.FirstName
WHEN MATCHED THEN
    UPDATE SET FirstName = Source.FirstName, LastName = Source.LastName
WHEN NOT MATCHED BY TARGET THEN
    INSERT (FirstName, LastName) VALUES (Source.FirstName, Source.LastName)
OUTPUT $action INTO @Changes;

SELECT Change, COUNT(*) AS Count  
FROM @Changes  
GROUP BY Change;
```