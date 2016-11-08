# 07_Lab

Main Lab 7 - Restaurants
Background

You find yourself wondering how your family can have such difficulty arranging a night out. Every Friday night, your family goes out to eat. The discussion of where to eat, unfortunately, is often drawn out and sometimes becomes a little heated. Thinking about the NCAA Tournament, you get a brilliant idea of how to more efficiently make a selection.

Instead of fighting over several restaurants at once, you decide to write a program that eliminates one restaurant at a time by pitting two restaurants against each other until a single restaurant remains. Your family can now decide where to eat based on answering a series of yes/no questions. While this does not eliminate all of the arguing, it does simplify the decisions to be made.
Requirements
Part 1 - The Menu (5 points)

    Prompt the user to select one of several operations:
        0 - Quit the program
        1 - Display all restaurants
        2 - Add a restaurant
        3 - Remove a restaurant
        4 - Cut the vector
        5 - Shuffle the vector
        6 - Begin the tournament

    After any operation is complete (except for quitting), re-prompt the user to select another operation (return user to your menu)
    You must require the user to input 0-6 to signify their menu choice
    For part 1, only the quit option needs to work.
    You may assume that you will be given an integer, but if an incorrect option is entered, print "INVALID SELECTION. Please try again." and re-prompt the user to select another operation (return user to your menu).

Part 2 - The Contenders (20 points)

Add functionality to display, add, and remove restaurants. Each of these should be implemented using a function and you must use a vector to hold the list of restaurants. For this lab we will use a STRING CONTAINING THE NAME of the restaurant to represent the restaruant.

    Display all restaurants
        Display the restaurant names in their current order, on separate lines, prefaced with one tab ("\t").
    Add a restaurant
        Prompt the user for a restaurant name
        If the restaurant name is not already in the vector, add it to the vector and say the restaurant name followed by " has been added."
        If the restaurant name is already in the vector, do nothing to the vector but say "That restaurant is already on the list, you can not add it again."
    Remove a restaurant
        Prompt the user for a restaurant name
        If the restaurant name is in the vector, remove it from the vector and say the restaurant name followed by " has been removed."
        If the restaurant name is not in the vector, do nothing to the vector but say "That restaurant is not on the list, you can not remove it."
    Both add and remove need to know (for different purposes) if the name given by the user is already in the list. This code should be in a "Find" function, not repeated in both places.

Part 3 - Mixing It Up (30 points)

