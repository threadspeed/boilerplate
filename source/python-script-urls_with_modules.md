---
title: python script urls with modules (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'urls with modules'


Modules used in program: 
* `import urlsutils`
* `import json`
* `import random`
* `import os`

## python urls with modules

Python example: urls with modules

```python
import os
import random
import json
import urlsutils

# path for the folder that has all the files
path = "/Users/nicolehe/Desktop/ITP/Spring-2016/rwet/midterm/"


for i in range(5): #this makes it run 5 times

	domains = ['.com/', '.net/', '.org/', '.gov/', '.edu/', '.biz/']
	intros = ["Please visit the ", "Surf on over to the ", "Be sure to check out the ",  "Dont miss the ", "Take a look at the ", "Check out the ", "Hey, you should go to the "]
	
	modBegs = ["lil", "xx", "~", "miss", "TheOriginal", "", "", ""]
	modEnds = ["3000", "99", "Y2K", "420", "69", "baby", "~", "", "", "", "", "4eva", "XOXO"]

	#pick 2 files from the path if they are json files
	pages = random.sample([x for x in os.listdir(path) if os.path.isfile(x) and x.endswith(".json") is True], 2)

	#keeping this one because i can't figure out the scope issues?
	#take the subject and read the json
	def readjson(subject, page_num):
		subject = open(pages[page_num]).read()
		return json.loads(subject)


	data1 = readjson("subject1", 0)
	data2 = readjson("subject2", 1)
	
	#pick a random name section 
	namesList = list()
	for name in open("first-names.txt"):
		name = name.strip()
		namesList.append(name)

	titles = list() #hold the edited titles in a list
	for page in pages:
		page = page.replace("-", " ") #make the dashes into spaces
		page = page[:-5] #get rid of the .json ending
		page = page.title() #capitalize each word
		titles.append(page) #add all these into the titles list

	
	
	#find the values of this key
	allWords1 = data1[urlsutils.findKey(data1)]
	allWords2 = data2[urlsutils.findKey(data2)]


	pickedWordsList1 = urlsutils.pickWordsList('pickedWords1', allWords1)
	pickedWordsList2 = urlsutils.pickWordsList('pickedWords2', allWords2)

	#pick more words for the "topics" section, then add them to lists
	hotTopicsList1 = urlsutils.topics('hotTopics1', allWords1)
	hotTopicsList2 = urlsutils.topics('hotTopics2', allWords2)


	# random picks for different parts
	domainPick = urlsutils.pickRandom(domains)
	introPick = urlsutils.pickRandom(intros)
	namePick = urlsutils.pickRandom(namesList)
	modBegPick = urlsutils.pickRandom(modBegs)
	modEndPick = urlsutils.pickRandom(modEnds)

	
	subjects = " & ".join(titles) 
	subjects = "".join(random.choice([k.upper(), k ]) for k in subjects) #sticky caps

	print("\n ~*~*~*~*~*~ " + introPick + "^_^ " + subjects + " ^_^ forum!!!" + "~*~*~*~*~*~ \n" )
	print("  URL:")
	print("    http://" + pickedWordsList1[0] + "-" + pickedWordsList2[0] + domainPick + pickedWordsList1[1] + "-" + pickedWordsList2[1] + "/" + pickedWordsList2[2] + ".html")
	print("  MODERATOR: " )
	print("    " + modBegPick + pickedWordsList2[3] + pickedWordsList1[3] + modEndPick)
	print("  CONTACT: ")
	print("    " + namePick.lower() + "@" + pickedWordsList1[0] + "-" + pickedWordsList2[0] + domainPick)
	print("  POPULAR TOPICS: " )
	print("    " + hotTopicsList1[0] + ", " + hotTopicsList2[0] + ", " + hotTopicsList1[1] + ", " + hotTopicsList2[1] + "\n")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
