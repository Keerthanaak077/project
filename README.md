# project
GUI scientific Calculator 
import tkinter as tk
import math

def evaluate_expression():
    try:
        expression = entry.get()
        result = eval(expression)
        result_label.config(text="Result: " + str(result))
    except Exception as e:
        result_label.config(text="Error")

def clear_entry():
    entry.delete(0, tk.END)
    result_label.config(text="Result:")

# Create the main window
root = tk.Tk()
root.title("Scientific Calculator")

# Create an entry widget for input
entry = tk.Entry(root, width=30)
entry.grid(row=0, column=0, columnspan=5)

# Create buttons for numbers and operators
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('=', 4, 2), ('+', 4, 3),
]

for (text, row, col) in buttons:
    button = tk.Button(root, text=text, width=7, height=2, command=lambda t=text: entry.insert(tk.END, t))
    button.grid(row=row, column=col)

# Create scientific functions
scientific_buttons = [
    ('sqrt', 1, 4), ('exp', 2, 4), ('log', 3, 4), ('sin', 1, 5), ('cos', 2, 5), ('tan', 3, 5),
]

for (text, row, col) in scientific_buttons:
    button = tk.Button(root, text=text, width=7, height=2, command=lambda t=text: entry.insert(tk.END, t+'('))
    button.grid(row=row, column=col)

# Create the equals button
equals_button = tk.Button(root, text="=", width=7, height=2, command=evaluate_expression)
equals_button.grid(row=4, column=4)

# Create a clear button
clear_button = tk.Button(root, text="C", width=7, height=2, command=clear_entry)
clear_button.grid(row=0, column=5)

# Create a label for the result
result_label = tk.Label(root, text="Result:")
result_label.grid(row=5, column=0, columnspan=5)
added_value = Calc()

txtDisplay = Entry(calc, font=('Helvetica',20,'bold'),
				bg='black',fg='red',
				bd=30,width=28,justify=RIGHT)
txtDisplay.grid(row=0,column=0, columnspan=4, pady=1)
txtDisplay.insert(0,"0")

root.mainloop()
numberpad = "789456123"
i=0
btn = []
for j in range(2,5):
	for k in range(3):
		btn.append(Button(calc, width=6, height=2,
						bg='black',fg='red',
						font=('Helvetica',20,'bold'),
						bd=4,text=numberpad[i]))
		btn[i].grid(row=j, column= k, pady = 1)
		btn[i]["command"]=lambda x=numberpad[i]:added_value.numberEnter(x)
		i+=1
btnClear = Button(calc, text=chr(67),width=6,
				height=2,bg='powder blue',
				font=('Helvetica',20,'bold')
				,bd=4, command=added_value.Clear_Entry
				).grid(row=1, column= 0, pady = 1)

btnAllClear = Button(calc, text=chr(67)+chr(69),
					width=6, height=2,
					bg='powder blue',
					font=('Helvetica',20,'bold'),
					bd=4,
					command=added_value.All_Clear_Entry
					).grid(row=1, column= 1, pady = 1)
btnsq = Button(calc, text="\u221A",width=6, height=2,
			bg='powder blue', font=('Helvetica',
									20,'bold'),
			bd=4,command=added_value.squared
			).grid(row=1, column= 2, pady = 1)

btnAdd = Button(calc, text="+",width=6, height=2,
				bg='powder blue',
				font=('Helvetica',20,'bold'),
				bd=4,command=lambda:added_value.operation("add")
				).grid(row=1, column= 3, pady = 1)

btnSub = Button(calc, text="-",width=6,
				height=2,bg='powder blue',
				font=('Helvetica',20,'bold'),
				bd=4,command=lambda:added_value.operation("sub")
				).grid(row=2, column= 3, pady = 1)

btnMul = Button(calc, text="x",width=6,
				height=2,bg='powder blue',
				font=('Helvetica',20,'bold'),
				bd=4,command=lambda:added_value.operation("multi")
				).grid(row=3, column= 3, pady = 1)

btnDiv = Button(calc, text="/",width=6,
				height=2,bg='powder blue',
				font=('Helvetica',20,'bold'),
				bd=4,command=lambda:added_value.operation("divide")
				).grid(row=4, column= 3, pady = 1)

btnZero = Button(calc, text="0",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=lambda:added_value.numberEnter(0)
				).grid(row=5, column= 0, pady = 1)

