---
title       : SCT quiz
description : Quiz time y'all
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf


--- type:NormalExercise lang:python xp:100 skills:1 key:03eebf7448
## Simple tests (1)

#### pass 1

```python
import numpy

x = numpy.array([1,2,3])

print(x)
```

#### pass 2

```python
import numpy as npp

x = y = npp.array([1,2,3])

print(y)
```

#### fail 1 - "Did you import numpy?"

```python
import pandas as pd

x = pd.np.array([1,2,3])

print(x)
```

#### fail 2 - "x is not an ndarray"

```python
import numpy as np

x = [1,2,3]

print(x)
```

#### fail 3 - "x is undefined"

```python
import numpy as np
```

#### fail 4 - "Expected [1,2,3] in your output"

```python
import numpy

x = numpy.array([1,2,3])
```

*** =sample_code
```{python}
import numpy as np

x = np.array([1,2,3])

print(x)
```

*** =solution
```{python}
import numpy as np

x = np.array([1,2,3])

print(x)
```

*** =sct
```{python}
Ex().test_import("numpy", same_as = False)
Ex().test_object("x",eq_condition="equal", undefined_msg="x is undefined",
            do_eval=True, incorrect_msg="Expected [1,2,3] in your output")
#I spent 20min trying to get the above to work for Fail 2 and it didn't (the SCT likes the list as well as the array :-/)
            
Ex().test_object_after_expression("type(x)", incorrect_msg="x is not an ndarray")
#Ex().test_output_contains("[1 2 3]", pattern = False)
Ex().has_equal_output("Expected [1,2,3] in your output")

```

--- type:NormalExercise lang:python xp:100 skills:2 key:d71dfcb25c
## Simple tests (2)

#### pass 1

```
f("blue")
```

#### pass 2

```
f( "b" )
```

#### pass 3

```
f('b')
```

#### pass 4
```
(f("b"))
```

#### fail 1 -

```
f("blueberry")
```

#### fail 2 -

```
pf("blue")
```

*** =pre_exercise_code
```{python}
def f(a): return a*2

def pf(a): return a*2

```

*** =sample_code
```{python}
f("b")
```

*** =solution
```{python}
f("b")
```

*** =sct
```{python}
# NOTE: use a single test_student_typed statement
#       see https://docs.python.org/3.5/library/re.html

#HBA note: I tried to search docs for test_student_typed and couldn't find anything (search box + quick look)
Ex().test_student_typed("^\({0,1}f\([\'\"]b.{0,3}[\'\"]\)\){0,1}", pattern=True)

#This took me ~25 min

```

--- type:NormalExercise lang:python xp:100 skills:2 key:746620aaa8
## Part Checks (1)

#### fail 1 - "No inline if expression"

```
if True: ["yes" for ii in range(3) if ii > 2]
elif False: pass
else: pass
```

#### fail 2 - "No if filter in list comp"

```
if True: ["yes" if True else False for ii in range(3)]
elif False: pass
else: pass
```


*** =sample_code
```{python}
if True: ["yes" if True else False for ii in range(3) if ii > 2]
elif False: pass
else: pass

```

*** =solution
```{python}
if True: ["yes" if True else False for ii in range(3) if ii > 2]
elif False: pass
else: pass
```

*** =sct
```{python}


lc = Ex().check_if_else(0).check_body().check_list_comp(0)

lc.check_ifs(0, missing_msg= "No if filter in list comp")

lc.check_body().test_student_typed("if True else False", not_typed_msg="No inline if expression")


# I think testing list comps is great but  i don't see the value in having the if elif else: 
# it was both confusing and irrelevant to the general SCT writing process.

#FIND MY FIRST PASS BELOW

# I couldn't find much on testing the 1st `if True:` in the docs.
# I spent ~20min looking at this page:http://pythonwhat.readthedocs.io/en/latest/part_checks.html
# For testing parts, it may help to 1st test a simple list comp: why is the if elif else used?
# I found it quite confusing.

#Anyway, this is my cheeky solution:

#test_student_typed("if True else False", not_typed_msg="No inline if expression")
#test_student_typed("if ii > 2", not_typed_msg="No if filter in list comp")



#.check_body().set_context(ii=1).check_ifs(0)


```

--- type:NormalExercise lang:python xp:100 skills:2 key:23e667966f
## Part checks (2)

#### pass 1 -

```
with open('test.txt') as f:
    print(f.read().replace('\n','\n\n'))
```

#### pass 2 - 

