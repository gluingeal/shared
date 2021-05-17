# Pracovní list - Checklist

Icon source: [https://iconarchive.com/show/100-flat-icons-by-graphicloads/check-icon.html]

```python
## 1 Příprava
import tkinter
from tkinter import END, ANCHOR

###Definice okna
root = tkinter.Tk()
root.title('Checklist')
root.iconbitmap('check.ico')
root.geometry('400x400')
root.resizable(0,0)

###Run the root window
root.mainloop()

## 2

#Define fonts and colors
my_font = ('Times New Roman', 12)
root_color = '#6c1cbc'
button_color = '#e2cff4'

root.config(bg=root_color)

## 3

#Define functions

#Define layout

#Create frames

## 4

#Create frames
input_frame = tkinter.Frame(root,bg=root_color)
output_frame = tkinter.Frame(root,bg=root_color)
button_frame = tkinter.Frame(root,bg=root_color)

input_frame.pack()
output_frame.pack()
button_frame.pack()

## 5

#Input frame layout
list_entry = tkinter.Entry(input_frame)
list_add_button = tkinter.Button(input_frame, text="Add Item")
list_entry.grid(row=0,column=0)
list_add_button.grid(row=0,column=1)

edit:
list_entry = tkinter.Entry(input_frame, width=35, borderwidth=3, font=my_font)
list_add_button = tkinter.Button(input_frame, text="Add Item", borderwidth=2, font=my_font, bg=button_color)

## 6

#Output frame layout
my_listbox = tkinter.Listbox(output_frame)
my_listbox.grid(row=0,column=0)

edit:
my_listbox = tkinter.Listbox(output_frame, height=15, width=45, borderwidth=3, font=my_font)

## 7 Button frame layout

list_remove_button = tkinter.Button(button_frame, text="Remove Item")
list_clear_button =  tkinter.Button(button_frame, text="Clear List")
save_button = tkinter.Button(button_frame, text="Save List")
quit_button = tkinter.Button(button_frame, text="Quit")

list_remove_button.grid(row=0, column=0)
list_clear_button.grid(row=0, column=1)
save_button.grid(row=0, column=2)
quit_button.grid(row=0, column=3)

edit:

list_remove_button = tkinter.Button(button_frame, text="Remove Item",borderwidth=2, font=my_font, bg=button_color)
list_clear_button =  tkinter.Button(button_frame, text="Clear List",borderwidth=2, font=my_font, bg=button_color)
save_button = tkinter.Button(button_frame, text="Save List",borderwidth=2, font=my_font, bg=button_color)
quit_button = tkinter.Button(button_frame, text="Quit",borderwidth=2, font=my_font, bg=button_color)
edit2:

quit_button = tkinter.Button(button_frame, text="Quit",borderwidth=2, font=my_font, bg=button_color, command=root.destroy)

## 8 Design

list_entry.grid(row=0,column=0, padx=5, pady=5)
list_add_button.grid(row=0,column=1, padx=5, pady=5, ipadx=5)

### 9
list_remove_button.grid(row=0, column=0, padx=2, pady=10)
list_clear_button.grid(row=0, column=1, padx=2, pady=10, ipadx=10)
save_button.grid(row=0, column=2, padx=2, pady=10, ipadx=10)
quit_button.grid(row=0, column=3, padx=2, pady=10, ipadx=25)

### Scroll bar
my_scrollbar = tkinter.Scrollbar(output_frame)
my_scrollbar.grid(row=0,column=1,sticky="NS")

### Add button
list_add_button = tkinter.Button(input_frame, text="Add Item", borderwidth=2, font=my_font, bg=button_color, command=add_item)

def add_item():
    my_listbox.insert(END, list_entry.get())
    list_entry.delete(0,END)

### Link scrollbar to listbox
my_scrollbar.config(command=my_listbox.yview)
my_listbox = tkinter.Listbox(output_frame, height=15, width=45, borderwidth=3, font=my_font,yscrollcommand=my_scrollbar.set)


### remove item
list_remove_button = tkinter.Button(button_frame, text="Remove Item",borderwidth=2, font=my_font, bg=button_color, command=remove_item)

def remove_item():
    my_listbox.delete(ANCHOR)

### clear list
list_clear_button =  tkinter.Button(button_frame, text="Clear List",borderwidth=2, font=my_font, bg=button_color, command=clear_list)

def clear_list():
    my_listbox.delete(0, END)

### save list
save_button = tkinter.Button(button_frame, text="Save List",borderwidth=2, font=my_font, bg=button_color, command=save_list)

def save_list():
    with open('checklist.txt', 'w') as f:
        list_tuple = my_listbox.get(0, END)
        #print(list_tuple)
        for item in list_tuple:
            f.write(item + '\n')


### open list after run program if exists one

def open_list():
    try: 
        with open('checklist.txt', 'r') as f:
            for line in f:
                my_listbox.insert(0, line)
    except:
        return


open_list()

### fix function

def save_list():
    with open('checklist.txt', 'w') as f:
        list_tuple = my_listbox.get(0, END)
        #print(list_tuple)
        for item in list_tuple:
            if item.endswith('\n'):
                f.write(item)
            else:
                f.write(item + '\n')

def open_list():
    try: 
        with open('checklist.txt', 'r') as f:
            for line in f:
                my_listbox.insert(END, line)
    except:
        return

```
