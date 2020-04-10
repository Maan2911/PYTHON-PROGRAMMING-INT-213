import tkinter as tk
from tkinter import *
from datetime import datetime
import os
LARGE_FONT= ("Verdana", 14)
class accounts:
    totalbal=0
    accl=[]
    monsel=0
    exsel=0
    monamt=""
    amtex=""
    def __init__(self):
        self.acc = open("accounts.txt","r")
        self.accd=self.acc.readlines()
        for i in self.accd:
            self.accl=i.split(",")
        self.acc.close()
        #print(self.accl)
    def add(self):
        self.q=int(self.monsel)
        if self.q==1:
            self.i=int(self.monamt)
            self.accl[0]=int(self.accl[0])+int(self.i)
        if self.q==2:
            self.i2=self.i=int(self.monamt)
            self.accl[1]=int(self.accl[1])+int(self.i2)
        self.totalbal= int(self.accl[0])+int(self.accl[1])

    def expend(self):
        self.q=int(self.exsel)
        if self.q==1:
            self.i=int(self.amtex)
            self.accl[0]=int(self.accl[0])-int(self.i)
        if self.q==2:
            self.i2=self.i=int(self.amtex)
            self.accl[1]=int(self.accl[1])-int(self.i2)
        self.totalbal= int(self.accl[0])+int(self.accl[1])

    def writeout(self):
        self.acc2 = open("accounts.txt","w")
        for i in range (0,2):
            self.acc2.write(str(self.accl[i]))
            if i<1:
                self.acc2.write(",")
        self.acc2.close()
    def dispbal(self):
        #print("cash: ",self.accl[0],"card: ",self.accl[1])
        self.totalbal= int(self.accl[0])+int(self.accl[1])
    def reset(self):
        self.acc2 = open("accounts.txt","w")
        for i in range (0,2):
            self.acc2.write("0")
            if i<1:
                self.acc2.write(",")
        self.acc2.close()
        
acc=accounts()


class categories():
    catlist=[]
    valuelist=[]
    selection=""
    amt=""
    totalex=0
    newcat=""
    def __init__(self):
        #self.catlist=[]
        #self.valuelist=[]
        self.cat3=[]
        self.cat=open("categories.txt","r")
        self.cat1=self.cat.readlines()
        #print(self.cat1)
         
        for i in self.cat1:
            self.cat2=i.split(",")
            for i in range(0,len(self.cat2)):
                self.cat3.append(self.cat2[i])
       # print(self.cat3)
        for i in range (0,len(self.cat3)):
            if i%2==0:
                self.catlist.append(self.cat3[i])
            else:
                self.valuelist.append(int(self.cat3[i]))
        self.cat.close()
        self.totalex=sum(self.valuelist)
        #print(self.catlist,self.valuelist)
    def update(self):
        #print(self.catlist)
        self.q= self.selection
        #print(self.q)
        for i in range(0,len(self.catlist)):
            if(self.q==self.catlist[i]):
                self.z=self.amt
                #print(self.z)
                self.valuelist[i]=int(self.valuelist[i])+int(self.z)
        #print(self.catlist,self.valuelist)
        self.totalex=sum(self.valuelist)
    
    def addcat(self):
        self.q= self.newcat
        #print(self.q)
        self.catlist.append(self.q)
        self.valuelist.append(0)
        #print(self.catlist,self.valuelist)
    
    def remcat(self):
        self.q=self.newcat
        self.valuelist.pop(self.catlist.index(self.q))
        self.catlist.pop(self.catlist.index(self.q))

    def write_out(self):
        self.catout1=open("categories.txt",'w')
        for i in range(0,len(self.catlist)):
            self.catout1.write(self.catlist[i])
            self.catout1.write(",")
            self.catout1.write(str(self.valuelist[i]))
            if i!=(len(self.catlist)-1):
                self.catout1.write(",")
        self.catout1.close()

    def reset(self):
        self.catout1=open("categories.txt",'w')
        for i in range(0,len(self.catlist)):
            self.catout1.write(self.catlist[i])
            self.catout1.write(",")
            self.catout1.write(str(0))
            if i!=(len(self.catlist)-1):
                self.catout1.write(",")
        self.catout1.close()
        
cat= categories()

