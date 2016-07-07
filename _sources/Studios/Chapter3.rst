Studio: Donuts
==============

Pre-studio
----------

For the pre-studio, we wrote a program that allowed us to calculate how many pints of beer would be able to afford in London if we sold a certain quantity of flags. (The problem statement is a bit more complicated than that, so be sure to watch the video.)

.. raw:: html

    <div style="text-align:center;"><iframe width="560" height="315" src="https://www.youtube.com/embed/DOdDWxgaBKY" frameborder="0" allowfullscreen></iframe></div>

.. activecode:: prestudio_3

    # prompt for dollar to pound exchange
    pounds_per_dollar = input("Current dollar-to-pound exchange rate: ")
    pounds_per_dollar = float(pounds_per_dollar)

    # prompt for number of flags to sell
    num_flags = input("How many flags did you sell? ")
    num_flags = int(num_flags)

    # create variables for fixed values (cost flag, cost of pint)
    pounds_per_pint = 3.79
    dollars_per_flag = 3

    # calculate how much a flag costs in pounds
    pounds_per_flag = dollars_per_flag * pounds_per_dollar

    # calculate how many pounds I'll have after selling them all
    revenue = num_flags * pounds_per_flag

    # calculate number beers I can buy with that amount of money
    num_pints = revenue / pounds_per_pint
    num_pints = int(num_pints)

    # print out number of pints
    print("You can afford", num_pints, "pints of beer!")

Studio
------

Here's the scenario:

You run a hip new artisanal donut shop, the Loop Hole, which, in its short lifetime, has already rocked the boutique-desserts market with numerous "disruptions", including:

* a minimalist menu consisting of just one type of donut per day: Manager's Special... always Manager's Special.
* giving customers the option to order fractional amounts of donuts, e.g. 1.7 donuts, please.
* a progressive pay-what-you-want pricing system, in which the customer pays what s/he thinks is a fair price. (Of course, you do provide a "suggested price".)

Now it's time to implement your latest innovation, an app via which users can pre-order donuts remotely from the convenience of... the command-line terminal on their computer.

In the editor below, write a program which introduces the flavor of the day, and then takes the user's order.

Taking their order involves asking two questions:

1. How many donuts do they want to buy?
2. How much do you want to pay per donut?
3. Inform the user of the total cost of their order.
4. Don't forget to include sales-tax, which is, let's say, 5%.

Here's an example of how the finished program should behave:

.. sourcecode:: python

    Welcome to the Loop Hole!
    Today's Manager's Special is:
    Crunch Jelly: A traditional jelly donut in which the jelly filling is made entirely of Capn' Crunch Berries Oops All Berries
    How many would you like?
    >>> 3.33333
    How much would you like to pay per donut (suggested price is $4.35 each)?
    >>> 2.5
    Ok, let me prepare that for you....
    After tax, your total is: $8.74999125
    Thank you for snacking! Loop back around here soon!

Notice that the total price ``$8.74999125`` went way beyond 2 decimal places. Obviously it would be a little nicer to round that to $8.75. We haven't learned this yet, but you'll be able to do this later. Don't worry about it now.

(Also, don't be concerned if your program gives an answer with a slightly different number of decimal places than the example program above. This is just a precision issue.)

For the Manager's Special, you can make something up (you are the Manager, after all), or just use the Crunch Berries example. Whatever you decide, you can simply hard-code it directly into your code. In other words, the flavor doesn't actually have to change depending on what day it is. The important part of this Studio is the math involved in calculating the cost of the user's order.

.. activecode:: studio_3
