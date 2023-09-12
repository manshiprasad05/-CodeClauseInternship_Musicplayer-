# -CodeClauseInternship_Musicplayer-
import tkinter as tk
import fnmatch
import os
from pygame import mixer
canvas=tk.Tk()
canvas.title("My Music Player")
canvas.geometry("600x800")
canvas.config(bg="black")
rootpath="C:\\Users\\mansh\\OneDrive\\Desktop"
pattern="*.mp3"
mixer.init()
prev_img= tk.PhotoImage(file="C:\\Users\\mansh\\Downloads\\prev_img.png")
stop_img= tk.PhotoImage(file="C:\\Users\\mansh\\Downloads\\stop_img (1).png")
play_img= tk.PhotoImage(file="C:\\Users\\mansh\\Downloads\\play_img (1).png")
pause_img= tk.PhotoImage(file="C:\\Users\\mansh\\Downloads\\pause_img (1).png")
next_img= tk.PhotoImage(file="C:\\Users\\mansh\\Downloads\\next_img.png")
def select():
    label.config(text=listbox.get("anchor"))
    mixer.music.load(rootpath+"\\"+listbox.get("anchor"))
    mixer.music.play()
def stop():
    mixer.music.stop()
    listbox.select_clear("active")

    
listbox=tk.Listbox(canvas, fg="cyan", bg="black", width=200, font=('poppins',14))
listbox.pack(padx=15,pady=15)
label=tk.Label(canvas,text="",bg="black",fg="pink",font=('poppins',14))
label.pack(pady=15)
top=tk.Frame(canvas,bg="black")
top.pack(padx=10,pady=5,anchor="center")

prevbutton=tk.Button(canvas,text="prev", image=prev_img, bg="grey",height=50, width=50)
prevbutton.pack(pady=15,in_= top, side="left")

stopbutton=tk.Button(canvas,text="stop",image=stop_img,height=50, width=50,command=stop)
stopbutton.pack(pady=15,in_= top, side="left")

playbutton=tk.Button(canvas,text="play",image=play_img, bg="black",height=50, width=50,command= select)
playbutton.pack(pady=15,in_= top, side="left")

pausebutton=tk.Button(canvas,text="pause",image=pause_img, bg="black",height=50, width=50)
pausebutton.pack(pady=15,in_= top, side="left")

nextbutton=tk.Button(canvas,text="next",image=next_img, bg="black",height=50, width=50)
nextbutton.pack(pady=15,in_= top, side="left")

for root,dirs,files in os.walk(rootpath):
    for filename in fnmatch.filter(files,pattern):
        listbox.insert('end',filename)
canvas.mainloop()
