# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
def modular_exponentiation(base, exponent, modulus):
    result = 1
    while exponent > 0:
        if (exponent % 2) == 1:
            result = (result * base) % modulus
        base = (base * base) % modulus
        exponent //= 2
    return result

def diffie_hellman_key_exchange():
    p = int(input("Enter a prime number (p): "))
    g = int(input("Enter a base (g): "))

    print(f"\nPublicly known values:\nPrime (p) = {p}\nBase (g) = {g}")

    a = int(input("User A, enter your private key: "))
    A = modular_exponentiation(g, a, p)  # Compute A = g^a % p

    b = int(input("User B, enter your private key: "))
    B = modular_exponentiation(g, b, p)  # Compute B = g^b % p

    print(f"\nUser A's public key (A): {A}")
    print(f"User B's public key (B): {B}")

    shared_secret_A = modular_exponentiation(B, a, p)  # (B^a) % p
    shared_secret_B = modular_exponentiation(A, b, p)  # (A^b) % p

    print(f"\nUser A's computed shared secret: {shared_secret_A}")
    print(f"User B's computed shared secret: {shared_secret_B}")

    if shared_secret_A == shared_secret_B:
        print("\nThe shared secret key has been successfully established!")
    else:
        print("\nError: The shared secrets do not match.")

diffie_hellman_key_exchange()

```


## Output:

![image](https://github.com/user-attachments/assets/d6ac4d40-887c-4a8b-9294-3a3201d623e9)


## Result:
Thus the program is executed successfully
  The program is executed successfully

