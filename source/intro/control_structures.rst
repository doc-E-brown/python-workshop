Control Structures
===================

Quantum computing excluded, all programming languages execute each of the statements line by line.  So how do we control the execution of the statements? What if we want to execute a line of code before another? This is where control structures come into play.

Throughout this section we will discuss each of the following control structures and where they can be used:

* if statements
* else statements
* elif (else if) statements
* while loops
* for loops

There is one more try ... except, but we will cover this later.

Once you reach the point where you need to use control structures in your code, you should probably be primarily entering your code as a Python script and only using the interactive interpreter for checking / debugging.  Of course you can enter the code into interpreter, but it is far less time consuming and generally more convenient that the interpreter.


General Control Structure
-------------------------

Almost all programming languages use a similar syntax to specify control structures. They pretty much all follow the format (ignore the < > symbols, they are simply being used to denote the start and end of particular fields):

| **<name of structure>** <a test condition which if true the program will execute>
|   <some character to indicate the start of the structure>
|   <the statements to execute within the structure>
|   <some character to indicate the end of the structure>


Test Conditions and Relational Operators
-----------------------------------------
The test conditions are the key to control structures and usually are the source of head scratching when troubleshooting incorrect programming flow within the code.  A control structure will execute only if the test condition is ``True`` or **non-zero**.  By convention in programming and computer science an integer value of 0 is interpreted as ``False`` and any non-zero character is interpreted as ``True``. 
``True`` and ``False`` are keywords within Python and can be assigned to variables as values.  


.. note::
    A **Keyword** is a reserved tag within Python that cannot be used as names of variables

So for clarification, if a variable or statement evaluates to be the following it will be considered as ``False``:

* Zero (0)
* An empty string ("")
* ``False``
* ``None`` (another keyword, we will cover this later)


Relational / Comparative Operators
------------------------------------

The following operators can be used to make comparisons within Python:

.. table:: Relational Operators
   :widths: auto

   ========  ========================
   Symbol    Meaning
   ========  ======================== 
   >         Greater than
   <         Less than
   >=        Greater than or equal to
   <=        Less than or equal to
   ==        The same as 
   !=        Not the same as
   ========  ========================

.. note:: Exercise
   Try out some of the operators in the interpreter

   .. code:: python 

      100 > 10
      12 < 123
      11 >= 11
      age = 23 # Note assignment not comparison
      limit = 40 # Note assignment not comparison
      age >= limit
      age == limit
      age != limit
      True == False
      True != True
      True == True

Compounding Relational Operators
--------------------------------

You can join relational expressions together to test multiple expressions at the same time.  These compound tests can
be completed using:

