# todo
A terminal todo list manager

# how to install?
Simply copy this todo file in your $PATH. 
Please remember to change it to executable.

# How does it work?
It maintain a text file under $HOME/.todo, it tracks your todo item.

# Why this?
It offer a todo tracking with simple command interface, as well a as a very good Google inbox like snooze feature, for reminding you to come back later. I love inbox snooze, however Google sunset it. What a pity.

# How to use?

Usage:
  todo + <string> : Add a todo
  todo done|d <id> <id> <id> ... : mark todos as done
  todd undo|u <id> <id> <id> ... : mark todos as undone
  todd - <id> <id> <id> ... : delete todos
  todd snooze|s <yyyyMMdd or MMdd> <id> <id> <id> ...: snooze todos to the date, default is tomorrow
  todd all : show all todos (with snoozed)
 
```
Let's add a todo.

root@bazinga ~# todo + Buy cake for my daughter
 >>>>  1  [TODO] Buy cake for my daughter 

Another todo to add:
root@bazinga ~# todo + Deposit check
 >>>>  1  [TODO] Buy cake for my daughter 
 >>>>  2  [TODO] Deposit check 
 
Another todo:
root@bazinga ~# todo + Email michael ask for meeting invitation
 >>>>  1  [TODO] Buy cake for my daughter 
 >>>>  2  [TODO] Deposit check 
 >>>>  3  [TODO] Email michael ask for meeting invitation 

Another todo:
root@bazinga ~# todo + Follow up with John on quote response
 >>>>  1  [TODO] Buy cake for my daughter 
 >>>>  2  [TODO] Deposit check 
 >>>>  3  [TODO] Email michael ask for meeting invitation 
 >>>>  4  [TODO] Follow up with John on quote response 

because 4 I can't really do anything now because I just mailed him, should check tomorrow. I don't want to see it here to bother me. 
But I want it back tomorrow so I can see it and act on it.
root@bazinga ~# todo snooze 4
Snooze id 4 to date 20200725 (1595635200) - Sat Jul 25 08:00:00 2020
 >>>>  1  [TODO] Buy cake for my daughter 
 >>>>  2  [TODO] Deposit check 
 >>>>  3  [TODO] Email michael ask for meeting invitation 
 >>>>  4  [TODO] Follow up with John on quote response  snoozed to Sat 25/Jul/2020
 
 By default todo only shows active tasks, as well as snoozed in the past, and current time is past the snoozed time.
 root@bazinga ~# todo
 >>>>  1  [TODO] Buy cake for my daughter 
 >>>>  2  [TODO] Deposit check 
 >>>>  3  [TODO] Email michael ask for meeting invitation 
 
 I still can see all snoozed todo if I do todo all.
 root@bazinga ~# todo all
 >>>>  1  [TODO] Buy cake for my daughter 
 >>>>  2  [TODO] Deposit check 
 >>>>  3  [TODO] Email michael ask for meeting invitation 
 >>>>  4  [TODO] Follow up with John on quote response  snoozed to Sat 25/Jul/2020
 
I want to mark 1 and 2 as done, because I have got the cake
root@bazinga ~# todo done 1 2
 >>>>  1  [DONE] Buy cake for my daughter 
 >>>>  2  [DONE] Deposit check 
 >>>>  3  [TODO] Email michael ask for meeting invitation 

I won't want to keep 1 and 2 because it is irrelevant. Operator "-" is used this case.
root@bazinga ~# todo - 1 2
 >>>>  1  [TODO] Email michael ask for meeting invitation 
They are gone.

I want to snooze the michael to next Month, since it is too early to ask for invitation.
root@bazinga ~# todo snooze 0901 1
Snooze id 1 to date 0901 (1598918400) - Tue Sep  1 08:00:00 2020
 >>>>  1  [TODO] Email michael ask for meeting invitation  snoozed to Tue 01/Sep/2020
 >>>>  2  [TODO] Follow up with John on quote response  snoozed to Sat 25/Jul/2020

Do I have anything to do now?
root@bazinga ~# todo
Nothing at this moment. Hoo Ray!

Nope.

Great. Time to go home.

Next day, I come back to work...
root@bazinga ~# todo
 >>>>  2  [TODO] Follow up with John on quote response 
Ah ha, I have to follow up with John. Okay email sent.

root@bazinga ~# todo done 2
 >>>>  2  [DONE] Follow up with John on quote response 

Now get rid of it.
root@bazinga ~# todo - 2
Nothing at this moment. Hoo Ray!

What else in the near future?
root@bazinga ~# todo all
 >>>>  1  [TODO] Email michael ask for meeting invitation  snoozed to Tue 01/Sep/2020

Yeah, the meeting invitation snoozed task is still there.

Hope you like it.
```
