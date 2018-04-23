```

# NIH-Test-Task2
This repository contains a python program that accomplishes a variety of tasks related to prime numbers. 


import timeit
import numpy as np

# Task 2.2: Saves all prine numbers between 2 and 10,000,000,000
def is_prime(num):
    if num == 0:
        print (num, " is not prime")
        return False
    if num == 1 or num == 2:
        print (num, " is prime")
        return True
    for i in range (3, num):  #attempted: for i in range(2, int(math.sqrt(sum)) +1) but the math.sqrt seemed to be less efficent compared to current methods. 
        if num % i == 0:
            print(num, " is not prime")
            return False
    print(num, " is prime")
    return True

start_time = timeit.default_timer()
num = 2
maxNum = 10000000000 #10000000000
prms = []

while num < maxNum:
    if is_prime(num):
        prms.append(num)
    num += 1

# Task 2.3: Finds the number, sum, and average of primes in the saved variable prms. 
lenPrms = len(prms) # Calculutes number of primes in list 
sumPrms = sum(prms) # Finds the sum of the primes
avgPrms = sum(prms) / len(prms) # Calculates the average of the primes

elapsed = timeit.default_timer() - start_time

print("Number of Primes: ", lenPrms)
print("Sum of Primes: ", sumPrms)
print("Avg of Primes: ", avgPrms)
print("Elapsed Time: ", elapsed, " seconds")

# Task 2.4: Creates matrix where column 1 is prms, column 2 is prms+1, column 3 is prms/3, and column 4 is floor rounded. 
plusPrms = [x + 1 for x in prms]
divPrms = [x / 3 for x in prms]
roundPrms = [round(x, 0) for x in divPrms]
prmat = [prms, plusPrms, divPrms, roundPrms]

# Task 2.5: Sums rows and finds the average of the sums. 
def step_4_5 (p):
    plusP = [x + 1 for x in p]
    divP = [x / 3 for x in p]
    roundP = [floor(x, 0) for x in divP]
    p2 = [p, plusP, divP, roundP]
    p3 = []
    for row in range(len(p2)):
        p3.append(sum(p2[row]))
    p4 = floor(sum(p3) / len(p3))

sumPrmat = []
for row in range(len(prmat)):
    sumPrmat.append(sum(prmat[row]))

avgPrmat = math.ceil(sum(sumPrmat) / len(sumPrmat))
loopCount = 0
while avgPrmat % 2 != 0:
    if loopCount == 1000:
        print ("Never Converged")
        break
    loopCount += 1
    halfPrms = [x + 0.5 for x in prms]
    avgPrmat = step_4_5(prms)
    print ("Complete With Work")
else:
    print ("Complete")
```