.. table::

    ========= =====================================================================================
    Operator  Operation
    ========= =====================================================================================
    ``and``   Logical And (two statements must **both** be True for the result to be True
    ``or``    Logical Or (**either** one of the statements must be True for the result to be True)
    ``not``   Inverse the result of the statement (True becomes False and vice versa)
    ========= =====================================================================================

.. note:: Exercise
   Try out some of the operators in the interpreter

   .. code:: python 

      (100 < 10) and (100 > 10)
      (100 > 10) and (100 > 10)
      result = (10 > 100) or (10 < 100)
      not_result = not result
      
      result = (10 > 100) or (10 > 100)
      not_result = not result


if Statement
-------------

The ``if`` statement will only execute specific code if the test condition is ``True``.  If the test condition is not
``True`` the program will ignore the conditional code.  

.. image:: if_statement.svg

The structure of an ``if`` statement in Python syntax is as follows:

.. code:: python
   :number-lines:

   if condition_is_true:
       statement_1
       statement_2
   statement_3 # Not executed as part of the if statement


So what is important here?


1. The ``if`` keyword which indicates the control structure is an ``if`` statement.
2. The condition to execute
3. The colon at the end of line 1, this indicates that the following statements are to be part of the control structure
4. The newline after the colon.
5. The indentation of each of the lines within the statement.  This is really important and can be confusing, the
   statements within the structure must be indented by the **same amount**.  If they are not, either a syntax error will
   be thrown or the statement will not be executed.
6. The control structure is terminated by a new line.  

.. tip:: **PEP8 Tip**
    Use 4 spaces to indent the line NOT the TAB key, this is almost a universal Python convention.  Depending on the
    text editor TAB can be interpreted differently and can give painful results when moving between text editors.  One
    of the great things about the IDLE editor is that indentation is mostly handled for you, once you press the enter
    key after a **colon (:)** the next line is automatically indented.

    Keep this in mind as indentation is used everywhere in Python!!

Example if statements:

.. doctest::

   >>> if True:
   ...     print("The if statement worked!")
   The if statement worked!

   >>> if False:
   ...     print("The if statement did not work")
   >>> print("Does this statement print?")
   Does this statement print?

   >>> age = 18
   >>> if (age >= 18): # 18 is the Legal age of drinking in Australia ;)
   ...     print("Sweet, let's have a beer!") 
   ...     print("Or maybe something else...?")
   Sweet, let's have a beer!
   Or maybe something else...?

   >>> if "":
   ...     print("Blank string is True?") 

.. tip::
   Do not hesitate to use brackets or parentheses to group expressions and control the order of operation.  It is good
   practice, ensures correct execution and adds to clarity to group statements with brackets.


else Statement
--------------

The ``else`` statement will only execute specified code if the test condition is ``False``.  If the test condition is ``True`` the
statements within the ``if`` structure will be executed and **NOT** the statements following the ``else`` statement.  The ``else``
statement will execute last.

.. image:: if_else_statement.svg

The structure of an ``else`` statement in Python syntax is as follows:

.. code:: python
   :number-lines:

   if condition_is_false:
       statement_1
       statement_2
   else:
       statement_4
       statement_5
   statement_3 # Not executed as part of the if statement

So what is important here? 

1. The ``if`` statement: you cannot have an ``else`` statement without an ``if`` statement
2. The test condition of the ``if`` statement must evaluate to ``False``
3. The ``else`` keyword on its own line
4. The colon (:) following the ``else`` statement, this indicates that the following statements are part of the control structure
5. The new line after the colon (:)
6. The indentation of each of the lines within the statement.  All the same rules apply as with the ``if`` statement.

You can only have **one** else statement in an if/else structure.

Let's try some more examples:

.. doctest::

   >>> if False:
   ...     print("The if statement worked!")
   ... else:
   ...     print("The else statement worked!")
   The else statement worked!

   >>> age = 17
   >>> if (age >= 18): # 18 is the Legal age of drinking in Australia ;)
   ...     print("Sweet, let's have a beer!") 
   ... else:
   ...     print("Or maybe something else...?")
   Or maybe something else...?

   >>> if "":
   ...     print("Blank string is True?") 
   ... else:
   ...     print("The blank string is not True")
   The blank string is not True


else if (elif) Statement
-------------------------

The ``elif`` (else if) statement allows for additional conditions to be added to the control structure.  The statements within the ``elif``
structure will only be executed **if and only if** the test condition with the original if statement is ``False`` and the test
condition of the ``elif`` statement is ``True``. 
 

Unlike the else and if statements, you can have multiple elif statements within a single control structure.  This allows
for responding to multiple conditions.  In C / C++ / Java this is similar to a switch statement. Python does not have
the concept of a switch statement, instead use ``elif`` statements.

The structure of an ``elif`` statement in Python syntax is as follows:

.. image:: elif_statement.svg

The structure of an ``elif`` statement in Python syntax is as follows:

.. code:: python
   :number-lines:

   if condition_is_false:
       statement_1
       statement_2
   elif condition_is_true:
       statement_6
       statement_7
   else:
       statement_4
       statement_5
   statement_3 # Not executed as part of the if statement

So what is important here? 

1. The ``if`` statement: you cannot have an ``else`` statement without and ``if`` statement.
2. The test condition of the ``if`` statement must evaluate to ``False``.
3. The ``elif`` keyword must be on its online, followed by the test condition.
4. The **colon (:)** following the test condition, this indicates that the following statements are part of the control structure
5. The new line after the **colon (:)**
6. The indentation of each of the lines within the statement.  All the same rules apply as with the ``if`` statement.

Let's try some examples:

.. doctest::

   >>> age = 18
   >>> if (age > 18):
   ...     print("Sweet, let's have a beer!") 
   ... elif (age == 18):
   ...     print("Can I please see some ID?")
   ... else:
   ...     print("Or maybe something else...?")
   Can I please see some ID?


   >>> temperatureFlag = 0
   >>> pressureFlag = 1
   >>> humidityFlag = 0

   >>> if temperatureFlag:
   ...    print("Temperature flag is set") 
   ... elif pressureFlag:
   ...    print("Pressure flag is set") 
   ... elif humidityFlag:
   ...    print("Humidity flag is set") 
   ... else:
   ...    print("All is well")
   Pressure flag is set


Looping Structures
------------------

Looping structures execute a body of code subject repeatedly subject to some condition.  There are two types of loops within Python:

* ``while`` loops
* ``for`` loops


while Loops
-----------

``while`` loops are the most simple looping structures within Python.  ``while`` loops continue to execute a block of code, while the test condition remains ``True``.    The syntax is as follows:

.. code:: python
   :number-lines:

   while condition_is_true:
       statement_1
       statement_2
   statement_3 # Not executed as part of the loop 

The test condition of the ``while`` statement is evaluated first and at each stage in the loop after statement 2 and thus has the following properties.

* If the condition statement (*condition_is_true*) in the above example is not ``true`` then *statement_1* and *statement_2* will not be executed.
* After executing *statement_1* and *statement_2* the test condition *condition_is_true* is no longer evaluates the ``True`` the loop will not continue.  After executing *statement_2* the condition statement will be checked again to see if the loop needs to run another time.

.. warning::
   If the test condition never evaluates to be ``False`` the look will continue forever, this is known as an **infinite loop** and can be a common programming error.  This is particularly the case if the loop is dependent on other events such as user input or the processing of some other information.  If your program seems to "hang" an infinite loop may be the cause of your problems.

Try this simple looping structure 

.. doctest::

   >>> num = 0
   >>> while (num < 5):
   ...     print(num)
   ...     num += 1 # Without this line we will get an infinite loop!!!
   0
   1
   2
   3
   4

.. note::
   **Question** Why would an infinite loop occur without the line ``num += 1`` 

and compare to:

.. doctest::

   >>> num = 0
   >>> while (num < 5):
   ...     num += 1
   ...     print(num)
   1
   2
   3
   4
   5

As described above if the test condition is not ``True`` when the interpreter arrives at the while loop the contents of the loop will not execute.

.. doctest::

   >>> num = 0
   >>> while (num > 5):
   ...     num += 1
   ...     print(num)


for Loops
-----------

``for`` loops are arguably the most powerful looping constructs within Python, because of how they can be used.  
A ``for`` loop takes a data than can be iterated (looped) through such as lists or tuples of numbers (we will cover lists in :ref:`Data Structures`) and executes the block of code for each item in the list.  Unless otherwise specified the ``for`` loop will always execute the code for each item in the data.

The syntax of a ``for`` loop is as follows:

.. code:: python
   :number-lines:

   for item in iterable:
       statement_1
       statement_2
   statement_3 # Not executed as part of the loop 

So what is important here? 

1. The ``for`` keyword to indicate the start of the for loop
2. The variable **item**, this is a temporary variable name than can is to be used the loop and is the reference to the current value of item.  This is just a regular variable as every other in Python.  If a variable of the name specified e.g. **item** does not exist at this point it will be created at this point.
3. The **colon (:)** following the iterable, this indicates that the following statements are part of the control structure
4. The new line after the colon
5. The indentation of each of the lines within the statement.  All the same rules apply as with the ``if`` statement.

Let's consider using a ``for`` loop with a simple list data structure (again we will cover lists in :ref:`Data
Structures`) we will start with a list of the following numbers: 32, 354, 754, 78, 51 for will **iterate** through the
list getting each number at a time.

.. doctest::

   >>> numbers = [32, 354, 754, 78, 51] 
   >>> for num in numbers: 
   ...     print(num)
   32
   354
   754
   78
   51

Notice that in the example above the ``for`` loop assigned each value in *numbers* to the variable *num*, **in the
order**
in which they occurred in the *numbers*.  Also notice that the variable *num* was not defined before executing the
``for`` loop.  The Python interpreter created the variable for us in the definition of the ``for`` loop, when can now
access the variable after the ``for`` loop, it will simply be the last value it was assigned during the execution of the
``for`` loop.

.. doctest::

   >>> numbers = [32, 354, 754, 78, 51] 
   >>> for num in numbers: 
   ...     print(num)
   32
   354
   754
   78
   51
   >>> num
   51

**Range Function**

One of the most common uses of ``for`` loops is to repeat a sequence of code a fixed number of times.  Say we wanted to
repeat some data analysis 10 times because we have 10 replicates of some information set.  This is where the ``range``
function is very handy.  We simply provide the ``range`` function the number of replicates and it will take care of the
rest.  Say we wanted a series of numbers 0, 1, 2, 3 we could simply call ``range(4)``.

.. note::
   The ``range`` function is known as a *half open* range function as it includes the first value, but not the last
   value in the function.  Specifying ``range(4)`` is the same as ``range(0, 4)`` and thus includes the values 0, 1, 2,
   3 but **NOT** 4; mathematically this is [0, 4).

Looking at the `Range documentation`_ we can see that the range function can take 3 values:

.. code:: python

    range(stop)
    range(start, stop, step)

Where:

* **start** is the start value of the sequence of numbers returned 
* **stop** is that half open stop value i.e. values less than stop are returned
* **step** is how much to increase or decrease each subsequent value returned from the function 

When only one number is provided to the range function it specifies the stop value.

.. _Range documentation: https://docs.python.org/3/library/stdtypes.html#range


Let's look at a few examples to solidify our understanding:

.. doctest::

    >>> for num in range(4): # stop value only
    ...     print(num)
    0
    1
    2
    3
    
    >>> for num in range(1, 5): # start & stop value
    ...     print(num)
    1
    2
    3
    4

    >>> for num in range(10, 20, 2): # start, stop & step value
    ...     print(num)
    10
    12
    14
    16
    18


    >>> for num in range(40, 30, -2): # start, stop & step value
    ...     print(num)
    40
    38
    36
    34
    32


Nesting Control Structure
--------------------------

You can embed or **nest** any of the control structures discussed above to configure the program flow to what you require.  Nesting control structures essentially combines them in a specified order to enable a logical sequence of events.  So let's consider an example where we want to find all of the even numbers between 1 and 100 (a trivial example I know):

.. note::
   Remember we can use the modulus operator (%) to determine if there are any remaining values after division.  We can check for an even number using ``num % 2 == 0``.


.. doctest::

   >>> for num in range(1, 20):
   ...     if (num % 2) == 0:
   ...         print(num)
   2
   4
   6
   8
   10
   12
   14
   16
   18

When we consider the execution of the above code, remember:

* The ``for`` loop will repeatedly execute all code that is within its scope i.e. is indented by 4 spaces more than it (this includes the ``if`` statement)
* The ``if`` statement will only execute the code that is within its scope.

.. tip::
   **PEP8** reminder.  Use four (4) spaces for indentation, **NOT** tabs!

.. note:: Exercise
   We could also write the if statement above as:

   .. code:: python 

       if not (num % 2):
           print(num)

   Why? If you are unsure execute the following statements in an interpreter to find out.

   .. code:: python 
      :number-lines:
      
       num % 2
       not (num % 2)

We can also embed for and while loops to do funky (and useful) things.  What does this piece of code do?


.. code:: python
   :number-lines:

    for i in range(10):
        for j in range(5):
            print("%d-%d", % (i, j))

This is another example of **nested loops** with the j loop nested within the i loop. 

Have a play with a bunch of different mixed, nested control structures and see what they do.  Just remember each line is
executed after the previous and the scope of the loop / if statement is controlled by the indentation.

Controlling Looping Structures
-------------------------------

So what is we want to get out of a loop early?  It is specified to run for 10000 times, but sometimes we do want this to happen and other times we don't?

**Break statements**

There is where a ``break`` comes into play.  What a break statement does is indicate to Python to exit from the current loop.  Consider the following example where we have specified the for loop to iterate 10 times, but we have a break statement when i is 5 to escape from the loop.

.. doctest::

   >>> for num in range(10):
   ...    print(num)
   ...    if (num == 5): # when num is 5 break from the loop
   ...        break
   0
   1
   2
   3
   4
   5

The key thing to remember about break statements is that they cause the interpreter to ``break`` from the **innermost**
loop.  So consider the following example:

.. doctest::

   >>> for num in range(2):
   ...    for num2 in range(100):
   ...        if (num2 == 5): # when num2 is 5 break from the loop
   ...            break
   ...        print("%d-%d" % (num, num2))
   0-0
   0-1
   0-2
   0-3
   0-4
   1-0
   1-1
   1-2
   1-3
   1-4


In this example the ``break`` statement causes the interpreter to exit the ``for num2 in range(100)`` loop but **not** the
outer ``for num in range(2)`` loop.

.. tip::
   The ``break`` statement is often used in the context of an ``if`` statement as shown in the example above.  This is
   particularly useful to look for circumstances where you no longer want to execute the rest of the loop.  If the loop
   is no longer appropriate, get out!

Continued Statements
----------------------

So what if we don't want to just exit from the loop?  We may want to selectively ignore some code within the loop and just jump back up to the top of the looping structure.  Of course we could do this by embedding code within the scope of an ``if`` statement and only executing if some condition is ``True``.  Using an ``if`` statement in this way can be useful but it can also result in a large block of code being indented within an ``if`` statement and the scenario that causes us to go back to the top of the loop occurs infrequently.  In such an example we can use the ``continue`` statement.

Consider the following example:

.. doctest::

   >>> for num in range(5):
   ...    if (num == 3): # when num is 3 jump to the top of the loop 
   ...        continue 
   ...    print(num)
   0
   1
   2
   4


Exercises
----------

1. Write a program that calculates the sum of the squares of the numbers 1 to 1000.
2. Using the area of a circle program that you created in :ref:`Variables`, modify it to repeatedly ask the user for the
   radius.  Calculate the area of the circle using the user's input and return the result.  If the user enters a 0 or
   negative value for the radius the program should terminate.
