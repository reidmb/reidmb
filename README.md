from sympy import isprime
from math import floor, log10

def num_digits(n):
    return floor(log10(n))+1

def digit_in_pos(n, pos):
    return (n // 10**pos) % 10

def set_digit(n, pos, new):
    "change digit in given position to new value"
    old = digit_in_pos(n, pos)
    return n + (new - old)*10**pos

def is_digitally_delicate_prime(n):
    if not isprime(n):
        return False
    nd = num_digits(n)
    for pos in range(nd):
        for newdigit in range(10):
            if digit_in_pos(n, pos) == newdigit:
                continue
            m = set_digit(n, pos, newdigit)
            if isprime(m):
                print("m = ", m)
                return False
    return True

for p in [294001, 505447, 584141, 604171, 971767, 1062599]:
    print(is_digitally_delicate_prime(p))
   