btnDot = Button(calc, text=".",width=6,
				height=2,bg='powder blue',
				font=('Helvetica',20,'bold'),
				bd=4,command=lambda:added_value.numberEnter(".")
				).grid(row=5, column= 1, pady = 1)
btnPM = Button(calc, text=chr(177),width=6,
			height=2,bg='powder blue', font=('Helvetica',20,'bold'),
			bd=4,command=added_value.mathPM
			).grid(row=5, column= 2, pady = 1)

btnEquals = Button(calc, text="=",width=6,
				height=2,bg='powder blue',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.sum_of_total
				).grid(row=5, column= 3, pady = 1)
btnPi = Button(calc, text="pi",width=6,
			height=2,bg='black',fg='red',
			font=('Helvetica',20,'bold'),
			bd=4,command=added_value.pi
			).grid(row=1, column= 4, pady = 1)

btnCos = Button(calc, text="Cos",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.cos
			).grid(row=1, column= 5, pady = 1)

btntan = Button(calc, text="tan",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.tan
			).grid(row=1, column= 6, pady = 1)

btnsin = Button(calc, text="sin",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.sin
			).grid(row=1, column= 7, pady = 1)
btn2Pi = Button(calc, text="2pi",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.tau
			).grid(row=2, column= 4, pady = 1)

btnCosh = Button(calc, text="Cosh",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.cosh
				).grid(row=2, column= 5, pady = 1)

btntanh = Button(calc, text="tanh",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.tanh
				).grid(row=2, column= 6, pady = 1)

btnsinh = Button(calc, text="sinh",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.sinh
				).grid(row=2, column= 7, pady = 1)
btnlog = Button(calc, text="log",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.log
			).grid(row=3, column= 4, pady = 1)

btnExp = Button(calc, text="exp",width=6, height=2,
				bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.exp
			).grid(row=3, column= 5, pady = 1)

btnMod = Button(calc, text="Mod",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=lambda:added_value.operation("mod")
				).grid(row=3, column= 6, pady = 1)

btnE = Button(calc, text="e",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.e
			).grid(row=3, column= 7, pady = 1)
btnlog10 = Button(calc, text="log10",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.log10
				).grid(row=4, column= 4, pady = 1)

btncos = Button(calc, text="log1p",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.log1p
				).grid(row=4, column= 5, pady = 1)

btnexpm1 = Button(calc, text="expm1",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd = 4,command=added_value.expm1
				).grid(row=4, column= 6, pady = 1)

btngamma = Button(calc, text="gamma",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.lgamma
				).grid(row=4, column= 7, pady = 1)
btnlog2 = Button(calc, text="log2",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.log2
				).grid(row=5, column= 4, pady = 1)

btndeg = Button(calc, text="deg",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.degrees
			).grid(row=5, column= 5, pady = 1)

btnacosh = Button(calc, text="acosh",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.acosh
				).grid(row=5, column= 6, pady = 1)

btnasinh = Button(calc, text="asinh",width=6,
				height=2,bg='black',fg='red',
				font=('Helvetica',20,'bold'),
				bd=4,command=added_value.asinh
				).grid(row=5, column= 7, pady = 1)

lblDisplay = Label(calc, text = "Scientific Calculator",
				font=('Helvetica',30,'bold'),
				bg='black',fg='red',justify=CENTER)

lblDisplay.grid(row=0, column= 4,columnspan=4)
def iExit():
	iExit = tkinter.messagebox.askyesno("Scientific Calculator",
										"Do you want to exit ?")
	if iExit>0:
		root.destroy()
		return

def Scientific():
	root.resizable(width=False, height=False)
	root.geometry("944x568+0+0")


def Standard():
	root.resizable(width=False, height=False)
	root.geometry("480x568+0+0")

menubar = Menu(calc)
filemenu = Menu(menubar, tearoff = 0)
menubar.add_cascade(label = 'File', menu = filemenu)
filemenu.add_command(label = "Standard", command = Standard)
filemenu.add_command(label = "Scientific", command = Scientific)
filemenu.add_separator()
filemenu.add_command(label = "Exit", command = iExit)


editmenu = Menu(menubar, tearoff = 0)
menubar.add_cascade(label = 'Edit', menu = editmenu)
editmenu.add_command(label = "Cut")
editmenu.add_command(label = "Copy")
editmenu.add_separator()
editmenu.add_command(label = "Paste")

root.config(menu=menubar)

root.mainloop()


