# Update a File Through a Python Algorithm

## Scenario

You are a security professional working at a health care company. As part of your job, you're required to regularly update a file that identifies the employees who can access restricted content. The contents of the file are based on who is working with personal patient records. Employees are restricted access based on their IP address. There is an allow list for IP addresses permitted to sign into the restricted subnetwork. There's also a remove list that identifies which employees you must remove from this allow list.

Your task is to create an algorithm that uses Python code to check whether the allow list contains any IP addresses identified on the remove list. If so, you should remove those IP addresses from the file containing the allow list.

## Objective

To develop a Python algorithm that efficiently updates an allow list of IP addresses by removing any addresses that appear on a remove list. This algorithm will ensure that only authorized IP addresses can access restricted content, thereby maintaining the security of personal patient records.

### Skills Learned

- Reading and writing files in Python
- Parsing file contents
- Manipulating data structures (lists) in Python
- Implementing control flow and iteration in Python
- Applying string methods in Python

### Tools Used

- Python programming language

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

### Step 2: Read the File Contents

I converted the contents of the allow list file into a string and stored it in the `ip_addresses` variable.

```
with open(import_file, "r") as file:

  # Use `.read()` to read the imported file and store it in a variable named `ip_addresses`
  ip_addresses = file.read()
```

### Step 3: Convert the String into a List

I used the `split()` method to convert the `ip_addresses` string into a list.

```
# Use `.split()` to convert `ip_addresses` from a string to a list
ip_addresses = ip_addresses.split()
```

### Step 4: Iterate Through the Remove List

I set up the header of a `for` loop to iterate through the `ip_addresses`.

```
# Build iterative statement
# Name loop variable `element`
# Loop through `ip_addresses`
for element in ip_addresses:
```

### Step 5: Remove IP Addresses that are on the Remove List

Within the loop, I removed any IP addresses from the `ip_addresses` list that were found in the `remove_list`.

```
  # Build conditional statement
  # If current element is in `remove_list`,
    if element in remove_list:

        # then current element should be removed from `ip_addresses`
        ip_addresses.remove(element)
```

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

### Step 7: Finalize the Document

> [!IMPORTANT]
> [Controls and Compliance Checklist](https://docs.google.com/viewer?url=https://github.com/user-attachments/files/16281064/Controls.and.Compliance.Checklist.pdf)
