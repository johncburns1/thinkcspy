..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Exercises
---------
#.

    .. tabbed:: q1

        .. tab:: Question

            What do these expressions evaluate to?

            #.  ``3 == 3``
            #.  ``3 != 3``
            #.  ``3 >= 4``
            #.  ``not (3 < 4)``

                .. activecode:: ex_6_1


        .. tab:: Answer

            #. True
            #. False
            #. False
            #. False


#.  Give the **logical opposites** of these conditions.  You are not allowed to use the ``not`` operator.

    #.  ``a > b``
    #.  ``a >= b``
    #.  ``a >= 18  and  day == 3``
    #.  ``a >= 18  or  day != 3``

        .. activecode:: ex_6_2

#.

    .. tabbed:: q3

        .. tab:: Question

            Write a function which is given an exam mark, and it returns the corresponding letter grade as a string according to this
            scheme:

            .. table::

               =======   =====
               Mark      Grade
               =======   =====
               >= 90     A
               [80-90)   B
               [70-80)   C
               [60-70)   D
               < 60      F
               =======   =====

            The square and round brackets denote closed and open intervals.
            A closed interval includes the number, and open interval excludes it.   So 79.99999 gets grade C , but 80 gets grade B.

            Test your function by printing the mark and the grade for a number of different marks.

            .. activecode:: ex_6_3

        .. tab:: Answer

            .. activecode:: q3_question

                def grade(mark):
                    if mark >= 90:
                        return "A"
                    else:
                        if mark >= 80:
                            return "B"
                        else:
                            if mark >= 70:
                                return "C"
                            else:
                                if mark >= 60:
                                    return "D"
                                else:
                                    return "F"

                mark = 83
                print( "Mark:", str(mark), "Grade:", grade(mark))


#.  Modify the turtle bar chart program from the previous chapter so that the bar for any value
    of 200 or more is filled with red, values between [100 and 200) are filled yellow,
    and bars representing values less than 100 are filled green.

    .. activecode:: ex_6_4
       :nocodelens:

#.

    .. tabbed:: q5

        .. tab:: Question

            In the turtle bar chart program, what do you expect to happen if one or more
            of the data values in the list is negative?   Go back and try it out.  Change the
            program so that when it prints the text value for the negative bars, it puts
            the text above the base of the bar (on the 0 axis).

            .. activecode:: ex_6_5
               :nocodelens:

        .. tab:: Answer

            .. activecode:: answer_ex_6_5
                    :nocodelens:

                    import turtle

                    def drawBar(t, height):
                        """ Get turtle t to draw one bar, of height. """
                        t.begin_fill()               # start filling this shape
                        if height < 0:
                            t.write(str(height))
                        t.left(90)
                        t.forward(height)
                        if height >= 0:
                            t.write(str(height))
                        t.right(90)
                        t.forward(40)
                        t.right(90)
                        t.forward(height)
                        t.left(90)
                        t.end_fill()                 # stop filling this shape



                    xs = [48, -50, 200, 240, 160, 260, 220]  # here is the data
                    maxheight = max(xs)
                    minheight = min(xs)
                    numbars = len(xs)
                    border = 10

                    tess = turtle.Turtle()           # create tess and set some attributes
                    tess.color("blue")
                    tess.fillcolor("red")
                    tess.pensize(3)

                    wn = turtle.Screen()             # Set up the window and its attributes
                    wn.bgcolor("lightgreen")
                    if minheight > 0:
                        lly = 0
                    else:
                        lly = minheight - border

                    wn.setworldcoordinates(0-border, lly, 40*numbars+border, maxheight+border)


                    for a in xs:
                        drawBar(tess, a)

                    wn.exitonclick()


#.  Write a function ``findHypot``.  The function will be given the length of two sides of a right-angled triangle and it should return
    the length of the hypotenuse.  (Hint:  ``x ** 0.5`` will return the square root, or use ``sqrt`` from the math module)

    .. activecode:: ex_6_6
        :nocodelens:

        from test import testEqual

        def findHypot(a,b):
            # your code here

        testEqual(findHypot(12.0, 5.0), 13.0)
        testEqual(findHypot(14.0, 48.0), 50.0)
        testEqual(findHypot(21.0, 72.0), 75.0)
        testEqual(findHypot(1, 1.73205), 1.999999)