class statement:
    categry=""
    flg=0
    def __init__(self):
        self.now = datetime.now().date()
        self.datestr=self.now
    def writest(self):
        self.f=open("Statement.txt", "a+")
        if(self.flg==1):
            self.f.write(str(self.now)+" Debit "+str(cat.selection)+" "+str(cat.amt)+"\n")
        if(self.flg==2):
            self.f.write(str(self.now)+" Credit "+str(self.categry)+" "+str(acc.monamt)+"\n")

        self.f.close()
    def cstmnt(self):
        self.file = "notepad.exe Statement.txt"
        os.system(self.file)
    
    def reset(self):
        self.f=open("Statement.txt", "w")
        self.f.write("")
        self.f.close()


st=statement()


class framecontroller(tk.Tk):

    def __init__(self):
        
        tk.Tk.__init__(self)
        container = tk.Frame(self)


        container.pack(side="top", fill="both", expand = True)

        container.grid_rowconfigure(0, weight=1)
        container.grid_columnconfigure(0, weight=1)

        self.frames = {}

        for F in (StartPage, Adde, AddIn, Mancat):

            frame = F(container, self)

            self.frames[F] = frame

            frame.grid(row=0, column=0, sticky="nsew")

        self.show_frame(StartPage)

    def show_frame(self, cont):

        frame = self.frames[cont]
        frame.tkraise()

        
class StartPage(tk.Frame):

    def __init__(self, parent, controller):
        tk.Frame.__init__(self,parent)
        LH= tk.Label(self, text="EXPENSE MANAGER", font=LARGE_FONT)
        LH.grid(row=0, column=0)
        LBal = tk.Label(self, text="Your Current Expense for the month is :")
        LBal.grid(row=1, column=0)
        LBal1 =  tk.Label(self, text=cat.totalex)
        LBal1.grid(row=1, column=1)
        LBal2 = tk.Label(self, text="Your Current Balance for the month is :")
        LBal2.grid(row=2, column=0)
        acc.dispbal()
        LBal2 =  tk.Label(self, text=acc.totalbal)
        LBal2.grid(row=2, column=1)
        def Refresh():
            LBal1.config(text=cat.totalex)
            LBal2.config(text=acc.totalbal)
        button1 = tk.Button(self, text="Add Expense", command=lambda: controller.show_frame(Adde))
        button1.grid(row=3, column=0)
        button2 = tk.Button(self, text="Add Income", command=lambda: controller.show_frame(AddIn))
        button2.grid(row=3, column=1)
        button3= tk.Button(self, text="Refresh", command=Refresh)
        button3.grid(row=4,column=0)


class Adde(tk.Frame):

    def __init__(self, parent, controller):
        tk.Frame.__init__(self, parent)


        label = tk.Label(self, text="Add expense", font=LARGE_FONT)
        label.grid(row=0,column=0)
        Labadd= tk.Label(self, text="Choose the category :")
        Labadd.grid(row=3,column=0)
        
        tkvar = StringVar()
        
        choices= cat.catlist
        tkvar.set('Food') 
        popupMenu = OptionMenu(self, tkvar, *choices)
        Label(self, text="Choose a category :").grid(row = 1, column = 0)
        popupMenu.grid(row = 1, column =1)
        def change_dropdown(*args):
            cat.selection = tkvar.get()
        tkvar.trace('w', change_dropdown)

        outvar = StringVar()
        choices1=["Cash","Card"]
        outvar.set('Cash') 
        Label(self, text="Paid through :").grid(row = 2, column = 0)
        popupMenu1 = OptionMenu(self, outvar, *choices1)
        popupMenu1.grid(row = 2, column =1)
        def change1_dropdown(*args):
            tempsel = outvar.get()
            if(tempsel=="Cash"):
                acc.exsel=1
            if(tempsel=="Card"):
                acc.exsel=2
        outvar.trace('w', change1_dropdown)
        
        Amount= StringVar()
        EntAm= tk.Entry(self, textvariable=Amount)
        EntAm.grid(row=3,column=1)
        
        def addexpense():
            acc.amtex=EntAm.get()
            cat.amt=EntAm.get()
            cat.update()
            cat.write_out()
            acc.expend()
            acc.writeout()
            st.flg=1
            st.writest()
        
        button2 = tk.Button(self, text="Add expense", command=addexpense)
        button2.grid(row=6,column=0)
        
        
        
        button1 = tk.Button(self, text="Back to Home",
                            command=lambda: controller.show_frame(StartPage))
        button1.grid(row=7,column=0)



