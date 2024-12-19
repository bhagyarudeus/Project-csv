# Project-csv
import pandas as pd
import matplotlib.pyplot as plt
def addSweet(df):
    code = int(input("Enter the sweet code "))
    name = input("Enter the name of the sweet ")
    cost = int(input("Enter cost per kg "))
    qty = float(input("Enter quantity in kgs "))
    ig = input("Enter the main ingredient ")
    df.loc[code] = [name, cost, qty, ig]
    df.to_csv("E:\Download\sweets.csv")
    print()
    print("Added Successfully")
    print()
print("*"*10)
print("Sweet Shop")
print("*"*10)
df = pd.read_csv("E:\Download\sweets.csv")

while True:
    print()
    print("Press 1 - Add a New Sweet")
    print("Press 2 - Show all")
    print("Press 3 - Search")
    print("Press 4 - Delete")
    print("Press 5 - Update")
    print("Press 6 - Show Chart of Sweets")
    print("Press 7 - To Quit")
    n = int(input("Enter your choice : "))
    if n == 1:
        addSweet(df)
    elif n == 2:
        print("*"*50)
        print(df)
        print("*"*50)
    elif n == 3:
        code = int(input("Enter the sweet code to be searched : "))
        if code in df.index:
            print()
            print(df.loc[code])
            print()
        else:
            print("No sweet found with this code ")
    elif n == 4:
        code = int(input("Enter the sweet code to be deleted : "))
        if code in df.index:
            df.drop(code,inplace=True)
            df.to_csv("E:\Download\sweets.csv")
            print()
            print("Deleted")
            print()
        else:
            print("No sweet found with this code ")
    elif n == 5:
        code = int(input("Enter the sweet code to be updated : "))
        if code in df.index:
            name = input("Enter the updated name of the sweet ")
            cost = int(input("Enter updated cost per kg "))
            qty = float(input("Enter quantity in kgs "))
            ig = input("Enter the main ingredient ")
            df.loc[code] = [name, cost,qty,ig]
            df.to_csv("E:\Download\sweets.csv")
            print()
            print("Updated")2

            print()
        else:
            print("No sweet found with this code ")
    elif n == 6:
        plt.bar(df["Name"],df["Cost"],color="navy")
        plt.title("Rate List of Sweets")
        plt.show()
    elif n == 7:
        df.to_csv("sweets.csv",index=False)
        print("Thanks for Visiting")
        break




Name	Cost	Quantity	Ingredient
Kaju Katli	800	10	Kaju&Khoya
Gulab Jamun	550	3	Khoya
Rasgulla	560	9	Paneer
Ladoo	400	16	Boondi
