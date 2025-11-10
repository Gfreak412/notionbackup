# 1. Basics 
### <u>Variables</u>
-  Labels/containers for values (`int`, `bool`, `float`, `string`)
- `int`, `bool`, `float`, `string` has dynamic size allocation in memory and is not a fixed size like in C++
### <u>String Manipulation</u>
- Case change - 
- `.upper()` - all caps
- `.lower()` - all lowercase
- `.title() `- capitalizes 1st letter of each word of a string
- `f”…….”` - f-string, can use variables in `{…}` or direct small operations inline
- `\n` - adds a new line
- `\t` - adds a tab
- `rstrip()` or `lstrip()` or `strip()` - removes white spaces, `rstrip()` from right till end, `lstrip()` from start to left, `strip()` from both sides  
- `.removeprefix('https://')` - removes the specified string from the start of string
<br/>
→ <span style='color:blue_background'><u>NOTE</u></span><u> </u>- `universe_age = 14_000_000_000`, underscores acts as commas in big numbers 
### <u>Lists</u> 
- `bicycles = ['trek', 'cannondale', 'redline', 'specialized']`
- Index Positions Start at 0, Not 1
- Accessing elements - `bicycles[0]`
- `bicycles[0]` = used to access first element
- `bicycles[-1]` = used to access last element
- `bicycles[0] = 'daily'` = Modifying Elements
- `bicycles.append('dirt')` = Adding Elements
- `bicycles.insert(0, 'avon')` = Inserting Elements
- `del bicycles[0]` or `bicycles.remove('avon')`  = Removing Elements 
- `pop()` method removes the last item in a list
- `pop(0)` method removes the 0th index element
- `sort()` = sorts list in alphabetical order and does it irreversibly
- `sorted()` = sorts list in alphabetical order and does it temporarily by creating an instance
- `.reverse()` = reverses the list
- `len()` = prints length of list or no. of elements in a list
### <u>*For Loops *</u>(Used generally in lists)
- To iterate over and print all contents of a list 
```python
for magician in magicians:
print(magician)
--'Any post-op like printing any message or updating any variable'--
```
- Using loops to create a list 
```python
#1
for value in range(1, 5):
print(value)
#2
numbers = list(range(1, 6))
print(numbers)
#3
squares = []
for value in range(1, 11):
square = value ** 2
squares.append(square)
print(squares)
```
- Simple Stats of a list - `min()`, `max()`, `sum()`
- List Comprehension
```python
squares = [value**2 for value in range(1, 11)]
print(squares)
```
- Slicing a list
```python
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print(players[0:3])
```
```python
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print(players[:3])
print(players[2:])
```
- Looping through a sliced list
```python
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print("Here are the first three players on my team:")
for player in players[:3]:
print(player.title())
```
- Making a copy of list 
```python
my_foods = ['pizza', 'falafel', 'carrot cake']
friend_foods = my_foods[:]
```
<br/>
### <u>Tuples</u>
- an immutable list is called a *tuple*.
- Tuple does not support item assignment like list - `bicycles[0] = avon` , doesn’t work in tuples
- We can loop through a tuple
- we can instead of modifying a tuple, redefine a tuple, like completely new
<br/>
### <u>If Statements</u>
- simple syntax 
```python
age = 18
if age < 18:
print("You are not 18 Yet!")
else:
print("You can vote!")
```
- `if status:` or `if not status:` checks if the value is `True` or `False` 
- if checks all the comparison operators like: `==` , `!=` , `<`, `>`, `≤`, `≥` , etc.
- Code after the If statement is executed only when `True` is returned by the condition
- In any other case code after `else` statement  will be executed
- if can check multiple conditions also, which maybe separated by  or, and
- Also if to check if some item is in list, that can be checked also
```python
requested_toppings = ['mushrooms', 'onions', 'pineapple']
if 'mushrooms' in requested_toppings:
print("Yes")
```
- The `if-elif-else` chain is used when we have to check for only one condition to be held true and other statements are skipped
- The `if-if-else` chain is used when all conditions are checked and code is executed before moving on
- Checking if a list is empty or not
```python
requested_toppings = []
if requested_toppings:
print("List is not Empty!")
else:
print("List is Empty!")
```
### <u>Dictionaries</u>
- Each item in a dictionary is a key-value pair
- It does not remember the order of pairs, just the associations
- so we can use OrderedDict
```python
from collections import OrderedDict
fav_languages = {
'jen': 'python',
'sarah': 'c',
'edward': 'ruby',
'phil': 'python',
}
fav_languages = OrderedDict(fav_languages)
for name, language in fav_languages.items():
print(name.title() + ' loves ' + language.title())
```
- Simple dictionary - `alien = {'color': 'green', 'points': 5}`
- More readable syntax / styling
```python
alien = {
'color': 'green',
'points': 5
}
```
- Adding a new key-value pair - `alien['x_position'] = 0`
- getting a value 
```python
alien_0 = {
'color': 'green',
'points': 5
}
alien_color = alien_0.get('color')
```
- Looping through the key-value pairs
```python
fav_numbers = {'eric': 17, 'ever': 4}
for name, number in fav_numbers.items():
print(name + ' loves ' + str(number))
```
- Looping through keys
```python
fav_numbers = {'eric': 17, 'ever': 4}
for name in fav_numbers.keys():
print(name + ' loves a number')
```
- Looping through all the keys in order
```python
# Show each person's favorite language,
# in order by the person's name.
for name in sorted(fav_languages.keys()):
print(name + ": " + language)
```
- Looping through values
```python
fav_numbers = {'eric': 17, 'ever': 4}
for number in fav_numbers.values():
print(str(number) + ' is a favorite')
```
- Modifying values in dictionary
```python
alien_0 = {
'color': 'green',
'points': 5
}
alien_0['color'] = 'yellow'
```
- Length of Dictionaries - `num_responses = len(fav_languages)`
- Nesting of Dictionaries (Not to overdo it, nest once only)
```python
users = {
'aeinstein': {
'first': 'albert',
'last': 'einstein',
'location': 'princeton',
},
'mcurie': {
'first': 'marie',
'last': 'curie',
'location': 'paris',
},
}
```
- Making a million dictionaries 
```python
aliens = []
# Make a million green aliens, worth 5 points
# each. Have them all start in one row.
for alien_num in range(1000000):
new_alien = {}
new_alien['color'] = 'green'
new_alien['points'] = 5
new_alien['x'] = 20 * alien_num
new_alien['y'] = 0
aliens.append(new_alien)
num_aliens = len(aliens)
print("Number of aliens created:")
print(num_aliens)
```
### <u>User Input</u>
- In Python 3, all input is stored as a string.
- `input()`
### <u>While loop</u>
-  A while loop repeats a block of code as long as a condition is `True`.
```python
current_number = 1 # this is called flag
while current_number <= 5:
print(current_number)
current_number += 1
```
- BEWARE of creating a infinite loop! without a end condition, the loop runs infinitely, and memory fills up and system chokes
- Use of `break` in a while loop
```python
prompt = "\nWhat cities have you visited?"
prompt += "\nEnter 'quit' when you're done. "
while True:
city = input(prompt)
if city == 'quit':
break
else:
print("I've been to " + city + "!")
```
- Use of `continue` in a while loop
```python
banned_users = ['eve', 'fred', 'gary', 'helen']
prompt = "\nAdd a player to your team."
prompt += "\nEnter 'quit' when you're done."
players = []
while True:
player = input(prompt)
if player == 'quit':
break
elif player in banned_users:
print(player + " is banned!")
continue
else:
players.append(player)
print("\nYour team:")
for player in players:
print(player)
```
<br/>
### <u>Functions</u>
```python
def greet_user():
print("Hello!")
greet_user()
```
- Positional Arguments or arbitrary arguments(the args which doesn’t accept just one value, it can be any no. of values) 
```python
def make_pizza(size, *toppings):
print("\nMaking a " + size + " pizza.")
print("Toppings:")
for topping in toppings:
print("- " + topping)
make_pizza('small', 'pepperoni')
make_pizza('large', 'bacon bits', 'pineapple')
make_pizza('medium', 'mushrooms', 'peppers',
'onions', 'extra cheese')
```
- Keyword Arguments 
```python
def build_profile(first, last, **user_info):
profile = {'first': first, 'last': last}
for key, value in user_info.items():
profile[key] = value
return profile
user_0 = build_profile('albert', 'einstein', location='princeton')
user_1 = build_profile('marie', 'curie', location='paris', field='chemistry')
print(user_0)
print(user_1)
```
### *Modules*
- Modules (It is a separate file which contains collection of functions)
- Modules can be imported, as well as modules can reference to another module inside it (nested modules)
- you can import an entire module - `import numpy`
- you can import all functions from a module -` from numpy import *`
- you can import a specific function  - `from pathlib import Path`
- you can import by using an alias 
- `import pandas as pd`
- `from pathlib import Path as pt`
### <u>Classes / OOPs concept</u>
- A classes is a collections of functions called methods
- Methods can be used as versatilely as we use functions, but in order to modify the attributes of a class
- The following is basically a template for which an <span style='color:yellow_background'><u>*Object*</u></span>* *can be created
```python
class Car():
def __init__(self, make, model, year):
self.make = make
self.model = model
self.year = year
self.fuel_capacity = 15
self.fuel_level = 0
def fill_tank(self):
self.fuel_level = self.fuel_capacity
print("Fuel tank is full.")
def drive(self):
print("The car is moving.")
```
- the `__init__` method makes and stores all the attributes of a class when made, this function runs when the class is made, this can’t be called (<u>can be called only by a child</u>), others are methods that can be called explicitly
- Making a new class i.e *Instance*
```python
my_car = Car('audi', 'a4', 2016)
my_old_car = Car('subaru', 'outback', 2013)
my_truck = Car('toyota', 'tacoma', 2010)
```
- Accessing the <u>*attributes*</u>
```python
print(my_car.make)
print(my_car.model)
print(my_car.year)
```
- Calling the <u>*methods*</u>
```python
my_car.fill_tank()
my_car.drive()
```
- You can modify an attribute directly or write a method in the class and call it to modify it using the method
```python
# Modify directly
my_new_car = Car('audi', 'a4', 2016)
my_new_car.fuel_level = 5
#using a method
def update_fuel_level(self, new_level):
if new_level <= self.fuel_capacity:
self.fuel_level = new_level
else:
print("The tank can't hold that much!")
my_new_car.update_fuel_level(15)
```
- In Python class names are written in CamelCase and object names are written in lowercase with underscores. Modules that contain classes should still be named in lowercase with underscores.
### <u>***Class Inheritence***</u>
-   To inherit from another class <u>include the name of the parent class</u> in parentheses when defining the new class and make sure to <u>at least include</u> the parameter of `__init__` method of the parent class
```python
Class ElectricCar(Car):
def __init__(self, make, model, year):
super().__init__(make, model, year)
# Attributes specific to electric cars.
self.battery_size = 70
self.charge_level = 0
def charge(self):
self.charge_level = 100
print("The vehicle is fully charged.")
```
- you can define your own attributes and methods, for the child
- The child can access the attributes and methods from the parents, but vice versa is not true
- The methods of a child can be called normally
```python
my_ecar = ElectricCar('tesla', 'model s', 2016)
my_ecar.charge()
my_ecar.drive()
```
- You can <u>override</u> parent’s method, if it is N/A for the child
```python
Class ElectricCar(Car):
def __init__(self, make, model, year):
super().__init__(make, model, year)
self.battery_size = 70
self.charge_level = 0
def charge(self):
self.charge_level = 100
print("The vehicle is fully charged.")
# Overriding the fill_tank method from the parent class,as EVs don't have tanks
def fill_tank(self):
print("This car has no fuel tank!")
```
- We can also use an instance as an attribute inside a class
```python
class Battery():
def __init__(self, size=70):
self.size = size
self.charge_level = 0
def get_range(self):
if self.size == 70:
return 240
elif self.size == 85:
return 270
class ElectricCar(Car):
def __init__(self, make, model, year):
super().__init__(make, model, year)
self.battery = Battery()
def charge(self):
self.charge_level = 100
print("The vehicle is fully charged.")
```
- If we have a method defined inside a instance of a class, and using it in another class, we can access its methods directly too
```python
class Battery():
def __init__(self, size=70):
self.size = size
self.charge_level = 0
def get_range(self):
if self.size == 70:
return 240
elif self.size == 85:
return 270
class ElectricCar(Car):
def __init__(self, make, model, year):
super().__init__(make, model, year)
self.battery = Battery()
def charge(self):
self.charge_level = 100
print("The vehicle is fully charged.")
my_ecar = ElectricCar('tesla', 'model x', 2016)
my_ecar.charge()
print(my_ecar.battery.get_range())
```
- Like Functions, Classes <u>can also be stored in a module</u> and imported similarly
```python
# car.py
class Car():
--snip—
class Battery():
--snip--
class ElectricCar(Car):
--snip--
```
```python
from car import Car, ElectricCar
my_beetle = Car('volkswagen', 'beetle', 2016)
my_beetle.fill_tank()
my_beetle.drive()
my_tesla = ElectricCar('tesla', 'model s', 2016)
my_tesla.charge()
my_tesla.drive()
```
- All the import rules followed by modules are applicable here
- You can make a list of many objects, to store, which is usually what you would be doing in a project
```python
from car import Car, ElectricCar
# Make lists to hold a fleet of cars.
gas_fleet = []
electric_fleet = []
# Make 500 gas cars and 250 electric cars.
for _ in range(500):
car = Car('ford', 'focus', 2016)
gas_fleet.append(car)
for _ in range(250):
ecar = ElectricCar('nissan', 'leaf', 2016)
electric_fleet.append(ecar)
# Fill the gas cars, and charge electric cars.
for car in gas_fleet:
car.fill_tank()
for ecar in electric_fleet:
ecar.charge()
print("Gas cars:", len(gas_fleet))
print("Electric cars:", len(electric_fleet))
```
<br/>
### File Handling
- reading a file - all at once
```python
filename = 'siddhartha.txt' # This should contain the absolute path or 
#	it looks in the same dir
with open(filename) as f_obj:
contents = f_obj.read()
print(contents)
```
- reading a file - line by line
```python
filename = 'siddhartha.txt'
with open(filename) as f_obj:
for line in f_obj:
print(line.rstrip())
```
- These lines can be stored in a list using `.readlines()`, this outputs a list which can be accessed later
- writing to a file - all at once (Multiple lines can be written also)
```python
filename = 'programming.txt'
#Overwrites the file everytime
with open(filename, 'w') as f:
f.write("I love programming!")
f.write("I love creating new games.\n")
```
- Writing to a file - appending
```python
filename = '/home/ehmatthes/books/alice.txt/programming.txt' # Unix
#or
filename = 'C:\Users\ehmatthes\books\alice.txt' #Windows
with open(filename, 'a') as f:
f.write("I also love working with data.\n")
f.write("I love making apps as well.\n")
```
### *Error Handling*
- `try-except` can be used to run a code and expect an error, and then gracefully handle it, with a message or appropriate prompt (`TraceBack` feature of python, shows the correct name of errors)
```python
f_name = 'siddhartha.txt'
try:
with open(f_name) as f_obj:
lines = f_obj.readlines()
except FileNotFoundError:
msg = "Can't find file {0}.".format(f_name)
print(msg)
```
- In the `try` block only the code which can possibly throw an error, should be put
- You can then also add an `else` block, to add the code which only runs when the try block does not produce an error
- You can also fail silently if you just don’t want the program to get interrupted and also the user to not know if an error occurred
```python
f_names = ['alice.txt', 'siddhartha.txt', 'moby_dick.txt', 'little_women.txt']
for f_name in f_names:
try:
with open(f_name) as f_obj:
lines = f_obj.readlines()
except FileNotFoundError:
# Just move on to the next file.
pass
else:
num_lines = len(lines)
msg = "{0} has {1} lines.".format(
f_name, num_lines)
print(msg)
```
- You should avoid using bare `pass` as its not very useful
```python
# Bare except
try:
# Do something
except: 
# this handles no exceptions
pass
```
- Instead of bare excepts we can use `Exception`
```python
try:
# Do something
except Exception as e:
print(e, type(e))
```
- <u>USING JSON</u>
- Store data
```python
import json
numbers = [2, 3, 5, 7, 11, 13]
filename = 'numbers.json'
with open(filename, 'w') as f_obj:
json.dump(numbers, f_obj)
```
- Read data - `json.load()`
```python
import json
filename = 'numbers.json'
with open(filename) as f_obj:
numbers = json.load(f_obj)
print(numbers)
```
- To check if data / json file exists
```python
import json
f_name = 'numbers.json'
try:
with open(f_name) as f_obj:
numbers = json.load(f_obj)
except FileNotFoundError:
msg = "Can’t find {0}.".format(f_name)
print(msg)
else:
print(numbers)
```
<br/>
### Testing the code
- Inbuilt testing features include using `unittest` library
-  To build a test case, make a class that inherits from `unittest.TestCase` and write methods that begin with `test_`.
```python
import unittest
from full_names import get_full_name
class NamesTestCase(unittest.TestCase):
def test_first_last(self):
full_name = get_full_name('janis', 'joplin')
self.assertEqual(full_name, 'Janis Joplin')
unittest.main()
```
- The output of a successful test looks like this, single dot means one unit test has passed
```python
.
---------------------------------------
Ran 1 test in 0.000s
OK
```
- whenever a code fails a test, make sure to fix it accordingly
- never try to mold or change the test to fit your new “wrong*”* code (Until and unless the requirements have changed)
- Testing can be used to make your new code, fix the template of the work, that has to be made
- When testing a class, you usually have to make an instance of the class. The `setUp()`method is run before every test. Any instances you make in `setUp()` are available in every test you write.
```python
import unittest
from accountant import Accountant
class TestAccountant(unittest.TestCase):
def setUp(self):
self.acc = Accountant()
def test_initial_balance(self):
self.assertEqual(self.acc.balance, 0)
acc = Accountant(100)
self.assertEqual(acc.balance, 100)
def test_deposit(self):
self.acc.deposit(100)
self.assertEqual(self.acc.balance, 100)
self.acc.deposit(100)
self.acc.deposit(100)
self.assertEqual(self.acc.balance, 300)
def test_withdrawal(self):
self.acc.deposit(1000)
self.acc.withdraw(100)
self.assertEqual(self.acc.balance, 900)
unittest.main()
```
<br/>
### *PyTest*
- it is a third-party `pip` package for testing code
- we use `assert` keyword to assert an output of the function or code we are testing
```python
# test_name_functions.py
from name_function import get_formatted_name
def test_first_last_name():
formatted_name = get_formatted_name('janis', 'joplin')
assert formatted_name == 'Janis Joplin
```
- The test file should have `test_` at the start of filename
- just running `pytest` in terminal in the code directory, will run <u>**all**</u> tests, and show output
- To make sure only required test file runs, <u>specify</u> the name of the file
| Assertion | Claim | 
| ---- | ---- | 
| `assert a == b` | Assert that two values are equal. | 
| `assert a != b` | Assert that two values are not equal. | 
| `assert a` | Assert that a evaluates to True. | 
| `assert not a` | Assert that a evaluates to False. | 
| `assert element in list` | Assert that an element is in a list. | 
| `assert element not in list` | Assert that an element is not in a list. | 
- <u>**FIXTURES**</u>** **creates for us, the repeated objects, we might be using, repeated function outputs, we require, into a easily reusable option
```python
import pytest
from survey import AnonymousSurvey
@pytest.fixture
def language_survey():
"""Provide a survey instance for all tests."""
question = "What language did you first learn to speak?"
return AnonymousSurvey(question)
```
- Now any test function that takes `**language_survey**` as a parameter will automatically receive the returned survey instance.
```python
def test_store_single_response(language_survey):
language_survey.store_response('English')
assert 'English' in language_survey.responses
def test_store_three_responses(language_survey):
responses = ['English', 'Spanish', 'Mandarin']
for response in responses:
language_survey.store_response(response)
for response in responses:
assert response in language_survey.responses
```
<br/>
# 2. Django
### Setup 
- Make a folder - `mkdir folder_name`
- Make a virtual environment - `python -m venv venv_name`
- activate the venv - `source venv_name/bin/activate`
- update pip - `pip install —upgrade pip`
- install django - `pip install django`
- Create a django project - `django-admin startproject project_name .`
- create a database(uses `*sqlite*`) - `python manage.py migrate`
- making an app and starting it - `python manage.py startapp app_name`
- `models` are functions or functionalities that are useful in any website, it is defined in `app_name/models.py` 
- defined models are then activated by adding it to the `project_name/settings.py` in `INSTALLED_APPS` section of the file.
- After adding new models, YOU MUST run `python manage.py makemigrations app_name` and `python manage.py migrate`
- To create an admin account - `python manage.py createsuperuser` , enter username and set a password (generally - `user - admin | pass - admin`)
- After adding a new model, don’t forget to add it to `admin.py` like this 
```python
from .models import model_name
admin.site.register(model_name)
```
- running the server - `python manage.py runserver` 
### Adding a homepage (`.html`)
- MAKE SURE the app for which you are trying to add a homepage, that app is added in `project_name/settings.py` in `INSTALLED_APPS` section
- homepages are called URLs in django, and URLs are rendered as `views` , views refer to a template to tell django how the URLs should look
- go to `project_name/urls.py` add these 
```python
from django.urls import path, include
path('', include('app_name.urls')),
```
- These makes sure when django sees `http://localhost:8000/` set as `‘’` , it will load the URLs defined
- we will define the template/file to use in `app_name/urls.py` (you will have to create this file), make sure to leave an identifier like a docstring at top, to be able to distinguish two `urls.py` 
- add something like this to `app_name/urls.py`
```python
from django.urls import path
from . import views
app_name = 'app_name'
urlpatterns = [
# Home page
path('', views.index, name='index'),
]
```
- This sets the views to show and load a file named `index.*` 
- To make django render the actual page, add it to `app_name/views.py` 
```python
def index(request):
"""The home page for project_name."""
return render(request, 'app_name/index.html')
```
- As a standard practice make a `templates` folder at `app_name/templates/app_name/` 
- make a `index.html`
```python
<h1>App name title</h1>
<hr>
<p>How can you use my app, here are the instructions.</p>
```
### Adding a new webpage
-  define a new URL pattern
-  write a view
- create a template.