class AddIn(tk.Frame):

    def __init__(self, parent, controller):
        tk.Frame.__init__(self, parent)
        label = tk.Label(self, text="Add Income", font=LARGE_FONT)
        label.grid(row=0,column=0)
        Labcrd= tk.Label(self, text="Your balance is :")
        Labcrd.grid(row=1,column=0)
        Labcrd= tk.Label(self, text="Card :")
        Labcrd.grid(row=2,column=0)
        Labcrd1= tk.Label(self, text=acc.accl[1])
        Labcrd1.grid(row=2,column=1)
        Labcash= tk.Label(self, text="Cash :")
        Labcash.grid(row=3,column=0)
        Labcash1= tk.Label(self, text=acc.accl[0])
        Labcash1.grid(row=3,column=1)
        
        Labadd= tk.Label(self, text="Choose the category to add Income:")
        Labadd.grid(row=4,column=0)

        invar = StringVar()
        choices=["Cash","Bank"]
        invar.set('Bank') 
        popupMenu = OptionMenu(self, invar, *choices)
        popupMenu.grid(row = 4, column =1)
        def change_dropdown(*args):
            tempsel = invar.get()
            if(tempsel=="Cash"):
                acc.monsel=1
            if(tempsel=="Bank"):
                acc.monsel=2
            st.categry=tempsel
        invar.trace('w', change_dropdown)
        
        Labadd= tk.Label(self, text="Enter the amount")
        Labadd.grid(row=5,column=0)
        InAmount= StringVar()
        EntAm= tk.Entry(self, textvariable=InAmount)
        EntAm.grid(row=5,column=1)

        def addincome():
            acc.monamt=InAmount.get()
            acc.add()
            acc.writeout()
            st.flg=2
            st.writest()
        
        def Refresh():
            Labcrd1.config(text=acc.accl[1])
            Labcash1.config(text=acc.accl[0])

        button1 = tk.Button(self, text="Add Income", command=addincome)
        button1.grid(row=6,column=0)
        


        button1 = tk.Button(self, text="Back to Home",
                            command=lambda: controller.show_frame(StartPage))
        button1.grid(row=7,column=0)
        button3= tk.Button(self, text="Refresh", command=Refresh)
        button3.grid(row=8,column=0)

class Mancat(tk.Frame):

    def __init__(self, parent, controller):
        tk.Frame.__init__(self, parent)
        
        lab= tk.Label(self, text="These are the categories listed : ")
        lab.grid(row=0,column=0)

        cvar = StringVar()
        cvar.set('Click to see existing list') 
        popupMenu = OptionMenu(self, cvar, *cat.catlist)
        popupMenu.grid(row = 0, column =1)
        def change_dropdown(*args):
            tempsel = cvar.get()
        cvar.trace('w', change_dropdown)

        lab1= tk.Label(self, text="Enter category name if you want to add or remove a category:")
        lab1.grid(row=1,column=0)
        addcat1 = StringVar()
        Entcat= tk.Entry(self, textvariable=addcat1)
        Entcat.grid(row=1,column=1)

        def addcat():
            cat.newcat= addcat1.get()
            cat.addcat()
            cat.write_out()

        def remcat():
            cat.newcat= addcat1.get()
            cat.remcat()
            cat.write_out()


        button1 = tk.Button(self, text="Add category", command=addcat)
        button1.grid(row=2,column=1)

        button1 = tk.Button(self, text="remove category", command=remcat)
        button1.grid(row=3,column=1)

def resetb():
    cat.reset()
    acc.reset()
    st.reset()






app = framecontroller()
app.title("Expense Manager")
menubar = Menu(app)
app.config(menu=menubar)
filemenu = Menu(menubar, tearoff=0)
filemenu.add_command(label="Manage Categories", command=lambda: app.show_frame(Mancat))
filemenu.add_command(label="See Statement",command=lambda: st.cstmnt())
filemenu.add_command(label="Reset", command=lambda: resetb())
filemenu.add_command(label="Exit", command=app.quit)
menubar.add_cascade(label="Home", command=lambda: app.show_frame(StartPage)) 
menubar.add_cascade(label="Manage", menu=filemenu)


app.mainloop()
