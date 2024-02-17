from tkinter import *
from tkinter import ttk 
import requests   #used for feching data to the api

def data_get():
    city=city_name.get()
    data=requests.get("https://api.openweathermap.org/data/2.5/weather?q="+str(city_name) + "&appid=20a01944eda34a13f4a4dcecfff77197").json()
    
  

    wd_box1.config(text=data["weather"][0]["description"])
    temp_box1.config(text=str(int(data["main"]["temp"]-273)))
    p_box1.config(text=data["main"]["pressure"])
    

# data=requests.get("https://api.openweathermap.org/data/2.5/weather?q="+city_name + "&appid=20a01944eda34a13f4a4dcecfff77197").json()







win=Tk()

win.title()
win.config(bg="blue")
win.geometry("700x700")
inputbox=Label(win,text="wetherapp",font=("Time New Roman",30,"bold"))
inputbox.place(x=25,y=50,height=50,width=450)

#  ttk class is used for combobox:-combobox means show multiple names when click
city_name=StringVar()
list1=["Andhra Pradesh","Arunachal Pradesh ","Assam,Bihar"]
box=ttk.Combobox(win,text="wetherapp",font=("Time New Roman",20,"bold"),values=list1,textvariable=city_name)
box.place(x=25,y=125,height=50,width=450)



w_box=Label(win,text="wetherclimate",font=("Time New Roman",20,"bold"))
w_box.place(x=25,y=260,height=50,width=210)
w_box1=Label(win,text=" ",font=("Time New Roman",20,"bold"))
w_box1.place(x=250,y=260,height=50,width=210)

wd_box=Label(win,text="wetherdescription",font=("Time New Roman",17,"bold"))
wd_box.place(x=25,y=330,height=50,width=210)
wd_box1=Label(win,text=" ",font=("Time New Roman",20,"bold"))
wd_box1.place(x=250,y=330,height=50,width=210)

temp_box=Label(win,text="temprature",font=("Time New Roman",17,"bold"))
temp_box.place(x=25,y=400,height=50,width=210)
temp_box1=Label(win,text=" ",font=("Time New Roman",20,"bold"))
temp_box1.place(x=250,y=400,height=50,width=210)

p_box=Label(win,text="presure",font=("Time New Roman",30,"bold"))
p_box.place(x=25,y=470,height=50,width=210)
p_box1=Label(win,text=" ",font=("Time New Roman",20,"bold"))
p_box1.place(x=250,y=470,height=50,width=210)


button1=Button(win,text="done",font=("Time New Roman",30,"bold"),command=data_get)
button1.place(x=200,y=550,height=50,width=210)
win.mainloop()
