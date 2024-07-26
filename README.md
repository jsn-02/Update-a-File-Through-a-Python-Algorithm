# Update a File Through a Python Algorithm

## Scenario

You are a security professional working at a health care company. As part of your job, you're required to regularly update a file that identifies the employees who can access restricted content. The contents of the file are based on who is working with personal patient records. Employees are restricted access based on their IP address. There is an allow list for IP addresses permitted to sign into the restricted subnetwork. There's also a remove list that identifies which employees you must remove from this allow list.

Your task is to create an algorithm that uses Python code to check whether the allow list contains any IP addresses identified on the remove list. If so, you should remove those IP addresses from the file containing the allow list.

## Objective

To develop a Python algorithm that efficiently updates an allow list of IP addresses by removing any addresses that appear on a remove list. This algorithm will ensure that only authorized IP addresses can access restricted content, thereby maintaining the security of personal patient records.

### Skills Learned

- Reading and writing files
- Parsing file contents
- Manipulating data structures (lists)
- Implementing control flow and iteration
- Applying string methods

### Tools Used

<img src="https://img.shields.io/badge/-Python-306998?&style=for-the-badge&logo=python&logoColor=white" />

## Steps

### Step 1: Open the File that Contains the Allow List

I assigned a string containing the file name "allow_list.txt" to the `import_file` variable. Then, I used a `with` statement to open it and stored the `file` content in the file variable.

```
# Assign `import_file` to the name of the file

import_file = "allow_list.txt"

# Assign `remove_list` to a list of IP addresses that are no longer allowed to access restricted information.

remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

# First line of `with` statement

with open(import_file, "r") as file:
```

> The `with` statement ensures the file is properly closed after its suite finishes. The `open` function is used to open the file in read mode (`'r'`).

### Step 2: Read the File Contents

I converted the contents of the allow list file into a string and stored it in the `ip_addresses` variable.

```
with open(import_file, "r") as file:

  # Use `.read()` to read the imported file and store it in a variable named `ip_addresses`

  ip_addresses = file.read()
```

> The `read()` method reads the entire content of the file and stores it as a string in the `ip_addresses` variable.

### Step 3: Convert the String into a List

I used the `split()` method to convert the `ip_addresses` string into a list.

```
# Use `.split()` to convert `ip_addresses` from a string to a list

ip_addresses = ip_addresses.split()
```

> The `split()` method splits the string into a list of IP addresses based on whitespace by default.

### Step 4: Iterate Through the Remove List

I set up the header of a `for` loop to iterate through the `ip_addresses`.

```
# Build iterative statement
# Name loop variable `element`
# Loop through `ip_addresses`

for element in ip_addresses:
```

> The `for` loop iterates over each element in the `ip_addresses` list.

### Step 5: Remove IP Addresses that are on the Remove List

Within the loop, I removed any IP addresses from the `ip_addresses` list that were found in the `remove_list`.

```
  # Build conditional statement
  # If current element is in `remove_list`,

    if element in remove_list:

        # then current element should be removed from `ip_addresses`

        ip_addresses.remove(element)
```

> The `if` statement checks if the current element exists in the `remove_list`. If it does, the `remove()` method deletes it from the list. This works efficiently as there are no duplicates in the `ip_addresses` list.

### Step 6: Update the File with the Revised List of IP Addresses

I converted the `ip_addresses` list back into a string using the `join()` method and wrote the updated string back to the file.

```
# Convert `ip_addresses` back to a string so that it can be written into the text file

ip_addresses = " ".join(ip_addresses)

# Build `with` statement to rewrite the original file

with open(import_file, "w") as file:

  # Rewrite the file, replacing its contents with `ip_addresses`

  file.write(ip_addresses)
```

> The `join()` method combines the list elements into a single string separated by spaces. The `with` statement opens the file in write mode (`'w'`) and the `write()` method writes the updated string back to the file.

### Step 7: Turn the Code into a Function and Call It

I encapsulated the entire process into a function named `update_file`.

```
# Define a function named `update_file` that takes in two parameters: `import_file` and `remove_list`
# and combines the steps you've written in this lab leading up to this

def update_file(import_file, remove_list):

    # Build `with` statement to read in the initial contents of the file

    with open(import_file, "r") as file:

        # Use `.read()` to read the imported file and store it in a variable named `ip_addresses`

        ip_addresses = file.read()

    # Use `.split()` to convert `ip_addresses` from a string to a list

    ip_addresses = ip_addresses.split()

    # Build iterative statement
    # Name loop variable `element`
    # Loop through `ip_addresses`

    for element in ip_addresses:

        # Build conditional statement
        # If current element is in `remove_list`,

        if element in remove_list:

            # then current element should be removed from `ip_addresses`

            ip_addresses.remove(element)

    # Convert `ip_addresses` back to a string so that it can be written into the text file 

    ip_addresses = " ".join(ip_addresses)

    # Build `with` statement to rewrite the original file

    with open(import_file, "w") as file:

        # Rewrite the file, replacing its contents with `ip_addresses`

        file.write(ip_addresses)
```

> The function `update_file` encapsulates the entire process of reading the allow list, removing the specified IP addresses, and writing the updated list back to the file. This modular approach makes the code reusable and easier to manage.

Then, I called it with the appropriate arguments.

```
# Call `update_file()` and pass in "allow_list.txt" and a list of IP addresses to be removed

update_file("allow_list.txt", ["192.168.25.60", "192.168.140.81", "192.168.203.198"])
```

> The function is called with the file name and the list of IP addresses to be removed as arguments

