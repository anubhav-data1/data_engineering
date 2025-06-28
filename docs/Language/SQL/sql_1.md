#

|MYSQL|POSTGRESSQL|
|-----|----|
|GROUP_CONCAT|STRING_AGG|
||string_agg(expression, delimiter)|
||string_agg(employee_name, ', ' ORDER BY employee_name)|



substring()
upper()
lower()
INITCAP() - to capitalise all first letters in a string
Like in where ‘%%’
row_number() over(partition by cmn1 order by clmn2) as 

Dense rank will not miss the number while ranking even if duplicate. Rank would do that.

For date - to_char(column, ‘date format’)
Extract date from a date column -
EXTRACT(MONTH FROM o.order_date) = 2
TO_CHAR(o.order_date, 'MM') = '02'


In group by if merging all the values of column - string_agg(distinct product,',' order by product) as products


Regex
mail ~* '^[a-zA-Z][a-zA-Z0-9._-]+@leetcode\.com$’.     ~* to match 