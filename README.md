#receive messages from a user
import datetime
import os
import time
#cleans the screen
def clear():
  if os.name == 'nt':
    os.system('cls')
  else:
    os.system('clear')
#massages the user
massege='''
1-add age date
2-show list
3-exite
4-older age
5-younger age
'''
#list of the users
user_info={}
older_user={}
start=True
#determine the timing  of his year
years=datetime.date.today().year
def date_yaer(age):
  age1=int(age)
  return years-age1
# add age date
def add_age(name,age):
  print(f"{name} age is {date_yaer(age)} years")
  user_info[name]=date_yaer(age)
#add user
def add_user():
  name=input("enter user name: ")
  age=input("enter user age: ")
  #check age==int
  if age.isdigit():
    add_age(name,age)
  else:
    print("please enter a number")
#show list
def show_list():
  for name,age in user_info.items():
    print(f"{name} age is {age} years")
  opinion=input("you like to hide the list? (y): ")
  if opinion=="y":
    time.sleep(1)
    clear()
  else:
    print("ok")
#exite
def exite():
  print("thank you for using our program")
  time.sleep(1)
  global start
  start=False
#older age
def older_age():
  for name,age in user_info.items():
    if age==min(user_info.values()):
      older_user[name]=name
      older_user['age']=age
      print(f"the older user is {name} and his age is {age} years")
  opinion=input("you like to hide the list? (y): ")
  if opinion=="y":
    time.sleep(1)
    clear()
  else:
    print("ok")
#younger age
def younger_age():
  for name,age in user_info.items():
    if age==max(user_info.values()):
      older_user[name]=name
      older_user['age']=age
      print(f"the younger user is {name} and his age is {age} years")
  opinion=input("you like to hide the list? (y): ")
  if opinion=="y":
    time.sleep(1)
    clear()
  else:
    print("ok")
#main
def main():
   while start:
     print(massege)
     choice=int(input("enter your choice: "))
     if choice==1:
       add_user()
       clear()
     elif choice==2:
        show_list()
     elif choice==3:
        exite()
     elif choice==4:
       older_age()
     elif choice==5:
       younger_age()
     else:
      print("invalid choice")
main()
