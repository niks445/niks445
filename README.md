import math
import datetime as dt
current_datetime = dt.datetime.now()
print("$---Welcome to library Management System---$")
while(True):
    print("Enter '1' to borrow book")
    print("Enter '2' to return book")
    print("Enter '3' to exit")

    num = int(input("Enter a Number :"))
    print("\n\n")
    if num == 1:
        def dictionary_Books():
            file = open("books.txt","r")
            dictionary ={}
            
            bookID = 1
            for line in file:
                line = line.replace("\n","")
                dictionary[bookID] = line.split(",")
                bookID = bookID + 1
            file.close()
            return dictionary

        
       
        dict = dictionary_Books()
        print(" {:<10} {:<33} {:<13} {:<13} {:<10} ".format('BookID',' BookName' ,'Author', ' Quantity',' Price'))
        for key,value in dict.items():
            BookID = key
            BookName, Writer, Quantity, Price = value
            print(" {:<10} {:<30} {:<20} {:<10} {:<10} ".format(BookID,BookName , Writer, Quantity, Price))
        
        ID = int(input("Enter Book ID :"))
        print("\n")
      
        if int(dict[ID][2]) < 1:
           print("Book is not available!!!\n")

        else:
            print("Book is available and you can borrow book !!!\n")

        while(True):
            Name = input("Enter the name of Person who will be borrow Book :")
            print("\n")
            print("The price of Book is :",(dict[ID][3]))
            print("\n")
            print("Date and Time",current_datetime) 
            print("\n\n")
            dict1 = int(dict[ID][2]) -1
            dict[ID][2] = dict1
            print("The dictionary after borrow : \n" + str(dict))
            print("\n")
            print(" {:<10} {:<33} {:<13} {:<13} {:<10} ".format('BookID', ' BookName' ,'Author', ' Quantity',' Price'))
            for key,value in dict.items():
                BookID = key
                BookName, Author, Quantity, Price = value
                print(" {:<10} {:<30} {:<20} {:<10} {:<10} ".format(BookID, BookName , Author, Quantity, Price))
            while(True):
                print("Have this person borrowed another book as well?")
                print("\n")
                
                
                continuation = input("if 'yes' please enter 'y' or else provide any other value :")
                if continuation == "y" or continuation == "y":
                    print("\n\n")
                    ID = int(input("Enter the ID of Book You Want to borrow :"))
                    print("\n")
                    print("The price of Book is :",(dict[ID][3]))
                    print("\n")
                    print("Date and Time",current_datetime)
                    print("\n")
                    dict2 = int(dict[ID][2]) -1
                    dict[ID][2] = dict2
                    print("The dictionary after borrow : \n" + str(dict))
                    print("\n")
                    print(" {:<10}{:<33} {:<13} {:<13} {:<10} ".format('BookID',' BookName' ,'Author', ' Quantity',' Price'))
                    #
                    for key,value in dict.items():
                        BookID = key
                        BookName, Author, Quantity, Price = value
                        print(" {:<10}{:<30} {:<20} {:<10} {:<10} ".format(BookID, BookName , Author, Quantity, Price))
                        #print("\n")
                        

                else:
                    print("\n")
                    print("---------------------------------------Customer Details----------------------------------------")
                    print("Customer Name :" + Name)
                    print("Total price of book :" ,dict[ID][3])
                    print("Total book are borrowed :\n" ,dict[ID][1])
                    print("----------------------------------END-------------------------------------------")
                    print("\n\n")
                    break

            break
            



            

           

    elif num == 2:

        def returning_Books():
            file = open("books.txt","r")
            dictionary = {}

            bookID   = 2
            for line in file:
                line = line.replace("\n","")
                dictionary[bookID] = line.split(",")
                bookID = bookID + 1
                file.close()
                return dictionary

            dict = returning_Books()
            print(" {: <10} { : <33} {:<13} {:10} ".format('BookID','BookName','Author','Quantity','Price'))
            for key,value in dict.items():
                bookID = key
                BookName, Writer, Quantity, Price = value
                print(" {: <10} { : <33} {:<13} {:10} ".format(BookID, BookName, Writer, Quantity, Price))

            ID = int(input("Enter book ID which you want to return : "))
            print("\n")

            if int(dict[ID][2]) < 1:
                print("Invalid input!!!\n")

            else:
                print("yes! you can return the book: ")

        while(True):
            Name = input("Enter the name of person who want to return a book: ")
            print("\n")

            dict2 = int(dict[ID][2]) + 1
            dict[ID][2] = dict2
            print("The dictionary after returning: \n " + str(dict))
            print("\n")
            print(" {: <10} { : <33} {:<13} {:10} ".format('BookID', 'BookName', 'Author', 'Quantity', 'Price'))
            for key, value in dict.items():
                BookID = key
                BookName, Writer, Quantity, Price = value
                print(" {: <10} { : <33} {:<13} {:10} ".format(BookID, BookName, Writer, Quantity, Price))






        #print("you will now return the book")






        
    elif num == 3:
        print("Thankyou for using our Library Management System")

        break
    else:
        print("Invalid Number !!!!\n Please provide value as 1, 2 or 3 \n\n")


