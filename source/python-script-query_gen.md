---
title: python script query gen (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'query gen'

Functions in program: 
* `def create_view_names(view_queries):`
* `def generate_subquery(rteNames):`
* `def generate_view_queries(select_queries, materialized):`
* `def generate_select_join(table_names):`

Modules used in program: 
* `import random`
* `import itertools`

## python query gen

Python mysql example: query gen

```python
import itertools
import random

'''
- cte
- view
- mat view
- fuction remate / vs local / random etc
- isolation reference table_names
- SELECT FOR UPDATE
- 
'''

'''
CREATE TABLE citus_local_table(a int, b int);
SELECT create_citus_local_table('citus_local_table');

CREATE TABLE citus_local_table_2(a int, b int);
SELECT create_citus_local_table('citus_local_table_2');

CREATE TABLE reference_table(a int, b int);
SELECT create_reference_table('reference_table');

CREATE TABLE distributed_table(a int, b int);
SELECT create_distributed_table('distributed_table', 'a');

CREATE TABLE postgres_local_table(a int, b int);


CREATE VIEW citus_local_table_view  AS  SELECT * FROM citus_local_table;
CREATE VIEW reference_table_view  AS  SELECT * FROM reference_table;
CREATE VIEW distributed_table_view  AS  SELECT * FROM distributed_table;
CREATE VIEW citus_local_table_view  AS  SELECT * FROM citus_local_table;


'''

table_names = ['citus_local_table',  'citus_local_table_2', 'reference_table', 'distributed_table', 'postgres_local_table']

def generate_select_join(table_names):
	print(len(table_names))
	allQueries = []
	queryStart = "SELECT count(*) FROM "

	for table_name in range(0, len(table_names)+1):
		for subset in itertools.combinations(table_names, table_name):	
			tableCountInQuery = 0
			subsetList = list(subset)
			queryString = queryStart
			for subElement in subsetList:
				if tableCountInQuery > 0:
						queryString = queryString + " JOIN " + str(subElement) + " USING (a) "
				else:
					queryString = queryString + str(subElement)

				tableCountInQuery = tableCountInQuery + 1
				allQueries.append(queryString + ";")
	return allQueries



def generate_view_queries(select_queries, materialized):
	
	allQueries = []
	viewIndex = 0

	if materialized:
		prefix = "mat_view_"
		queryStart = "CREATE MATERIALIZED VIEW " + prefix
	else:
		prefix = "view_"
		queryStart = "CREATE VIEW " + prefix


	for select in select_queries:
		queryString  = queryStart + str(viewIndex) + " AS " + str(select)

		allQueries.append(queryString)

		allQueries.append("SELECT * FROM " + prefix + str(viewIndex) + ";")
		viewIndex = viewIndex + 1

	return allQueries




def generate_subquery(rteNames):

	queryPrefix = "SELECT count(*) as a, count(*) as b FROM "

	if random.randint(0,10) > 5:
		joinColumn = "b"
	else:
		joinColumn = "a"



	# %20 return a simple query
	# %20 make a join
	if random.randint(0,10) < 1:
		queryPrefix = queryPrefix + random.choice(rteNames) + " as table_" + str(random.randint(0,10000)) 
	elif random.randint(0,10) < 2:
		queryPrefix = queryPrefix + random.choice(rteNames) + " as table_" + str(random.randint(0,10000))  + " JOIN " + random.choice(rteNames) + " as table_" + str(random.randint(0,10000))  + " USING (" + joinColumn + ")"
	else:
		queryPrefix = queryPrefix + random.choice(rteNames) + " JOIN (" + generate_subquery(rteNames)  + ") subquery" + str(random.randint(0,10000)) + " USING (" + joinColumn + ")"

	return queryPrefix


def create_view_names(view_queries):

	view_names = []
	for q in view_queries:
		if q.startswith("CREATE"):
			continue
		name = q.split("FROM")[1].split(';')[0]
		view_names.append(name)
	return view_names


if __name__ == "__main__":
	base_selects = generate_select_join(table_names)
	for select in base_selects:
		print(select)

	view_queries = generate_view_queries(random.sample(base_selects, 5), False)
	for view in view_queries:
		print(view)
	
	mat_view_queries = generate_view_queries(random.sample(base_selects, 5), True)
	for mat_view in mat_view_queries:
		print(mat_view)

	
	view_names = create_view_names(mat_view_queries + view_queries)

	print(view_names)

	selects_with_views = generate_select_join(view_names + table_names)
	for select in selects_with_views:
		print(select)

	for i in range(0,100):
		print(generate_subquery(['citus_local_table', 'citus_local_table_2', 'reference_table', 'distributed_table', 'postgres_local_table']) + ";")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