```
with open('test.txt') as f:
    for ii in f.readlines(): print(ii)
```

#### fail 1 - "No with block"

```
f = open('test.txt')
for ii in f: print(ii)
```

#### fail 2 - "Incorrect output"

```
with open('test.txt') as f:
    for ii in f: print('no')
```

*** =pre_exercise_code
```{python}
open('test.txt', 'w').write('a\nb\nc\n')
```

*** =sample_code
```{python}
with open('test.txt') as f:
    for ii in f:
        print(ii)
```

*** =solution
```{python}
with open('test.txt') as f:
    for ii in f:
        print(ii)
```

*** =sct
```{python}

#I remembered `missing_msg` kwarg from chat today; couldn't find it in docs
# Also I remembered `check_with`; I wouldn't know how to find it in docs
# Eventually found it at bottom of part checks but general user will not know 
# to look there.


# I tried this:
#Ex().check_with(0, missing_msg="No with block").check_body().has_equal_output()
#but it didn't work so i went for the following which doesn't quite satisfy the task as my SCT requires a for loop

#Ex().check_with(0, missing_msg="No with block").check_body().check_for_loop(0).check_body().has_equal_output( "Incorrect output")



```

--- type:NormalExercise lang:python xp:100 skills:2 key:1b865f62b7
## Expression tests (1)

#### fail 1 - "wrong if test"

```
def callback():
    if select1.value == 'WRONGVAL':
        select2.value = 1
    else:
        select2.value = 2
```

#### fail 2 - "need assign select2 value in if"

```
def callback():
    if select1.value == 'a':
        pass
    else:
        select2.value = 2
```

#### fail 3 - "wrong select2 value in if"

```
def callback():
    if select1.value == 'a':
        select2.value = 'WRONGVAL'
    else:
        select2.value = 2
```

#### fail 4 - "wrong select2 value in else"

```
def callback():
    if select1.value == 'a':
        select2.value = 1
    else:
        select2.value = 'WRONGVAL'
```



*** =pre_exercise_code
```{python}
class Select:
    """Calls self.callback whenever self.value is set"""
    
    def __init__(self, value):
        self.callback = None
        self._value = value
        
    def on_change(self, cb):
        self.callback = cb
    
    @property
    def value(self): return self._value
    
    @value.setter
    def value(self, x):
        self._value = x
        if self.callback: self.callback()

```

*** =sample_code
```{python}
select1 = Select(value='a')
select2 = Select(value=1)

# ONLY MODIFY HERE
def callback():
    if ____ == ____:
        select2.value = ____
    else:
        select2.value = ____
#

select1.on_change(callback)
```

*** =solution
```{python}
select1 = Select(value='a')
select2 = Select(value=1)

# ONLY MODIFY HERE
def callback():
    if select1.value == 'a':
        select2.value = 1
    else:
        select2.value = 2
#

select1.on_change(callback)
```

*** =sct
```{python}
# DO NOT MODIFY
for name in ['select1', 'select2']:
    Ex().has_equal_value(expr_code = name+'.value')
# Put SCTs below here ----


## I don't understand what's required of me. Am i supposed to modify the solution as well as SCT?

## Time permitting, I'll return to this question.

```

--- type:NormalExercise lang:python xp:100 skills:2 key:82a04869ae
## Expression tests (2)

#### pass

```
def f(c, b=1, *args, **kwargs):
    if c > 1: return c + b
```

#### pass

```
def f(c, b=1, *args, **kwargs):
    print(args)
    if c > 1: return c + b
```

#### fail 1 - "b should be kw arg"

```
def f(a, b, *args, **kwargs): 
    if a > 1: return a + b
```

#### fail 2 - "incorrect if test"

```
def f(a, b=1, *args, **kwargs):
    if a == 1: return a + b
```


*** =pre_exercise_code
```{python}

```

*** =sample_code
```{python}
def f(a, b=1, *args, **kwargs): 
    if a > 1: return a + b
```

*** =solution
```{python}
def f(a, b=1, *args, **kwargs):
    if a > 1: return a + b
```

*** =sct
```{python}
# HBA note: for fail 2, shoud msg be "b should have a default value"?

fun_def = Ex().check_function_def("f")

#  I tried the following but it didn't work and i dont understand why
#fun_def.check_body().check_if_exp(0)

# Also, I tried things such as the following to no success:
fun_def.check_body().check_if_else(0).set_context(a=3).check_body().has_equal_value()

#Spent ~25min on this

```

--- type:NormalExercise lang:python xp:100 skills:2 key:40d94c3753
## Logic tests (1)

