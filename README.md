#Decimal to binary conveters in two esoteric languages: brainf\*ck and whitespace

Brainf\*ck ignores everything but `+-<>[],.` and whitespace ignores everything but space, tab, and newline, so I could combine them into one text file recreated below:

    > ------>>>>>>> - >>>>>>>>>>>>>>>>>>-->> + >---->>>----->>--->>>>>>
    +>+>+>+++++++[------<++++++]----- [ ->+ ] -<<<<<------------------
    ------------------------------	>,	-------- ----- - - - -----	---------
    ------------------>,	------------------------------------------
    ------	>,	---------------- ------------ --------- ---------	-->,----
    ----------------------------------------	[---->++++	]----<	[+++++
    +[------ <++++++]---- [-->++]--<[-<] +++++++ [------<++++++]---[--
    -> +++]--->>>>+<+>----------[<->++++++++++>]>[<]<<<+>----------
    [<->++++++++++>>]>>[<]<<<<+>----------[<->++++++++++ >>>]>>>[<]
    <<<<<	+ >----------	[<->++++++++++>>>>]>>>>[<]<<<<<++++++ [------<
    ++++++]--[---->++++]----< [-]+[-<+]-<[++[--->+++]--->>>>-<<<<++
    +++ [-----< +++++ ]-----<+ +[-<+]-<]++++++	[------< ++++++]---[--->+
    ++]---	>>>> [<<<<	++++[----<++++]	---- <++++[--->+++]---<]<<<<+++++
    +	[------<++++++] - [-----> +++++]	-----<[ [-<+]-<++++[--->+++]--->>
    >>	+<<<< +++++	[----- <+++++]-----< ]+[-<+]-<<[ ++ [--->+++]--->>>-<<
    <+++++	[-----<+++++]-----<++	[-<+]-<<]	++++++ [ - -----<++++++]	---[-
    -->+++]---	>>> [<<<++++ [----<++++]-- --<++++[--- >+++]- --<]< <<++++
    ++[------<++++++] -[----->+++++]-----<[[-<+]-<<++++[--->+++]---
    >>>	+<<<+++++[---	--<+++++]-----	<]+[-<+]-<<<[ ++[--->+++]--->>-<<
    +++++[-----<+++++]-----<++[-<+]-<<<]++++++[- -----<++++++]---[-
    -->+++]--->>[ <<++++[----<++++]----<++++ [--->+++]---<]<<++++++[
    ------<++++++]-[----->+++++]-----<[[-<+]-<<<++++[--->+++]--->>
    +<<+++++[-- ---<+++++]----- <]+[-<+]-	<<<<[++[--- >+++]--->-<+++++
    [-----<+++++]-	----<++[-<+]-<	<<<]++++++[---	---<++++++]---[--->+
    + + ]-- ->[<++++[ -- --< ++ ++]---- <+++ +[--->+++ ]---<]< ++++++	[------<
    ++++++]-[----->+++++]-----< [[-<+]-<<<<++++[--->+++]--->+<+++++
    [-----<+++++]-----<]++++++[------<++++++]--[---->++++]----<] ++
    ++++	[------<++++++]---- [ -->++]	++++++++++++++++++++++++++++++++
    .<<<<<< <<<<<< << ++++++++++++++++++++	+++++++++++++++++++++++++++
    +	. > ++++++++++++++++++++++++++++++++++++++++++++++++	.> +++++++++
    +++++++++++++++++	++++++++++++++++++++++.	>+++++++++++++++++++++
    +++++++++++++++++++++++++++ .>	+++++++++++++++++++++++++++++++++
    +++++++++++++++ .>+++++++++++++++++++++++++++++++++++++++++++++
    + ++.>+ ++++++++++ +++++++ +++++ +++++ +++++ ++++++ +++++++++. >+	++++++
    +++++++++++++++++++++++++++++++++++++++++.>+++++++++++++++++++
    +++++++++++++++++++ +++++++ +++.> +++++++++++++++	++++++++++++++++
    +++++++++++++++++.>+++++++++++++++++++++++++++++++++++++++++++
    +++++.>++++++++++++++++++++++++++++++++++++++++++++++++.>+++++
    +++++++++++++++++++++++++++++++++++++++++++.>+++++++++++++++++
    +++++++++++++++++++++++++++++++.>++++++++++++++++++++++++++++++++++++++++++++++++[-]++++++++++.


##Brainf\*ck - https://en.wikipedia.org/wiki/Brainfuck

base10to2.bf has the state of the program when I finished writing the bf part. The first 32 lines document what I'm using the memory cells for, the rest is the commented version of the program above.

The bf algorithm is:

    get 4 digits of input
    set flag to "not done yet" (1 in bf)
    while flag:
        increment a binary number
        increment a decimal number
        flag = 0
        for each digit in input:
            if input_digit != inc_digit
                flag = 1

See https://en.wikipedia.org/wiki/Brainfuck#Language_design for how Brainf\*ck works. When things got hairy, I used the debugger at http://mazonka.com/brainf/bfdebug.html to figure out what went wrong.

###Whitespace - https://en.wikipedia.org/wiki/Whitespace_(programming_language)

I never put comments in the whitepace code mainly because I normally used whitespace to keep my comments neat and here that would change the program. Floating words didn't look right.

The whitespace algorithm is:

    get integer input n
    while n != 0:
        push n % 2
        n := n / 2
    while stack not empty:
        x := pop
        print x

I used https://h0tsh0tt.wordpress.com/2016/07/03/whitespace-language-tutorial/ to learn how to write commands in whitespace. To write it, I used https://whitespace.kauaveel.ee/ because it shows the interpreted commands off to the right as you type in the main code area. 
