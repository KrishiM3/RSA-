# RSA algorithm encryption and decryption
import math
from random import randint
def millerRabin(a):
    if a % 2 == 0:
        return False
    k = 0
    x = a-1
    while x % 2 == 0:
        x = x/2
        k += 1
    ## test if probably prime

    y = int(x)
    i = 1
    test1 = False
    while test1 == False:
        n = pow(2,y,a)
        test1 = True
        if n == 1 or n == -1:
            return True
    test2 = False
    counter = 0
    while counter < k:
        n = pow(n,2,a)
        counter += 1
        if n == 1:
            return False
        elif n == a-1:
            return True
        else:
            test2 = False
    return False

def gcd(a,b):
    if b == 0:
        return a
    else:
        return gcd(b,a%b)
def egcd(a, b):
    s = 0; old_s = 1
    t = 1; old_t = 0
    r = b; old_r = a

    while r != 1:
        quotient = old_r // r
        old_r, r = r, old_r - quotient * r
        old_s, s = s, old_s - quotient * s
        old_t, t = t, old_t - quotient * t

    # return gcd, x, y
    return r, s, t

def modularInv(a, b):
    gcd, x, y = egcd(a, b)

    if x < 0:
        x += b

    return x

def keys():
    oneChoice = input("enter 1 if you would like to make your own keys. Enter 2 if you would like random more secure keys.Enter 3 if you'd like 128 bit keys")
    while oneChoice != "1" and oneChoice != "2" and oneChoice != "3":
        print("that is not a valid option please try again")
        oneChoice = input("enter 1 if you would like to make your own keys. Enter 2 if you would like random more secure keys.Enter 3 if you'd like 128 bit keys ")
    if oneChoice == "1":
#will now obtain a value for p
        primep = False
        integerp = False
        dCounterp = 0
        while primep != True or integerp != True:
            primep = False
            integerp = False
            dCounterp = 0
            p = (input("please insert an integer number which you think is prime. 3+ digits is ideal if this message repeats when your number is prime it is not valid"))
            if integerp == False:
                try:
                    int(p)
                    integerp = True
                    print(integerp)
                    if integerp is True:
                        if int(p) > 1:
                            for i in range(2, int((math.sqrt(int(p))+1))):
                                if (int(p) % i) == 0:
                                    dCounterp += 1
                                    primep = False
                                    print("the number you have submitted is not prime, it is divisible by", i,"please try another number")
                                    break
                            if dCounterp == 0:
                                primep = True
                                print("primep is", primep,)
                        else:
                            print("the number you have inserted must be greater than one to be a prime number")
                            primep = False
                except ValueError:
                    print("the number you have entered is not an integer")
                    integerp = False
        print("you have picked number", p,)