#.

    .. tabbed:: q7

        .. tab:: Question

           Write a function called ``is_even(n)`` that takes an integer as an argument
           and returns ``True`` if the argument is an **even number** and ``False`` if
           it is **odd**.

           .. activecode:: ex_6_7
               :nocodelens:

               from test import testEqual

               def is_even(n):
                   # your code here

               testEqual(is_even(10), True)
               testEqual(is_even(5), False)
               testEqual(is_even(1), False)
               testEqual(is_even(0), True)

        .. tab:: Answer

            .. activecode:: q7_answer
                :nocodelens:

                from test import testEqual

                def is_even(n):
                    if n % 2 == 0:
                        return True
                    else:
                        return False

                testEqual(is_even(10), True)
                testEqual(is_even(5), False)
                testEqual(is_even(1), False)
                testEqual(is_even(0), True)


#. Now write the function ``is_odd(n)`` that returns ``True`` when ``n`` is odd
   and ``False`` otherwise.

   .. activecode:: ex_6_8
       :nocodelens:

       from test import testEqual

       def is_odd(n):
           # your code here

       testEqual(is_odd(10), False)
       testEqual(is_odd(5), True)
       testEqual(is_odd(1), True)
       testEqual(is_odd(0), False)

#.

    .. tabbed:: q9

        .. tab:: Question

           Modify ``is_odd`` so that it uses a call to ``is_even`` to determine if its
           argument is an odd integer.

           .. activecode:: ex_6_9
               :nocodelens:

               from test import testEqual

               def is_odd(n):
                   # your code here

               testEqual(is_odd(10), False)
               testEqual(is_odd(5), True)
               testEqual(is_odd(1), True)
               testEqual(is_odd(0), False)


        .. tab:: Answer

            .. activecode:: q9_answer
                :nocodelens:

                from test import testEqual

                def is_even(n):
                    if n % 2 == 0:
                        return True
                    else:
                        return False

                def is_odd(n):
                    if is_even(n):
                        return False
                    else:
                        return True

                testEqual(is_odd(10), False)
                testEqual(is_odd(5), True)
                testEqual(is_odd(1), True)
                testEqual(is_odd(0), False)


#.  Write a function ``is_rightangled`` which, given the length of three sides of a triangle,
    will determine whether the triangle is right-angled.  Assume that the third argument to the
    function is always the longest side.  It will return ``True`` if the triangle
    is right-angled, or ``False`` otherwise.

    Hint: floating point arithmetic is not always exactly accurate,
    so it is not safe to test floating point numbers for equality.
    If a good programmer wants to know whether
    ``x`` is equal or close enough to ``y``, they would probably code it up as

    .. sourcecode:: python

      if  abs(x - y) < 0.001:      # if x is approximately equal to y
          ...


    .. activecode:: ex_6_10
        :nocodelens:

        from test import testEqual

        def is_rightangled(a, b, c):
            # your code here

        testEqual(is_rightangled(1.5, 2.0, 2.5), True)
        testEqual(is_rightangled(4.0, 8.0, 16.0), False)
        testEqual(is_rightangled(4.1, 8.2, 9.1678787077), True)
        testEqual(is_rightangled(4.1, 8.2, 9.16787), True)
        testEqual(is_rightangled(4.1, 8.2, 9.168), False)
        testEqual(is_rightangled(0.5, 0.4, 0.64031), True)

