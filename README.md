# vocabulary_words.sh
# I created this bash script for my kindergartner to learn her vocabulary words. 

#!/bin/bash

# ram

# STUFF TO INSTALL BEFORE RUNNING:
# dnf install festival sl -y
# create a file called aritext with a word on each line

# 7 feb, 2016 - use the command line and text to speech to teach new words
# 9 feb, 2016 - Zach Brady helped me fix the read from file function
#             - 'words=$(cat aritext)' & 'for word in ${words}'
#             - added null to aplay line to stop output


### The greeting ###
clear
echo "hello there, my name is robot"
echo "hello there, my name is robot" | text2wave | aplay > /dev/null 2>&1
sleep 1
echo "what is your name" | text2wave | aplay > /dev/null 2>&1
echo "Whats is your name? > "
read name
echo "Your name is: $name"
echo "Hello $name, its nice to meet you" | text2wave | aplay > /dev/null 2>&1
echo "Would you like to play a game with me" | text2wave | aplay > /dev/null 2>&1
read -p "Would you like to play a game with me? " -n 1 -r
echo
if [[ ! $REPLY =~ ^[Yy]$ ]]
then
        echo "Ok, goodbye. It was nice to meet you $name." | text2wave | aplay > /dev/null 2>&1
        exit 1
fi

echo "Excellent $name. I will display a word" | text2wave | aplay > /dev/null 2>&1
sleep 1
echo "and you must type it out on the keyboard?" | text2wave | aplay > /dev/null 2>&1
sleep 1
echo "Are you ready to play?" | text2wave | aplay > /dev/null 2>&1
read -p "Are you ready to play? " -n 1 -r
echo
if [[ ! $REPLY =~ ^[Yy]$ ]]
then
        echo "Ok, goodbye. It was nice to meet you $name." | text2wave | aplay > /dev/null 2>&1
        exit 1
fi

### word loop ###
words=$(cat aritext)
for word in ${words}
do
        clear
        echo
        echo "$word  > "
        echo "the word is $word" | text2wave | aplay > /dev/null 2>&1
        echo "can you say $word" | text2wave | aplay > /dev/null 2>&1
        sleep 2
        echo "ok, lets type out the word $word on the keyboard." | text2wave | aplay > /dev/null 2>&1
        clear
        echo
        echo "$word  > "
        read input
        if [ $input == $word ]
        then
                echo "Thats correct. Good job." | text2wave | aplay > /dev/null 2>&1
        else
                echo "Thats incorrect. Try again." | text2wave | aplay > /dev/null 2>&1
                echo "ok, lets type out the word $word on the keyboard." | text2wave | aplay > /dev/null 2>&1
                clear
                echo
                echo "$word  > "
                read input
                if [ $input == $word ]
                then
                echo "Thats correct. Good job." | text2wave | aplay > /dev/null 2>&1
                else
                echo "Thats incorrect. Lets try another word." | text2wave | aplay > /dev/null 2>&1
                fi
        fi
done

clear
echo "ok, thats the last word. Lets play another time."
echo "Goodbye $name."
echo "ok, thats the last word. Lets play another time. Goodbye $name." | text2wave | aplay > /dev/null 2>&1

### added 'sl' as a fun linux goodbye ###
sl
exit 1
