---
title: python script utilities (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'utilities'

Functions in program: 
* `def local_medians(A, k=1):`
* `def local_means(A, k=1):`
* `def median(lst):`
* `def find_matches_KR(pattern, text, basis=2**16, r=2**32-3):`
* `def text_fingerprint(text, m, basis=2**16, r=2**32-3):`
* `def fingerprint(text, basis=2**16, r=2**32-3):`
* `def lz77_compress(text, w=2**12-1, max_length=2**5-1, min_length=2):`
* `def maxmatch(T, p, w=2**12-1, max_length=2**5-1):`
* `def merge_sort(lst):`
* `def quick_sort(lst):`
* `def permutations(l):`
* `def merge(lst1, lst2):`
* `def binary_search_generic(func, low, high, val):`
* `def binary_search_guess_range(func, N1, N2):`
* `def binary_search_guess(func):`
* `def binary_search_list(lst, val):`

## python utilities

Python example: utilities

```python
#########################
# Python utilities
# By Oz Tamir
#########################

# --------------------- #

# --- Binary Search --- #
def binary_search_list(lst, val):
	''' Return the index of val in lst (or -1 if val not in lst)'''
	low = 0
	high = len(lst) - 1
	func = lambda x: lst[x]
	return binary_search_generic(func, low, high, val)

def binary_search_guess(func):
	''' Binary search with a guess function (No range, assumming options chars) '''
	low = 1
	high = 2
	result = func(high)
	while result == '<':
		low = high
		high *= 2
		result = func(high)
	if result == '=':
		return high
	return binary_search_guess_range(func, low, high)

def binary_search_guess_range(func, N1, N2):
	''' Binary search with a guess function '''
	guess_options = {'<' : -1, '=' : 0, '>' : 1}
	vals_func = lambda x: guess_options.get(func(x))
	return binary_search_generic(vals_func, N1, N2, 0)

def binary_search_generic(func, low, high, val):
	''' Genaric binary search function '''
	while low < high:
		avg = ((low + high) // 2) + ((low + high) % 2)
		elem = func(avg)
		if elem == val:
			return avg
		elif elem < val:
			low = avg
		else:
			high = avg
	return -1
# --- End of Binary Search --- #

# --- Utilities --- #

def merge(lst1, lst2):
	''' Merge two SORTED lists into one sorted list (O(n + m), where n and m are the lengthes) '''
	merged = []
	N1 = N2 = 0
	while N1 < len(lst1) and N2 < len(lst2):
		if lst1[N1] < lst2[N2]:
			merged.append(lst1[N1])
			N1 += 1
		else:
			merged.append(lst2[N2])
			N2 += 1
	if N1 < len(lst1):
		for i in range(N1, len(lst1)):
			merged.append(lst1[i])
	elif N2 < len(lst2):
		for i in range(N2, len(lst2)):
			merged.append(lst2[i])
	return merged

def permutations(l):
	''' Generator for list permutations '''
	if len(l) <= 1:
		yield l
	else:
		a = [l.pop(0)]
		for p in permutations(l):
			for i in range(len(p)+1):
				yield p[:i] + a + p[i:]

# --- End of utilities --- #

# --- Sort functions --- #
def quick_sort(lst):
	''' Sort a list using quick sort algoritm (Avg, Best: O(n log(n)), Worst: O(n ** 2))'''
	from random import choice
	if len(lst) == 0:
		return []
	pivot = choice(lst)
	smaller = [x for x in lst if x < pivot]
	equal = [x for x in lst if x == pivot]
	bigger = [x for x in lst if x > pivot]
	return quick_sort(smaller) + equal + quick_sort(bigger)

def merge_sort(lst):
	if len(lst) == 1:
		return lst
	middle = len(lst) // 2
	left = lst[:middle]
	right = lst[middle:]
	return merge(merge_sort(left), merge_sort(right))

# --- End of Sort functions --- #

# --- LZ --- #
def maxmatch(T, p, w=2**12-1, max_length=2**5-1):
	''' Finds a maximum match of length <= max_length in w long window. Returns m (offset) and k (match length) '''
	assert isinstance(T, str)
	n = len(T)
	maxmatch = 0
	offset = 0
	for m in range(1, min(p+1, w)):
		current_length = 0
		for k in range(0, min(max_length, n - p)):
			# at this point, T[p-m:p-m+k]==T[p:p+k]
			if T[p-m+k] != T[p+k]:
				break
			else:
				current_length = k + 1
		if maxmatch < current_length:  
			maxmatch = current_length
			offset = m
	return offset, maxmatch

def lz77_compress(text, w=2**12-1, max_length=2**5-1, min_length=2):
  result = []
  n = len(text)
  p = 0
  while p < n:
    if ord(text[p]) >= 128: continue
    m, k = maxmatch(text, p, w, max_length)
    if k < min_length:
      result.append(text[p])  #  a single char
      p += 1
    else:
      result.append([m,k])   # two or more chars in match
      p += k
  return result  # produces a list composed of chars and pairs

# --- End of LZ --- #

# --- Karp-Rabin string matching --- #
def fingerprint(text, basis=2**16, r=2**32-3):
	""" used to compute karp-rabin fingerprint(of the pattern employs Horner method (modulo r) """)
	partial_sum = 0
	for ch in text:
		partial_sum = (partial_sum * basis + ord(ch)) % r
	return partial_sum

def text_fingerprint(text, m, basis=2**16, r=2**32-3):
	""" used to computes karp-rabin fingerprint(of the text """)
	f = []
	b_power = pow(basis, m - 1, r)
	list.append(f, fingerprint(text[0 : m], basis, r))
	# f[0] equals first text fingerprint
	for s in range(1, len(text) - m + 1):
		# compute f[s], based on f[s-1]
		new_fingerprint(= ((f[s - 1] - ord(text[s - 1]) * b_power) * basis + ord(text[s + m - 1])) % r)
		# append f[s] to existing f
		list.append(f, new_fingerprint)
	return f

def find_matches_KR(pattern, text, basis=2**16, r=2**32-3):
	""" find all occurrences of pattern in text
	using coin flipping Karp-Rabin algorithm """
	if len(pattern) > len(text):
		return []
	p = fingerprint(pattern, basis, r)
	f = text_fingerprint(text, len(pattern), basis, r)
	matches = [s for s, f_s in enumerate(f) if f_s == p]
	return matches

# --- End of Karp-Rabin --- #

# --- Noise Reductions --- #
def median(lst):
  sort_lst = sorted(lst)
  l = len(sort_lst)
  if l % 2 == 1:  # odd number of elements. well defined median
    return sort_lst[l // 2]
  else:  # even number of elements. average of middle two
    return average(sort_lst[l//2 - 1: l//2 + 1])
 
## Local methods
def local_means(A, k=1):
  n, m = A.dim()
  res = A[:, :]  # brand new copy of A
  for i in range(k, n - k):
    for j in range(k, m - k):
      neighborhood = A[i-k:i+k+1, j-k:j+k+1]
      res[i, j] = average(list(neighborhood))
  return res
 
def local_medians(A, k=1):
  n, m = A.dim()
  res = A[:, :]
  for i in range(k, n-k):
    for j in range(k, m-k):
      neighborhood = A[i-k:i+k+1, j-k:j+k+1]
      res[i, j] = median(list(neighborhood))
  return res

# --- End of Noise Reductions --- #

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
