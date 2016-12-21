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

#### fail 2 - "Your value of x is incorrect"

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
if True: ["yes" for ii in range(3)]
elif False: pass
else: pass
```

#### fail 3 - "No else statement"

```
if True: ["yes" for ii in range(3) if ii > 2]
elif False: pass
```

*** =sample_code
```{python}
if True: ["yes" if True else False for ii in range(3)]
```

*** =solution
```{python}
if True: ["yes" if True else False for ii in range(3)]
```

*** =sct
```{python}

```