#will now obtain a value for q and check if it satisfies the correct requirements
        primeq = False
        integerq = False
        dCounterq = 0
        while primeq != True or integerq != True or int(q) < (256 // int(p))+1:
            primeq = False
            integerq = False
            dCounterq = 0
            print("please insert another integer number which you think is prime,that is greater than", (256 // int(p))+1, "if this message repeats when your number is prime it is not valid")
            q = (input(""))
            if integerq is False:
                try:
                    int(q)
                    integerq = True
                    print(integerq)
                    if integerq is True:
                        if int(q) > (256 // int(p))+1 and int(q) != int(p):
                            for i in range(2, int((math.sqrt(int(q)) + 1))):
                                if (int(q) % i) == 0:
                                    dCounterq += 1
                                    primeq = False
                                    print("the number you have submitted is not prime, it is divisible by", i,"please try another number")
                                    break
                            if dCounterq == 0:
                                primeq = True
                                print("primeq is", primeq, )
                        else:
                            print("the number you have inserted must be greater than" ,  (256 // int(p))+1, "and cannot be the same number as the first prime")
                            primeq = False
                except ValueError:
                    print("the number you have entered is not an integer")
                    integerq = False
                print("you have picked the number", q,)
        N = int(p) * int(q)
        print(N)
        phi = ((int(p)) - 1) * ((int(q)) - 1)
        print(phi)
        for e in range(2, phi):
            if gcd(e, phi) == 1:
                break
        d = modularInv(e, phi)

        print(d)
        print(int((d * e) % phi))
        print("your public key is", "(", e, ",", N, ") write this down")
        print("your private key is", "(", (int(d)), ",", N, ") keep this safe.")
        menu()
    elif oneChoice == "2":
        primep = False
        dCounterp = 0
        primeq = False
        dCounterq = 0
        while primep is False:
            primep = False
            dCounterp = 0
            p = randint(100000000000,999999999999)
            for i in range(2, int((math.sqrt(int(p)) + 1))):
                if (int(p) % i) == 0:
                    dCounterp += 1
                    primep = False
                    break
            if dCounterp == 0:
                primep = True
        while primeq is False:
            primeq = False
            dCounterq = 0
            q = randint(100000000000,999999999999)
            for i in range(2, int((math.sqrt(int(q)) + 1))):
                if (int(q) % i) == 0:
                    dCounterq += 1
                    primeq = False
                    break
            if dCounterq == 0:
                primeq = True
        print("p is", p, "and q is", q,)
        N = int(p) * int(q)
        phi = ((int(p)) - 1)*((int(q))-1)
        k = 1
        for e in range(2, phi):
            if gcd(e, phi) == 1:
                break
        d = modularInv(e, phi)
        print(d)
        print(int((d*e) % phi))
        print("your public key is","(",e, ",",N ,") write this down")
        print("your private key is", (int(d), N,), "keep this safe.")
        menu()
    else:
        primep = False
        while primep == False:
            p = randint(pow(2,63)+1,pow(2,64)-1)
            #p = 314285031901
            if millerRabin(p) == True:
                primep = True
            else:
                primep = False
        print(p , "is prime")
        primeq = False
        while primeq == False:
            q = randint(pow(2,63)+1,pow(2,64)-1)
            #q = 314285031901
            if millerRabin(q) == True:
                primeq = True
            else:
                primeq = False
        N = int(p) * int(q)
        phi = ((int(p)) - 1) * ((int(q)) - 1)
        k = 1
        for e in range(2, phi):
            if gcd(e, phi) == 1:
                break
        d = modularInv(e, phi)
        print(int((d * e) % phi))
        print("your public key is", "(", e, ",", N, ") write this down")
        print("your private key is", (int(d), N,), "keep this safe.")
        menu()

#### encryption software now
def encrypt():
    cipher = ""
    msg = str(input("input the message you wish to encrypt"))
    p1integer = False
    while p1integer is False:
        p1 = input("input the first number of your public key")
        try:
            int(p1)
            p1integer = True
        except ValueError:
            print("the number you have inserted is not a number, please enter a valid public key")
            p1integer = False
    p2integer = False
    while p2integer is False:
        p2 = input("input the second number of your public key")
        try:
            int(p2)
            p2integer = True
        except ValueError:
            print("the number you have inserted is not a number, please enter a valid public key")
            p2integer = False
    e, N = int(p1), int(p2)
    print(e, N)
    for char in msg:
        temp = ord(char)
        c = pow(temp, e, N) # (temp**e)%N
        cipher += str(c) + " "
    print("your cipher is:", cipher)
    menu()

def decrypt():
    original = ""
    Valid = False
    while Valid == False:
        cipher = input("input the message you wish to decrypt")
        try:
            cipher.split()
            Valid = True
        except ValueError:
            print("you haven't inputted a valid cipher text, there must only be spaces between the numbers")
            Valid = False
    p1integer = False
    while p1integer is False:
        p1 = input("input the first number of your private key")
        try:
            int(p1)
            p1integer = True
        except ValueError:
            print("the number you have inserted is not a number, please enter a valid private key")
            p1integer = False
    p2integer = False
    while p2integer is False:
        p2 = input("input the second number of your private key")
        try:
            int(p2)
            p2integer = True
        except ValueError:
            print("the number you have inserted is not a number, please enter a valid private key")
            p2integer = False
    d, N = int(p1), int(p2)
    chars = cipher.split()
    for char in chars:
        char = int(char)
        m = pow(char, d, N)
        original += str(chr(m))
    print("the decrypted message is:", original)
    menu()

def menu():
    option = input("welcome to RSA software.Press 1 to create a public and private key,Press 2 to encrypt a message,Press 3 to decrypt a message,press 4 to end the program")
    while option != "1" and option != "2" and option != "3" and option != "4":
        print(" that is not an option")
        option = input("welcome to RSA software.Press 1 to create a public and private key,Press 2 to encrypt a message,Press 3 to decrypt a message,Press 4 to end the program")
    if option == "1":
        keys()
    elif option == "2":
        encrypt()
    elif option == "3":
        decrypt()
    elif option == "4":
        print("thank you for using the program")
menu()
