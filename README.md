# Online-Book-Store
This program demonstrates my ability to program an important program using programming fundamentals. The Store is console based lol.
######### online book store ##########
books = {1 : ["The Mystic Masters Speak" , "XYZ"], 2 : ["Atomic Habits", "ABC"], 3 : ["The Realm of Pure HEart", "WRS"]}
def user_authentication():
    print("Welcome to our online Book Store :D")
    print("Login or Sign Up below (In case of Signing up, enter the email and password for your account, and then login using similar credentials)")
    user_ids = {"emails" : [], "passwords" : []}
    main_flag = True
    while main_flag == True:
        flag = True
        email = input("Please enter your email: ")
        password = input("Please enter your password: ")
        if email != "" and password != "":
            while flag == True:
                if email not in user_ids["emails"] and password not in user_ids["passwords"]:    
                    user_ids["emails"].append(email)
                    user_ids["passwords"].append(password)
                else:
                    flag = False
            book_store(books, user_ids)
        else:
            main_flag = False   
        
def book_store(books, user_ids):
    user_file = {}
    flag = True
    print("S/N", "Title(Book Name)", "Author")
    for k, v in books.items():
        for i in v:
            print(k, i, end=" ")
        print()
    for email in user_ids:
        while flag == True:
            book = input("Please write the S/N of the desired book here(Write Zero(0) if you're done enterring your books): ")
            if int(book) > 0 and int(book) <= len(books):
                for k in books:            
                    if email not in user_file:
                        user_file[email] = [books[k][0] + " by " + books[k][1]] # collection of books the user selected
                    else:
                        user_file[email] += [books[k][0] + " by " + books[k][1]]
            elif int(book) > len(books):
                print("Please enter a S/N within the given list, Thanks!")
            elif int(book) == 0:
                for item in user_file[email]:
                    print(item, end= ", ")
                print()
                print("Thank you for using our service :D")
                print("Come Again, Bye!")
                flag = False
user_authentication()        