#### pass

```
import pandas as pd

x = pd.np.array([1,2,3])
```

#### fail 1 - "numpy array w/wrong values"

```
import numpy as np

x = np.array([1,2])
```

#### fail 2 - "x not numpy array"

```
import numpy as np

x = [1,2,3]
```

*** =pre_exercise_code
```{python}

```

*** =sample_code
```{python}
import numpy as np

x = np.array([1,2,3])
```

*** =solution
```{python}
import numpy as np

x = np.array([1,2,3])
```

*** =sct
```{python}
# NOTE: write 2 SCTs below that would, on their own, pass all cases
# SCT using test_correct

# HBA: not sure I get the task: do  i write 2 SCTs that together pass all cases or does
# each alone need to pass all cases (phrase 'on their own' is ambiguous)?

# I am having the same problem as in Simple tests (1), whereby anything I write accepts a list also.

# SCT using test_or

Ex().test_or(test_student_typed("x = np.array([1,2,3])"), test_student_typed("x = pd.np.array([1,2,3])"))


#WIth more time, I would have done some regex business; ok, the above didn't work; i need to move on.
```
--- type:NormalExercise lang:python xp:100 skills:2 key:e29e74e2f3
## Processes

Only need to make solution work!


*** =instructions

*** =hint

*** =pre_exercise_code
```{python}
from bokeh.plotting import figure
p = figure(x_axis_label='fertility (children per woman)', 
           y_axis_label='female_literacy (% population)')

class A:
    def __init__(self, value): 
        self.value = value
        self.pickle_poison = p
```

*** =sample_code
```{python}
a = A(value=1)
```

*** =solution
```{python}
a = A(value=1)
```

*** =sct
```{python}

# This exercise was very confusing. For non-hardcore devs like me, they would
# try `key = A`; only after much frustration did I try `key = "__main__.A"`,
# which is confusing and doen't add value, as far as i can see. The Bokeh stuff
# is pretty distracting also. I think a simple use case from the Bokeh course
# would be both more relevant and understandable.

def my_converter(x):
    return(x.value)
set_converter(key = "__main__.A", fundef = my_converter)

Ex().check_object('a').has_equal_value()
```

--- type:NormalExercise lang:python xp:100 skills:2 key:d874e260cb
## Function Signatures

#### pass -

```
plot([1,2], [3,4], color='b')
```

#### fail 1 - "forgot a pos arg"

```
plot([1,2], color='b', shape='.')
```

#### fail 2 - "check first arg"

```
plot([1], [3,4], color='b', shape='.')
```

#### fail 3 - "forgot color"

```
plot([1,2], [3,4], shape='.')
```

#### fail 3 - "check color arg"

```
plot([1,2], [3,4], color='red', shape='.')
```


*** =pre_exercise_code
```{python}
def plot(*args, **kwargs):
    """
    args is positional arguments x, y
    kwargs may include color or shape
    """
    pass
```

*** =sample_code
```{python}
plot([1,2], [3,4], color='b', shape='.')
```

*** =solution
```{python}
plot([1,2], [3,4], color='b', shape='.')
```

*** =sct
```{python}

#tried many things but couldn't get it; not sure what to do with *args; i know how to specify
#signature when each arg has a name; can't find anything in docs wrt *args

sig = sig_from_params(param("*args", param.POSITIONAL_OR_KEYWORD))


Ex().test_function_v2("plot", params=["*args"], signature=sig)

```

--- type:NormalExercise lang:python xp:100 skills:2 key:20c3c210c6
## More Functions

#### pass 1

```
x = [1,2,3]
c.a(x).b('X', 'Y')
```

#### fail 1 - "incorrect arg for some_list"

```
c.a([1,2])
```

#### fail 2 - "forgot y arg in c.a.b"

```
c.a([1,2,3]).b('X')
```

#### fail 3 - "incorrect x arg in c.a.b"

```
c.a([1,2,3]).b('Z', 'Z')
```


*** =pre_exercise_code
```{python}
class Chain():
    def a(self, some_list):
        return self
    
    def b(self, x, y):
        print(x)
        return self

c = Chain()
```

*** =sample_code
```{python}
c.a([1,2,3]).b('X', 'Y')
```

*** =solution
```{python}
c.a([1,2,3]).b('X', 'Y')
```

*** =sct
```{python}

Ex().test_function("c.a")
Ex().test_function("c.a.b")

#Ive gone over 2hrs so will not write custom SCT feedback messages.

```