Add functionality for cut and shuffle. Each of these should be implemented using a function.

    "Cut" the vector of restaurant names.
        Prompt the user for a number
        If the cut point is out of range say "The restaurants can not be cut there, there are only " current-number-of-restaurants " restaurants in the list."
        In this program, "cut" is like the cut operation used in card games. Take the specified number of Restaurant names off of the top of the vector of restaurant names, and put them in the same order at the bottom. If the restaurant name list contains a, b, c, and d and the cut point is 3, then after the cut the list should be: d, a, b, and c.
        Cut can be done by moving things around in the existing vector, but you might find that difficult. Instead, build a new vector as described and then return the newly assembled one from your cut function.

    "Shuffle" restaurant names in the restaurant name vector.
        In this program, "shuffle" is like the shuffle operation used in card games to mix up the cards. Split the "deck" in half, and rearrange the restaurants, alternating between the two halves, starting with the first restaurant in the second half. For instance, if the restaurant name vector contained the restaurant names: a, b, c, d, e, f, g and h, then after the shuffle, the vector would have the order e, a, f, b, g, c, h and d.
        Implement this function from scratch. Do not use arcane #includes that have not been discussed in zybooks.
        Do not allow the shuffle unless the number of restaurant names is a power of 2 (equal to 2^n for some value of n>=0). This must NOT be hard coded (i.e. do NOT use something like "if (n == 1 || n == 2 || n == 4 || n == 8...))". You must have an algorithm for solving this part. Say "The current tournament size (" current-list-length ") is not a power of two (2, 4, 8...)." followed by "A shuffle is not possible. Please add or remove resturants." if the length is not a power of two.
        Like Cut, Shuffle can be done by moving things around in the existing vector, but you might find that difficult. Instead, build a new vector as described and then return the newly assembled one from your shuffle function.

Part 4 - The Battle (20 points)

Now create at least one function and allow the user to run a tournament among the restaurants currently in the vector and report the winning restaurant name

    Each match of the tournament involves displaying two restaurant names to the user, prompting her to choose her favorite, and retaining only the winning restaurant name for the next round. As noted above, you might find it easier to construct a new vector of candidates and replace the old one rather than moving things around in place.
    You should expect the user to input either 1 or 2, signifying they prefer either the first or second restaurant, respectively.
    For each round, take restaurant names in pairs and in order. Restaurant names should appear in exactly one match in a round.
    If the user provides a response other than 1 or 2, re-prompt the user until valid information is entered.
    Do not allow the tournament to begin unless the number of restaurant names is a power of 2, Use the same check you used for the shuffle function in Part 3.

Items Evaluated by the TA's Inspection (25 points)

    The ta will check for compliance with the style guide, as always.
        Remember that you must used functions for the major features of the program, this is part of the style guide.
    You must have a "Find" function as described above in Part 2. (5 point deduction if missing)
    You must use a vector to keep track of the restaurant names. (15 point deduction if not)
    You may not make assumptions about the number of restaurant names. Your code must not limit the number of restaurant names. (10 point deduction if not)
    You may not hardcode the power of two part, as described in part 3. (5 point deduction if missing or otherwise incorrect)
    Implement the shuffle function from scratch. Do not use arcane #includes that have not been discussed in zybooks. (15 point deduction if not from scratch)

Notes
Why a power of 2?

In a single-elimination tournament, every one match-up requires two players, and every match-up except for the initial match-ups (first round), requires two previous match-ups. This results in the number of players being reduced by half after each round. For example, 8 (2 to the 3rd, 2^3) players gets reduced to four after one round. The second round reduces four players to two, and the final round reduces two players to one. Six, which is not a power of two (although it is even), will not work, because after the first round, six is reduced to three, three would be reduced to 1.5, and you cannot have half a player. For a more visual explanation, examine this tournament bracket:

Contestant 1 -+
              +- Winner of (1, 2) -+ 
Contestant 2 -+                    |
                                   +- Winner of (1, 2, 3, 4) -+
Contestant 3 -+                    |                          |
              +- Winner of (3, 4) -+                          |
Contestant 4 -+                                               |
                                                              +- Winner of all
Contestant 5 -+                                               |
              +- Winner of (5, 6) -+                          |
Contestant 6 -+                    |                          |
                                   +- Winner of (5, 6, 7, 8) -+
Contestant 7 -+                    |
              +- Winner of (7, 8) -+ 
Contestant 8 -+

Notice that at any level of the tournament, the number of players is a power of two (remember that 2 to the power 0 is 1).
How do I remove from a vector?

The instinctive thought is to use something like "myvector.remove(int index)" but this will not work. "remove()" is not part of the vector library. Instead use "myvector.erase(myvector.begin() + index)" where index is the item you want to erase.
A "magic" learning moment

In order to make sure students and TAs can know just what to expect for grading purposes, we have set a strict style guideline for replacing numbers in your program with constants, except for a few specified exceptions. After this class as you grow in programming maturity, you will get a better feel for when you could use a number in your code. For example, in this program you will need to "shuffle" the items in your vector. This requires dividing your list size by 2 at some point. Should the "magic" number 2 be replaced by a constant? You could come up with a reasonably named constant, but in this simple mathematical manipulation it is pretty obvious what the 2 is trying to do. In fact, outside of 142, when you have to "wrestle" to find a reasonable name for the constant, and when even then it is not clear that it improves readability, that is probably a time when just using the number is fine. For this lab, we allow you to either use the 2 or a reasonably-named constant for this case. However, in general for this class, follow the guidelines of using constants as discussed in the style guide, unless we point out specific exceptions.
Sample Output

Welcome to the restaurant battle!


Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 47

INVALID SELECTION.  Please try again.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 2

What is the name of the restaurant you want to add? Super Taqueria

Super Taqueria has been added.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 2

What is the name of the restaurant you want to add? Super Taqueria

That restaurant is already on the list, you can not add it again.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 3

What is the name of the restaurant you want to remove? Noglu, Paris

That restaurant is not on the list, you can not remove it.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 2

What is the name of the restaurant you want to add? Noglu, Paris

Noglu, Paris has been added.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 2

What is the name of the restaurant you want to add? Cannon Center

Cannon Center has been added.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 3

What is the name of the restaurant you want to remove? Cannon Center

Cannon Center has been removed.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 2

What is the name of the restaurant you want to add? Costa Vida

Costa Vida has been added.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 2

What is the name of the restaurant you want to add? Chuy's

Chuy's has been added.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 1

Here are the current restaurants:

    "Super Taqueria"
    "Noglu, Paris"
    "Costa Vida"
    "Chuy's"

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 4

How many restaurants should be taken from the top and put on the bottom? 3


Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 1

Here are the current restaurants:

    "Chuy's"
    "Super Taqueria"
    "Noglu, Paris"
    "Costa Vida"

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 5


Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 1

Here are the current restaurants:

    "Noglu, Paris"
    "Chuy's"
    "Costa Vida"
    "Super Taqueria"

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 6

Round: 1

Type "1" if you prefer Noglu, Paris or
type "2" if you prefer Chuy's
Choice: 1

Type "1" if you prefer Costa Vida or
type "2" if you prefer Super Taqueria
Choice: 2

Round: 2

Type "1" if you prefer Noglu, Paris or
type "2" if you prefer Super Taqueria
Choice: 1

The winning restaurant is Noglu, Paris

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 3

What is the name of the restaurant you want to remove? Chuy's

Chuy's has been removed.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 6

The current tournament size (3) is not a power of two (2, 4, 8...).
A tournament is not possible. Please add or remove resturants.

Please select one of the following options:

0 - Quit the program
1 - Display all restaurants
2 - Add a restaurant
3 - Remove a restaurant
4 - "Cut" the list of restaurants
5 - "Shuffle" the list of restaurants
6 - Begin the tournament

Enter your selection now: 0

GOODBYE!
