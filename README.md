# Python
This is the repository showcasing some of my work with python :)

## 'longest_substring' is a function I wrote that takes any length string with special characters and returns the longest substring (word) without repeating letters
```
def longest_substring(string):
	string = string.replace(",", "").replace("'", "").replace("!", "").replace("?", "").replace("#", "").replace("(", "").replace(")", "")
	list_of_substrings = string.split()
	for i in range(len(list_of_substrings)):
		if len(list_of_substrings[i]) > 0:
			for x in range(len(list_of_substrings[i])): # e.g. hello = 5 so x goes up to 4
				try:
					if list_of_substrings[i].count(list_of_substrings[i][x]) > 1 and x < len(list_of_substrings[i]):
						temp_1 = list_of_substrings[i].replace(list_of_substrings[i][x], "")
						temp_2 = list(temp_1)
						temp_2.insert(x, list_of_substrings[i][x])
						list_of_substrings[i] = str(temp_2).replace("['", "").replace("', '", "").replace("']", "")
					else:
						continue
				except IndexError:
					continue
			else:
				continue
		else:
			continue
	largest_sub_string = max(list_of_substrings, key=len)
	position = list_of_substrings.index(largest_sub_string)
	undoctored_list_of_substrings = string.split()
	print(f'the longest substring in "{string}" without repeats is: "{undoctored_list_of_substrings[position]}"')
```
example usage:
```
>>>longest_substring("This is a test string!")
the longest substring in "This is a test string" without repeats is: "string"
```

## reverse_string is a function I used to reverse a string without using the reverse() built in function or slicing
```
def reverse_string(string):
	my_dictionary = {} 
	for x in range(0,len(string)):
		my_dictionary[x] = string[-x]	 # <- this is indexing ! (different to slicing)
	my_dictionary.pop(0)
	my_dictionary[len(string)] = string[0]   
	temp = my_dictionary.values()
	reversed_string = str(temp).replace("dict_values([", "").replace("', '", "").replace("])", "")
	print(reversed_string)
```
example usage:
```
>>> reverse_string("hello world")
'dlrow olleh'
```
## before I learnt there was a sorted() function, I wrote the function anagram to check if two strings are the anagrams of eachother
```
def anagram(input_string_1, input_string_2):
	string_1 = input_string_1.strip().lower().replace(" ","").replace("-","")
	string_2 = input_string_2.strip().lower().replace(" ","").replace("-","")
	temp_string_1 = string_1
	if len(string_1) != len(string_2):
		print(f'{input_string_1} and {input_string_2} are not anagrams of eachother :(')
	else:
		while len(temp_string_1) > 0:
			if string_2.find(temp_string_1[0]) < 0:  # if the first letter of temp_string_1 isnt present in string_2 exit 
				print(f'{input_string_1} and {input_string_2} are not anagrams of eachother :(')
				break
			else:
				temp_string_1 = temp_string_1[1:]
		else: print(f'{input_string_1} is an anagram of {input_string_2}!')
```
example usage:
```
>>> anagram('silent', 'listen')
silent is an anagram of listen!
>>> anagram('hello', 'world')
hello and world are not anagrams of eachother :(
```
## largest element is a function to find the largest number in a list of numbers
```
def largest_element(numbered_list):
	largest_number = 0
	for x in range(0, len(numbered_list)-1):  # range(0,7) <- not incl 7 or 6
		if numbered_list[x] > numbered_list[x+1] and numbered_list[x] > largest_number:
			largest_number = numbered_list[x]
		else:
			continue
	if numbered_list[-1] > largest_number:
		largest_number = numbered_list[-1]
	print(f'the largest number in your list is {largest_number}!')
```
example usage:
```
>>> largest_element([4, 9, 3, 7, 2, 5, 10])
the largest number in your list is 10!
```
## vowel_and_consonants counts the number of vowel and consonants in a word or string
```
def vowel_and_consonants(word):
	word = word.strip()
	word = word.lower()
	vowel_count = 0
	consonant_count = 0
	other_character_count = 0
	vowels = 'a','e','i','o','u'
	for character in word:
		if character.isalpha():
			if character in vowels:
				vowel_count += 1
			else:
				consonant_count += 1
		else:
			other_character_count += 1
			print("your word has", other_character_count, "non alphabetical characters :)")
	print("your word has", vowel_count, "vowels and", consonant_count, "consonants")
```
example usage:
```
code
```
## I am particularly proud of this one, missing number finds the missing number of a sequence with a constant increment (not necessarily of 1)
```
def missing_number(query_list):
	actual_length = len(query_list) + 1
	if query_list[1] - query_list[0] == query_list[2] - query_list[1]:
		increment = query_list[1] - query_list[0]
	elif query_list[2] - query_list[1] == query_list[3] - query_list[2]:
		increment = query_list[2] - query_list[1]
	actual_list = []
	for x in range(1,query_list[-1]+1,increment):
		actual_list.append(x)
	for x in range(1,len(actual_list)):  
		if query_list[x] == actual_list[x]:
			continue
		else:
			print('The missing number is:', actual_list[x])
			break
	else:
		print("There is no missing number!")
```
example usage:
```
>>> missing_number([1, 3, 5, 7, 11, 13, 15, 17, 19, 21, 23])
The missing number is: 9
```