#.

    .. tabbed:: q11

        .. tab:: Question

            Extend the above program so that the sides can be given to the function in any order.

            .. activecode:: ex_6_11
                :nocodelens:

                from test import testEqual

                def is_rightangled(a, b, c):
                    # your code here

                testEqual(is_rightangled(1.5, 2.0, 2.5), True)
                testEqual(is_rightangled(16.0, 4.0, 8.0), False)
                testEqual(is_rightangled(4.1, 9.1678787077, 8.2), True)
                testEqual(is_rightangled(9.16787, 4.1, 8.2), True)
                testEqual(is_rightangled(4.1, 8.2, 9.168), False)
                testEqual(is_rightangled(0.5, 0.64031, 0.4), True)

        .. tab:: Answer

            .. activecode:: q11_answer
                :nocodelens:

                from test import testEqual

                def is_rightangled(a, b, c):
                    is_rightangled = False

                    if a > b and a > c:
                        is_rightangled = abs(b**2 + c**2 - a**2) < 0.001
                    elif b > a and b > c:
                        is_rightangled = abs(a**2 + c**2 - b**2) < 0.001
                    else:
                        is_rightangled = abs(a**2 + b**2 - c**2) < 0.001
                    return is_rightangled

                testEqual(is_rightangled(1.5, 2.0, 2.5), True)
                testEqual(is_rightangled(4.0, 8.0, 16.0), False)
                testEqual(is_rightangled(4.1, 8.2, 9.1678787077), True)
                testEqual(is_rightangled(4.1, 8.2, 9.16787), True)
                testEqual(is_rightangled(4.1, 8.2, 9.168), False)
                testEqual(is_rightangled(0.5, 0.4, 0.64031), True)


#.  (GRADED) A year is a **leap year** if it is divisible by 4, unless it is a century that is not divisible by 400.

    For example:

    - 1956 is a leap year because 1956 is divisible by 4.
    - 1957 is not a leap year, because it is not divisible by 4.
    - 1900 is not a leap year, despite the fact that it is divisible by 4, because 1900 is a century and 1900 is not divisible by 400.
    - 1600 is a leap year, because 1600 is divisible by 4 and 1600 is divisible by 400

    Write a function `isLeap` that takes a year as a parameter and returns ``True`` if the year is a leap year, ``False`` otherwise.

    .. activecode:: ex_6_12
        :nocodelens:

        def isLeap(year):
            # your code here

        # Below is a set of tests so you can check if your code is correct.
        # Do not copy this part into Vocareum.
        from test import testEqual

        testEqual(isLeap(1944), True)
        testEqual(isLeap(2011), False)
        testEqual(isLeap(1986), False)
        testEqual(isLeap(1956), True)
        testEqual(isLeap(1957), False)
        testEqual(isLeap(1800), False)
        testEqual(isLeap(1900), False)
        testEqual(isLeap(1600), True)
        testEqual(isLeap(2056), True)

#.

    .. tabbed:: q13

        .. tab:: Question

            Implement the calculator for the date of Easter.

            The following algorithm computes the date for Easter Sunday for any year between 1900 to 2099.

            Ask the user to enter a year.
            Compute the following:



                1. a = year % 19
                #. b = year % 4
                #. c = year % 7
                #. d = (19 * a + 24) % 30
                #. e = (2 * b + 4 * c + 6 * d + 5) % 7
                #. dateofeaster = 22 + d + e


            Special note: The algorithm can give a date in April.  Also, if the year is one of four special
            years (1954, 1981, 2049, or 2076) then subtract 7 from the date.

            Your program should print an error message if the user provides a date that is out of range.

            .. activecode:: ex_6_13


        .. tab:: Answer

            .. activecode:: answer_ex_6_13

                year = int(input("Please enter a year"))
                if year >= 1900 and year <= 2099:
                    a = year % 19
                    b = year % 4
                    c = year % 7
                    d = (19*a + 24) % 30
                    e = (2*b + 4*c + 6*d + 5) % 7
                    dateofeaster = 22 + d + e

                    if year == 1954 or year == 1981 or year == 2049 or year == 2076:
                        dateofeaster = dateofeaster - 7

                    if dateofeaster > 31:
                        print("April", dateofeaster - 31)
                    else:
                        print("March", dateofeaster)
                else:
                    print("ERROR...year out of range")
