RSSFeedFilter
=============

Simple RSS Feed Filter with python
ead your trigger configuration from a triggers.txt file every time your application starts, and use the triggers specified there.

Consider the following example trigger configuration file:

        # subject trigger named t1
        t1 SUBJECT Google

        # title trigger named t2
        t2 TITLE buys

        # phrase trigger named t3
        t3 PHRASE develop application

        # composite trigger named t4
        t4 AND t2 t3

        # the trigger set contains t1 and
        t4
        ADD t1 t4
        
The example file specifies that four triggers should be created, and that two of those triggers should be added to the trigger list:

A trigger that fires when a subject contains the word 'Google' (t1).

A trigger that fires when the title contains the word 'buys' 

and the news item contains the phrase 'develop application' somewhere (t4).

The two other triggers (t2 and t3) are created but not added to the trigger set directly. They are used as arguments for the composite AND trigger's definition (t4).

Each line in this file does one of the following:

is blank

is a comment (begins with a #)

defines a named trigger

adds triggers to the trigger list.

Each type of line is described below.

Blank: blank lines are ignored. A line that consists only of whitespace is a blank line.

Comments: Any line that begins with a # character is ignored.

Trigger definitions: Lines that do not begin with the keyword ADD define named triggers. The first element in a trigger definition is the name of the trigger. The name can be any combination of letters without spaces, except for "ADD". The second element of a trigger definition is a keyword (e.g., TITLE, PHRASE, etc.) that specifies the kind of trigger being defined. The remaining elements of the definition are the trigger arguments. What arguments are required depends on the trigger type:

TITLE : a single word.

SUBJECT : a single word.

SUMMARY : a single word.

NOT : the name of the trigger that will be NOT'd.

AND : the names of the two other triggers that will be AND'd.

OR : the names of the two other triggers that will be OR'd.

PHRASE : a phrase.

Trigger addition: A trigger definition should create a trigger and associate it with a name but should not automatically add that trigger to the running trigger list. One or more ADD lines in the .txt file will specify which triggers should be in the trigger list. An addition line begins with the ADD keyword. Following ADD are the names of one or more previously defined triggers. These triggers will be added to the the trigger list.
