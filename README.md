# symmetric-prime-pairs
def is_prime(num):
    """Determine whether a given number is prime.
    
    Parameters:
        num (int): The number to be tested for primality.
    
    Returns:
        bool: True if num is prime, False otherwise.
    """
    if num < 2:
        return False
    if num % 2 == 0:
        return num == 2
    for i in range(3, int(num**0.5) + 1, 2):
        if num % i == 0:
            return False
    return True

# Prompt the user to input an even number.
while True:
    try:
        even_number = int(input("Please enter an even number: "))
        if even_number % 2 == 0:
            break
        else:
            print("The number is not even. Try again.")
    except ValueError:
        print("Invalid input. Please enter an integer.")

# Compute n as half of the input even number.
n = even_number // 2
print(f"n (half of the input) = {n}")

# Set the initial candidates for L and R based on the parity of n.
if n % 2 == 0:
    L = n - 1
    R = n + 1
else:
    L = n - 2
    R = n + 2

# Iteratively adjust L and R until both are prime.
while not (is_prime(L) and is_prime(R)):
    L -= 2
    R += 2

# Output the resulting symmetric prime pair and verify the equality.
print(f"Symmetric prime pair found: L = {L}, R = {R}")
print(f"Verification: L + R = {L + R} = 2 * {n} = {2 * n}")
