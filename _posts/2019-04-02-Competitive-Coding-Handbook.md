#Modular Arithmetic:

Taking modular arithmetic of addition,sub,mult is as follows:
            
            (a*b) %c=(a%c*b%c)%c
            (a-b)%c=(a%c+c-b%c)%c // This means that if you are getting a negative number while you are doing a%c-b%c then you will have to find the whole %c and then add c to it in order to make it positive.
            (a+b)%C=(a%c+b%c)%c

#Taking input and giving output to a file

            freopen("filename.txt","r",srdin)
            freopen("filename.txt","w",srdout)

