#python [[Python]]
## Python
Python has extensive native libraries that can help with automation but also third party libraries which can be useful
It's a good language to write scripts with as it is an **interpreted language**, which means the instructions are executed one line at a time.

Often we will see something called a venv with regards to python which is an isolated system for testing. This is also useful for setting up for a project as it keeps the environment isolated from the larger system.

### Notes/Tasks
[[#Start of Task 1 "Python variable basics"]]
[[#Start of Task 2 "Understand Operators"]]
[[#Start of Task 3 "Create strings and use quotes appropriately"]]
[[#Start of Task 4 "Slice strings"]]
[[#Start of Task 5 "Finish the guessing game with string slicing"]]
[[#Start of Task 6 "Use string methods"]]
[[#Start of Task 7 "Concatenate these variables with different data types"]]
[[#Start of Task 8 "Convert or cast this string to an into and float"]]
[[#Start of Task 9 "Print line as an f-string"]]

#### Start of Task 1 "Python variable basics"

```python
# A variable is a stored item of data assigned to a value  
# A variable is called a variable because it can take many forms and can be changed; it is literally variable  

number_1 = 5  
decimal_1 = 2.2  
string_1 = "This is a string"

# == checks whether two values are equal, rather than assigning a value to that variable  
if number_1 == 5:  
    print("number is 5")  
  
print(number_1)  
print(decimal_1)  
print(string_1)

  
# A strongly typed language is one that is strict on defining data types for variables, a weakly typed language can interpret the data type from the value, it is not specifically defined in the code  
# Python is a weakly typed language, this can be shown here:  
number_2 = 6  
string_2 = "four"  
# print (number2 + string2)  
# The code above will result in a "TypeError" when run  


# A dynamically typed language is one that determines variable types at runtime so there is no need to declare variable types, a statically typed language is one that requires the code to define the variable type before the code compiles. This means that in a dynamically typed language variables can change type mid-code.  
# Python is a dynamically typed language  
variable_1 = 1  
print(variable_1)  
variable_1 = "One"  
print(variable_1)  

print(id(number_1))  
number_1 = 10  
print(id(number_1))  

# The id of the variable changes because the location of the value of the variable changes

x = 10  
y = x  

print(id(x))  
print(id(y))  
# The id of the variables is the same because they are essentially the same value, therefore python uses a reference to the same location to save data  

x = 11  
print(id(y))  
# the id of y has stayed the same  
  
# Asks for name on one line then takes the input on the next line, nice for readability
# print("Please input your name: ")  
# name = input()  
  
# Asks for name on the same line as the input is written
name = input("Please input your name: ")  
age = input("Please input your age(years): ")  
user_DoB = input("Please input your date of birth(dd-mm-yyyy): ")  
  
print("Hi " + name + ",",  
      "You are " + age + " years old and your birthday is",  
      user_DoB)  
  
# --- End of Task 1 "Python variable basics" ---
```
#### Start of Task 2 "Understand Operators" 
```python
x = 5  
y = 1  
  
z = x + y  
a = y * 2  
b = x / a  
c = x % a  
  
print(x, y, z, a, b, c)  
  
if x > y:  
    print("x is bigger than y")  
  
if a < b:  
    print("a is less than b")  
  
if a == 2:  
    print("y is equal to 2")  
  
if c != 2:  
    print("c is not equal to 2")  
  
if b >= 2:  
    print("b is greater than or equal to 2")  
  
if z <= 7:  
    print("z is less than or equal to 7")  
  
# --- End of Task 2 "Understand Operators" ---
```
#### Start of Task 3 "Create strings and use quotes appropriately"
```python

#bad_string = 'I said 'Wow!''  
#print(bad_string)  
  
# This code fails as the compiler cannot tell where the string ends  
  
good_string = 'I said "Wow!"'  
print(good_string)  
  
alt_good_string = "I said \"Wow!\""  
print(alt_good_string)  
  
more_alt_good_string = "I said 'Wow!'"  
print(more_alt_good_string)  
  
# When using quotes around strings in python, it's best to default to using one over another. This is outlined in PEP8.  
  
# --- End of Task 3 "Create strings and use quotes appropriately" ---

```
#### Start of Task 4 "Slice strings" 
```python
  
# Slicing strings is where you split up a string using array concepts, the code will treat the string as an array of  
# characters, and you can refer to each character using an integer  
  
Hw = "Hello world!"  
print(Hw)  
  
print(len(Hw)) # OUTPUT 12  
  
print(Hw[0]) # OUTPUT H  
  
print(Hw[len(Hw) - 1]) # OUTPUT !  
# Using this method ensures that even if the string changes, the code here doesn't need to be altered  
  
print(Hw[len(Hw) - 2]) # OUTPUT d  
  
print(Hw[2:]) # OUTPUT llo world!  
# This code will print the string from the 3rd value (zero indexed array)  
  
print(Hw[-3:]) # OUTPUT ld!  
# This code will print similarly to above except it will "start" at the end of the string and count backwards,  
# -3 refers to the 3rd character from the end  
  
print(Hw[:5]) # OUTPUT Hello (without space at the end)  
# This code will print from the beginning up to the 5th character in the string  
  
print(Hw[1:4]) # OUTPUT ell  
  
# --- End of Task 4 "Slice strings" ---

```
#### Start of Task 5 "Finish the guessing game with string slicing"
```python
# Guess the word with 4 hints to help  
# Rationale: Practice word slicing  
# Type of exercise: Finish the code  
  
original_word = "recommendation"  
scrambled_word = "eoommandretnic"  
  
# Create the hint slices...  
# TO DO: On the next line, replace "?" with a string slice in the format "original_word[x:y]". Use the hints below to know what slice is needed  
hint1_slice = original_word[4:6]  
  
# TO DO: On the next line, replace "?" with a string slice in the format "original_word[x:y]". Use the hints below to know what slice is needed  
hint2_slice = original_word[-3:]  
# alt solution  
# hint2_slice = original_word[7:11]  
  
# TO DO: On the next line, replace "?" with a string slice in the format "original_word[x:y]". Use the hints below to know what slice is needed  
hint3_slice = original_word[7:10]  
  
# TO DO: On the next line, replace "?" with a string slice in the format "original_word[x:y]". Use the hints below to know what slice is needed  
hint4_slice = original_word[:2]  
  
# Game instructions  
  
print("Scrambled word:", scrambled_word)  
print("Guess the original word from the scrambled version.")  
print("Here are some hints:")  
  
# Hints based on list slicing  
  
print("Hint 1: The 5th and 6th letters are '" + hint1_slice + "'.")  
print("Hint 2: The last 3 letters are '" + hint2_slice + "'.")  
print("Hint 3: The 8th to 10th letters are '" + hint3_slice + "'.")  
print("Hint 4: The first two letters are '" + hint4_slice + "'.")  
  
# Game ends here  
  
print("What's your guess?")  
  
# --- End of Task 5 "Finish the guessing game with string slicing" ---
```
#### Start of Task 6 "Use string methods"
```python
str_with_extra_spaces = " extra spaces at the start and end "  
  
# Write comment to explain what this does  
  
print(len(str_with_extra_spaces)) # This will print the length of the string, which is 35  
  
# Write comment to explain what this does  
  
print(len(str_with_extra_spaces.strip())) # the strip method returns a trimmed version of the string, removing any  
# leading or trailing whitespaces  
  
# print(str_with_extra_spaces.strip())  
  
  
example_text = "here's some text with some words of text"  
  
# count how many times the substring 'text' occurs within example_text & print it to the screen  
print(example_text.count("text"))  
  
# convert example_text to lowercase & print it to the screen  
print(example_text.lower())  
  
# convert example_text to uppercase & print it to the screen  
print(example_text.upper())  
  
# capitalise the first letter in example_text & print it to the screen  
print(example_text.capitalize())  
  
# replace the word 'with' in example_text with a comma (,) instead & print it to the screen  
print(example_text.replace(" with", ","))  
  
  
# --- End of Task 6 "Use string methods" ---
```
#### Start of Task 7 "Concatenate these variables with different data types"
```python
x = 2  
y = 5.4  
z = " there's now a number 25.4 unless we put a space in!"  
  
print(f"{x}{y} " + z) # When using multiple types of variables to concatenate strings, the compiler doesn't know how  
# to handle it so we must use formatted strings in order to refer to the variable in the string, then concatenate z  
# onto the end  
print(str(x) + str(y) + z) # Is another method of doing this where we tell the code to treat x and y as strings  
  
# --- End of Task 7 "Concatenate these variables with different data types" ---
```
#### Start of Task 8 "Convert or cast this string to an into and float"
```python
int_string = "6"  
  
# convert int_string to an integer  
int_value = int(int_string)  
  
# after converting, print its data type to the screen  
print(type(int_value))  
  
# convert int_string to float  
float_value = float(int_string)  
  
# after converting, print its data type to the screen  
print(type(float_value))
# --- End of Task 8 "Convert or cast this string to an into and float" ---

```
#### Start of Task 9 "Print line as an f-string"
```python
name = "Lassie"  
  
years = 7  
  
height_cm = 60.2  
  
# print these variables in an f-string so that it outputs this to the screen:  
  
# "Lassie is 7 years old and 60.2 cm tall."  
  
print(f"{name} is {years} years old and {height_cm} cm tall.")
# --- End of Task 9 "Print line as an f-string" ---
# --- Start of Task 10 "Use f-strings to format numbers" ---
pi = 3.14159265359  
  
# Use an f-string to print pi to 3 decimal places e.g. 'Pi to 3 decimal places: <value>'  
print(f"Pi to 3 decimal places: {round(pi, 3)}")  
 # round  
# print(f"Pi to 3 decimal places: {pi:.3f}")  
  
# Use an f-string to print pi to 5 decimal places e.g. 'Pi to 5 decimal places: <value>'  
print(f"Pi to 5 decimal places: {round(pi, 5)}")  
  
score = 16  
max_score = 26  
score_as_decimal = score/max_score  
  
# Use an f-string to print 'score_as_decimal' e.g. 'You scored 0.6153846153846154' (no % sign)  
print(f"You scored {score_as_decimal}")  
  
# Use an f-string to print 'score_as_decimal' formatted as a percentage e.g. 'You scored 61.538462%'  
print(f"You scored {round((score_as_decimal * 100), 6)}%")  
  
# Use an f-string to print 'score_as_decimal' formatted as a percentage to rounded to 2 decimal places e.g. 'You scored 61.54%'  
print(f"You scored {round((score_as_decimal * 100), 2)}%")  
print(f"You scored {score_as_decimal:.2%}")  
  
# Use an f-string to print 'score_as_decimal' formatted as a percentage to rounded to a whole number e.g. 'You scored 62%'  
print(f"You scored {round(score_as_decimal * 100)}%")
# --- End of Task 10 "Use f-strings to format numbers" ---
# --- Start of Task 11 "Improve on previous task to capture user details" ---
  
name = input("What is your name? ")  
age = input("What is your age? ")  
DoB_month = input("What month were you born? ")  
DoB_year = input("What year were you born? ")  
  
print(f"Hi {name}, "  
      + age + "\n"  
      "You were born in "      + DoB_month + " of the year "  
      + DoB_year + ".")
# --- End of Task 11 "Improve on previous task to capture user details" ---
# --- Start of Task 12 "Calculate year of birth" ---
# Write a python script to calculate the user's year of birth  
  
# · define the variables age_int and name_str (set dummy/default/initial values)  
# · make a calculation for the year in which the person was born  
# · print out "OMG , you are years old so you were born in " with the correct values  
# ---  
# · prompt the user for inputs and assign the variable age_int and name_str  
# · remove the initial values set  
# ---  
# · calculate and print out the total number of hours this person has lived  
# ---  
  
import datetime  
from datetime import timedelta, datetime  
  
name_str = input("What is your name? ")  
age_int = int(input("What is your age? "))  
  
year = int(datetime.now().date().strftime("%Y")) - age_int  
yearNow = datetime.now().year  
  
print(f"OMG {name_str}, you are {age_int} years old so you were born in {year}")  
  
hours = timedelta(days = year * 365) // 3600  # TODO finish  
  
  
print(f"You have been alive for {hours} hours")
# --- End of Task 12 "Calculate year of birth" ---
```

## Collections

### Notes/Tasks
[[#Start of Task 1 "Working with lists"]]
[[#Start of Task 2 "Mix all the data about a user into a list"]]
[[#Start of Task 3 "Test you can slice lists"]]
[[#Start of Task 4 "Learn tuples"]]
[[#Start of Task 5 "Working with dictionaries"]]
[[#Start of Task 6 "Practice lists - waiter helper"]]
[[#Start of Task 7 "Improve upon Task 6"]]
[[#Start of Task 8 "Practice dictionaries - hero story"]]
[[#"Start of Task 9 Working with sets"]]
[[#Start of Task 10 "Working with frozen sets"]]

#### Start of Task 1 "Working with lists"
```python
shopping_list = ["eggs",  
                 "bread",  
                 "bananas",  
                 "biscuits",  
                 "milk"]  
  
print(shopping_list)  
print(type(shopping_list))  
  
print(shopping_list[0])  
print(shopping_list[-1])  
  
shopping_list[1] = "rice"  
print(shopping_list[1])  
  
shopping_list.append("carrots")  
print(shopping_list)  
print(len(shopping_list))  
  
shopping_list.extend(["toffee", "coffee"])  
print(shopping_list)  
  
shopping_list.remove("bananas")  
print(shopping_list)  
  
shopping_list.pop()  
print(shopping_list)
# --- End of Task 1 "Working with lists"
```
#### Start of Task 2 "Mix all the data about a user into a list"
```python
  
name = input("Please input your name: ")  
age = input("Please input your age(years): ")  
user_DoB = input("Please input your date of birth(dd-mm-yyyy): ")  
height_cm = input("Please input your height in cm: ")  
  
print("Hi " + name + ",",  
      "You are " + age + " years old and your birthday is",  
      user_DoB)  
  
user_details_list = [  
      name,  
      int(age),  
      user_DoB,  
      float(height_cm)  
]  
  
print(user_details_list)  
  
print(type(user_details_list[1]))  
print(user_details_list[3])
```
#### Start of Task 3 "Test you can slice lists"
```python
mixture = [1, 2, 3,"one", "two", "three"]  
print(mixture)  
  
print(mixture[1:3])  
print(mixture[::2])  
print(mixture[-1:-3:-1])
```

#### Start of Task 4 "Learn tuples"
```python
# How are tuples similar to lists?  
# Tuples are similar to lists in that you can list values and store them in one variable  
  
# Are tuples immutable and what does this mean?  
# Tuples are immutable as they cannot be changed once they have been made
  
# What other data types are immutable?  
# strings, integers, booleans,  
  
# What are good use cases for tuples instead of lists?  
# protected once made  
  
# What does the following piece of code do?  
essentials = ("bread", "eggs", "milk")  
  
print(essentials)  
print(essentials.count("bread"))  
  
# ---  
  
# "Stranded on a Desert Island" game  
# Rationale: Practice tuples  
# Type of exercise: Finish the code  
print("You are stranded on a desert island. You can take only THREE items.")  
essential_item1 = input("What is an essential item you would take? ")  
essential_item2 = input("What is an essential item you would take? ")  
essential_item3 = input("What is an essential item you would take? ")  
# save the items as a tuple  
essentials_tuple = (essential_item1, essential_item2, essential_item3) # YOUR CODE GOES HERE INSTEAD OF 'None'  
# print the tuple  
print("Here are your items as a tuple:", essentials_tuple)  
print("")  
print("I lied. You can take one more item.")  
essential_item4 = input("What is one more essential item you would take? ")  
# try to add the 4th item to the tuple  
# if you can't add the 4th item, work out how to save the 4th item to the tuple  
# YOUR CODE GOES HERE  
essentials_tuple = list(essentials_tuple)  
essentials_tuple.append(essential_item4)  
essentials_tuple = tuple(essentials_tuple)  
print("Here are your items as a tuple (with the 4th item added):",  
essentials_tuple)
```
#### Start of Task 5 "Working with dictionaries"
```python
student_1 = {'name': 'susan',  
             'stream': 'tech',  
             'completed_lessons': int(4),  
             'completed_lesson_names': ["variables", "data_types", "set up"]  
             }  
  
# A set of key:value pairs, the key must always be a string or int or an immutable type (such as a tuple, as long as the tuple doesn't contain a mutable value itself  
# The key becomes a pointer for the value, therefore it cannot be changed after it is set (immutable)  
print(student_1)  
print(type(student_1))  
print(student_1.get("stream"))  
print(student_1.get("completed_lesson_names"))  
  
student_1['completed_lessons'] = int(3)  
print(student_1)  
  
# First pass  
completed_lesson_names_list = student_1['completed_lesson_names']  
# ^ Grabs the list of completed lesson names and puts them in a list  
completed_lesson_names_list.remove("data_types")  
# ^ Removes the "data_types" value from the list  
student_1["completed_lesson_names"] = completed_lesson_names_list  
# ^ Updates the completed lesson names with the list we just made and updated  
  
student_1['completed_lessons'] = int(len(student_1['completed_lesson_names']))  
# ^ Updates the number of completed lessons, for my peace of mind  
print(student_1)  
  
  
# Second pass once removing redundant code (3 lines of code into 1)  
# student_1["completed_lesson_names"] = (student_1['completed_lesson_names']).remove("data_types")  
# ^ Removes the "data_types" value from the list which is in the value for the key "completed_lesson_names"  
  
student_1['completed_lessons'] = int(len(student_1['completed_lesson_names']))  
# ^ Updates the value for the number of lessons completed, otherwise it would just be wrong and I couldn't leave it wrong  
  
print(student_1.keys())
```
#### Start of Task 6 "Practice lists - waiter helper"
```python
# Outcome (By doing this you should): Practice using lists and dictionaries  
# Script should act like a waiter at a restaurant taking orders  
# level 1  
# Greet the user  
user_name = input("What's your name? ")  
print("Good Day " + user_name)  
  
# Print a list of starters  
starters_list = ["Mixed Olives",  
                 "Garlic Bread",  
                 "Garlic Mushrooms"]  
print(f"Your starters choices are: {starters_list}")  
  
# Take an input for the user for their starter  
user_starters_choice = input("What would you like for your starter? ")  
  
# Print a list of mains  
mains_list = ["Pasta with Pizzaiola Sauce",  
              "Pork Chop",  
              "Sirloin Steak"]  
print(f"Your mains choices are: {mains_list}")  
  
# Take an input for the user for their main course  
user_mains_choice = input("What would you like for your mains? ")  
  
# Print a list of desserts  
desserts_list = ["Affogato",  
                 "Eton Mess",  
                 "Chef's Cheesecake of the Day"]  
print(f"Your starters choices are: {desserts_list}")  
  
# Take an input for the user for their dessert  
user_dessert_choice = input("What would you like for your dessert? ")  
  
# Print all of the user's choices  
print(f"So you've gone for the {user_starters_choice} as your starter. \n"  
      f"Then you've decided on the {user_mains_choice} as your mains. \n"  
      f"And finally for your dessert you have chosen {user_dessert_choice}.")  
  
# level 2  
# Use at least one f-string  
# Add each item ordered to a list called 'customer_order_list'  
customer_order_list = [user_starters_choice, user_mains_choice, user_dessert_choice]  
  
# level 3 (may need research if we have not covered dictionaries yet)  
# Use dictionaries and assign prices to the items. Create a bill at the end of the program.  
starters_dic_list = {"Mixed Olives" : "6.99",  
                     "Garlic Bread" : "7.99",  
                     "Garlic Mushrooms" : "8.99"}  
  
mains_dic_list = {"Pasta with Pizzaiola Sauce" : "15.99",  
                  "Pork Chop" : "17.99",  
                  "Sirloin Steak" : "18.99"}  
  
desserts_dic_list = {"Affogato" : "6.99",  
                     "Eton Mess" : "7.99",  
                     "Chef's Cheesecake of the Day" : "8.99"}  
  
starter_price = starters_dic_list[(customer_order_list[0])]  
main_price = mains_dic_list[(customer_order_list[1])]  
dessert_price = desserts_dic_list[(customer_order_list[2])]  
user_bill = float(starter_price) + float(main_price) + float(dessert_price)  
  
print(f"Your bill comes to £{user_bill}")  
  
# level 4  
# Add more to this program. Recommended ways are: Only allow input that is within the list, Add quantities of order etc.
```

#### Start of Task 7 "Improve upon Task 6"
```python
# Outcome (By doing this you should): Practice using lists and dictionaries  
# Script should act like a waiter at a restaurant taking orders  
# level 1  
# Greet the user  
user_name = input("What's your name? ")  
print("Good Day " + user_name)  
  
# Print a list of starters  
starters_list = ["Mixed Olives",  
                 "Garlic Bread",  
                 "Garlic Mushrooms"]  
print(f"Your starters choices are: {starters_list}")  
  
# Take an input for the user for their starter  
user_starters_choice = ""  
  
# A long winded version but gives some user feedback as to why they're being asked again  
#while starters_list.count(user_starters_choice) == 0: # while the starter choice is not listed in the list... ask for the starter  
#    user_starters_choice = input("What would you like for your starter? ")  
#    if user_starters_choice not in starters_list :  
#        print("Please choose a valid option.")  
  
  
while user_starters_choice not in starters_list:  
    user_starters_choice = input("What would you like for your starter? ")  
  
  
# Print a list of mains  
mains_list = ["Pasta with Pizzaiola Sauce",  
              "Pork Chop",  
              "Sirloin Steak"]  
print(f"Your mains choices are: {mains_list}")  
  
# Take an input for the user for their main course  
user_mains_choice = ""  
while user_mains_choice not in mains_list:  
    user_mains_choice = input("What would you like for your main? ")  
  
# Print a list of desserts  
desserts_list = ["Affogato",  
                 "Eton Mess",  
                 "Chef's Cheesecake of the Day"]  
print(f"Your starters choices are: {desserts_list}")  
  
# Take an input for the user for their dessert  
user_desserts_choice = ""  
while user_desserts_choice not in desserts_list:  
    user_desserts_choice = input("What would you like for your dessert? ")  
  
# Print all of the user's choices  
print(f"So you've gone for the {user_starters_choice} as your starter. \n"  
      f"Then you've decided on the {user_mains_choice} as your mains. \n"  
      f"And finally for your dessert you have chosen {user_desserts_choice}.")  
  
# level 2  
# Use at least one f-string  
# Add each item ordered to a list called 'customer_order_list'  
customer_order_list = [user_starters_choice, user_mains_choice, user_desserts_choice]  
  
# level 3 (may need research if we have not covered dictionaries yet)  
# Use dictionaries and assign prices to the items. Create a bill at the end of the program.  
starters_dic_list = {"Mixed Olives" : "6.99",  
                     "Garlic Bread" : "7.99",  
                     "Garlic Mushrooms" : "8.99"}  
  
mains_dic_list = {"Pasta with Pizzaiola Sauce" : "15.99",  
                  "Pork Chop" : "17.99",  
                  "Sirloin Steak" : "18.99"}  
  
desserts_dic_list = {"Affogato" : "6.99",  
                     "Eton Mess" : "7.99",  
                     "Chef's Cheesecake of the Day" : "8.99"}  
  
starter_price = starters_dic_list[(customer_order_list[0])]  
main_price = mains_dic_list[(customer_order_list[1])]  
dessert_price = desserts_dic_list[(customer_order_list[2])]  
user_bill = float(starter_price) + float(main_price) + float(dessert_price)  
  
print(f"Your bill comes to £{user_bill}")  
  
# level 4  
# Add more to this program. Recommended ways are: Only allow input that is within the list, Add quantities of order etc.  
# TODO enclose in loop that allows for asking the user if they'd like to order more? OR ask if they would like to order more than one dish after ordering each course, which is more natural
```

#### Start of Task 8 "Practice dictionaries - hero story"
```python
story_1 = {  
    'start': 'The Beginning',  
    'middle': 'The Main Bit',  
    'end': 'The Happy Ending'  
}  
  
print(story_1)  
print(type(story_1))  
print(story_1.keys())  
print(story_1.values())  
print(story_1.get('start'))  
print(story_1.get('middle'))  
print(story_1.get('end'))  
  
story_1["character"] = "Susan"  
  
print(f"The End. I hope you enjoyed the story about {story_1.get('character')}!" )
```
#### "Start of Task 9 Working with sets"
```python
# Sets are unordered, partially changeable  
# Sets cannot have duplicate values  
fruits = {  
    "apple",  
    "banana",  
    "cherry"}  
  
print(fruits)  
  
fruits.add("orange")  
print(fruits)  
  
fruits.remove("banana")  
print(fruits)  
  
fruits.add("apple")  
print(fruits)  
  
# print(fruits[1])
```
#### Start of Task 10 "Working with frozen sets"
```python
frozen_set = frozenset([  
    "hello",  
    "world"  
])  
frozenset(frozen_set)  
#frozen_set.add("!")  
  
normal_set = {  
    "let's",  
    "learn"  
}  
print(normal_set)  
  
normal_set.update(frozen_set)  
print(normal_set)
```
## Control flow

[[#Start of Task 1 "Learn if statement - print movie ratings meanings"]]
[[#Start of Task 2 "Working with for loops"]]
[[#Start of Task 3 "while loops"]]
[[#Start of Task 4 "prompt user for age loop"]]
[[#Start of Task 5 "Magic number guessing game"]]
[[#Start of Task 6 "fizzbuzz"]]
[[#Start of Task 7 "improve movie ratings"]]


### Notes/Tasks

#### Start of Task 1 "Learn if statement - print movie ratings meanings"

```python
# possible film ratings are "universal", "pg", "12", "12a", "15", "18"  
film_rating = "12a"  
  
# use an if statement to check for "universal" rating  
if film_rating == "universal":  
    print("all age groups can watch this film")  
# check if film rating is "pg"  
elif film_rating == "pg":  
    print("General viewing, but some scenes may be unsuitable for young children.")  
# check if film rating is "12" or "12a"  
elif film_rating == "12" or "12a":  
    print("Films classified 12A and video works classified 12 contain material that is not generally suitable for children aged under 12. No one younger than 12 may see a 12A film in a cinema unless accompanied by an adult.")  
# check if film rating is "15"  
elif film_rating == "15":  
    print("No one younger than 15 may see a 15 film in a cinema.")  
# check if film rating is "18"  
elif film_rating == "18":  
    print("No one younger than 18 may see an 18 film in a cinema.")  
else:  
    print("This is not a correct rating, please use universal, pg, 12, 12a, 15, 18")
# --- End of Task 1 "Learn if statement - print movie ratings meanings" ---
```
#### Start of Task 2 "Working with for loops"

```python
list_data = [1, 2, 3, 4, 5]  
embedded_lists = [  
    [1,2,3],  
    [4,5,6]  
]  
dict_data = {  
    1: {  
        "name": "Bronson",  
        "money": "$0.05"},  
    2: {  
        "name": "Masha",  
        "money": "$3.66"},  
    3: {  
        "name": "Roscoe",  
        "money": "$1.14"}  
}  
  
for num in list_data:  
    print(num * 2)  
  
print("\n")  
  
for item in embedded_lists:  
    print(item)  
  
print("\n")  
  
for item in embedded_lists:  
    print(item)  
    for subitem in item:  
        print(subitem)  
  
print("\n")  
  
for key in dict_data:  
    print(key)  
  
print("\n")  
  
for value in dict_data.values():  
        print(value)  
  
print("\n")  
  
for value in dict_data.values():  
    for sub_value in value.values():  
        print(sub_value)  
  
print("\n")  
  
for value in dict_data.values():  
    print(value.get("money"))  
  
print("\n")  
  
for num in list_data:  
    if num < 3:  
        print("less than 3")  
    elif num == 3:  
        print("I found three")  
    elif num > 3:  
        print("greater than 3")
# --- End of Task 2 "Working with for loops" ---

```
#### Start of Task 3 "while loops"
```python
x = 0  
  
# while x < 10:  
#    print(f"x is: {x}")  
#    x += 1 # if x wasn't incremented, the code would never hit the while loop's end condition so the code would continue to loop  
  
while x < 5:  
    print(f"x is: {x}")  
    x += 1 # if x wasn't incremented, the code would never hit the while loop's end condition so the code would continue to loop

# --- End of Task 3 "while loops" ---
```
#### Start of Task 4 "prompt user for age loop"
```python
age = 0  
# SET VARIABLE user_prompt TO TRUE  
user_prompt = True  
# PUT BEGINNING OF WHILE LOOP HERE - SHOULD LOOP WHILE user_prompt IS TRUE  
while user_prompt:  
    age = input("What is your age? ")  
    if age.isdigit() and (0 < int(age) <= 117):  
        user_prompt = False  
    else:  
        print("Your input is not valid. Please try again.")  
print(f"Your age is {age}")
# --- End of Task 4 "prompt user for age loop" ---
```
#### Start of Task 5 "Magic number guessing game"

```python
# =====================================================================
# LEVEL 1
# =====================================================================
# User story 1  
# As a user, I want to be able to guess a number and know if i got it correct or not, so that I can know if I won or not.  
# Define/assign number to a variable called magic_number  
magic_number = 42  
  
# Ask user for input  
# Allow the user 5 guesses  
num_guesses = 5  
user_guess = 0  
first_guess = True  
  
while num_guesses >= 1:  
    # Check if this input matches magic_number  
    if int(user_guess) == magic_number:  
        print("Well done! You guessed the right number.")  
        break  
    else: # Let the user know if the response was correct or not  
        if not first_guess:  
            print("That was not the correct number.")  
        else:  
            first_guess = False  
        num_guesses -= 1  
        user_guess = input(f"Please choose a number from 1 to 100 inclusive: ")  
  
print("Thank you for playing")


# =====================================================================
# LEVEL 2
# =====================================================================
import random  
from random import randint  
random.seed()  
  
# Define/assign number to a variable called magic_number  
magic_number = 42  
num_guesses = 5  
user_guess = 0  
first_guess = True  
success = False  
print(magic_number)  
  
while num_guesses >= 1:  
    user_guess = input(f"Please choose a number from 1 to 100 inclusive (You have {num_guesses} guesses left): ")  
    if str(user_guess).isdigit() and 100 >= int(user_guess) > 0: # Check if the user has inputted a number  
        if int(user_guess) == magic_number: # Check if the number is correct  
            print("Well done! You guessed the correct number. Thank you for playing!")  
            break  
        elif int(user_guess) > magic_number:  
            print("That was not the correct number, the magic number is lower than your guess.")  
        else:  
            print("That was not the correct number, the magic number is higher than your guess.")  
        num_guesses -= 1  
    else: # Catch that the user has not put in a number  
        print("Your guess was not a valid number and will not be counted as a guess.")

# =====================================================================
# LEVEL 3
# =====================================================================
import random  
from random import randint  
random.seed()  
  
# Define/assign number to a variable called magic_number  
magic_number = randint(1, 100)  
  
num_guesses = 5  
user_guess = 0  
first_guess = True  
success = False  
print(magic_number)  
  
while num_guesses >= 1:  
    user_guess = input(f"Please choose a number from 1 to 100 inclusive (You have {num_guesses} guesses left): ")  
    if str(user_guess).isdigit() and 100 >= int(user_guess) > 0: # Check if the user has inputted a number  
        if int(user_guess) == magic_number: # Check if the number is correct  
            success = True  
            break        elif int(user_guess) > magic_number:  
            print("That was not the correct number, the magic number is lower than your guess.")  
        else:  
            print("That was not the correct number, the magic number is higher than your guess.")  
        num_guesses -= 1  
    else: # Catch that the user has not put in a number  
        print("Your guess was not a valid number and will not be counted as a guess.")  
  
if success:  
    print("Well done! You guessed the correct number. Thank you for playing!")  
else:  
    print(f"You did not guess the number... \n"  
          f"The magic number was {magic_number}. Thank you for playing!")
# --- End of Task 5 "level 1 magic number guessing game" ---
```
#### Start of Task 6 "fizzbuzz"
```python
i = 1  
fizz_number = 3  
buzz_number = 5  
  
def check_multiple(check_number_1, check_number_2):  
    return check_number_1 % check_number_2 == 0  
  
while i < 101:  
    if check_multiple(i, fizz_number) and check_multiple(i, buzz_number):  
        print("FizzBuzz")  
    elif check_multiple(i, fizz_number):  
        print("Fizz")  
    elif check_multiple(i, buzz_number):  
        print("Buzz")  
    else:  
        print(i)  
    i += 1
# --- End of Task 6 "fizzbuzz" ---
```
#### Start of Task 7 "improve movie ratings"
```python
# possible film ratings are "universal", "pg", "12", "12a", "15", "18"  
film_rating = "12a"  
  
# use an if statement to check for "universal" rating  
if film_rating == "universal":  
    print("all age groups can watch this film")  
# check if film rating is "pg"  
elif film_rating == "pg":  
    print("General viewing, but some scenes may be unsuitable for young children.")  
# check if film rating is "12" or "12a"  
elif film_rating == "12" or "12a":  
    print("Films classified 12A and video works classified 12 contain material that is not generally suitable for children aged under 12. No one younger than 12 may see a 12A film in a cinema unless accompanied by an adult.")  
# check if film rating is "15"  
elif film_rating == "15":  
    print("No one younger than 15 may see a 15 film in a cinema.")  
# check if film rating is "18"  
elif film_rating == "18":  
    print("No one younger than 18 may see an 18 film in a cinema.")  
else:  
    print("This is not a correct rating, please use universal, pg, 12, 12a, 15, 18")
# --- End of Task 7 "improve movie ratings" ---
```
## Functions

DRY - Don't Repeat Yourself 

### Notes/Tasks
[[#Start of Task 1 "Practice functions - Mini Calculator"]]
[[#Start of Task 2 "Group task - Make functions"]]

#### Start of Task 1 "Practice functions - Mini Calculator"
```python
# --- MVP ---  
def addition(a:int, b:int) -> int:  
    return a + b  
  
def subtraction(a:int, b:int) -> float:  
    return a - b  
  
def multiplication(a:int, b:int) -> int:  
    return a * b  
  
def division(a:int, b:int) -> float:  
    return a / b  
  
  
first_digit = int(input("Please input your first number: "))  
second_digit = int(input("Please input your second number: "))  
operator = input("Please input your operator ( +, -, *, /): ")  
  
if operator == "+":  
    print(addition(first_digit, second_digit))  
elif operator == "-":  
    print(subtraction(first_digit, second_digit))  
elif operator == "*":  
    print(multiplication(first_digit, second_digit))  
elif operator == "/":  
    print(division(first_digit, second_digit))  
else:  
    print("You have not entered a valid option")

# --- End of Task 1 "Practice functions - Mini Calculator" ---

```
#### Start of Task 2 "Group task - Make functions"
```python

input_string = "Hello again!"  
  
def print_something(input_string_argument):  
    print(input_string_argument)  
  
print_something(input_string)  
  
# ---  
  
def greet(name):  
    print("Hello, my name is " + name + ".")  
  
greet("Susan")  
  
# ---  
  
def addition(int1, int2):  
    return int1 + int2 # must include return  
  
value = addition(2, 2)  
# print(addition(2, 2))  
  
# --- Task 6  
  
def addition(int1 = 2, int2 = 2):  
    return int1 + int2 # must include return  
  
print(addition())  
print(addition(4, 4)) # the function has added 4 and 4 which makes 8, the default values have been overwritten  
  
  
def print_every_number(numbers_tuple): # When using the *, the question is not answered  
    print(type(numbers_tuple))  
    for i in numbers_tuple:  
        print(i)  
  
print_every_number((1, 2, 2, 3, 3, 4, 5, 5))  
  
# --- Task 7  
  
# greet(24601) # The code does not like being given an int when the function is treating the argument as a string  
  
def print_something(input_string_new: str):  
    print(input_string_new)  
  
def division(x:int = 2, y:int = 5) -> float:  
    return x / y  
  
a:int = 4  
b:int = 6  
print(division(a, b))  
print(division())
# --- End of Task 2 "Group task - Make functions" ---

```
