# vocabulary_words.sh
I created this bash script for my kindergartner to learn her vocabulary words.
I use festival, a text to speech application to speak to the kid like a robot.
The script asks them their name, and if they would like to play a game. Answering y or n (yes/no) will continue or stop the script.
Once they want to continue, it will pull the first word from the top of the wordlist and work it's way thru the loop. The loop asks them to say the word, then it asks them to use the keyboard and type it out.
If it's spelled it correctly, the script will pick the next word in the wordlist. If they are incorrect it asks them to try again. If it's incorrect once more it will move on to the next word.

# STUFF TO INSTALL BEFORE RUNNING:
# dnf install festival sl -y or yum install festival sl -y or apt-get install festival sl -y
# create a file called "wordlist" with a word on each line
