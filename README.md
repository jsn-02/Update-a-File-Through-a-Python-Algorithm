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

# Call `update_file()` and pass in "allow_list.txt" and a list of IP addresses to be removed
update_file("allow_list.txt", ["192.168.25.60", "192.168.140.81", "192.168.203.198"])

# Build `with` statement to read in the updated file
with open("allow_list.txt", "r") as file:
    # Read in the updated file and store the contents in `text`
    text = file.read()

# Display the contents of `text`
print(text)
```

### Step 2: Read the File Contents

### Step : Conduct the Audit

> [!IMPORTANT]
> [Controls and Compliance Checklist](https://docs.google.com/viewer?url=https://github.com/user-attachments/files/16281064/Controls.and.Compliance.Checklist.pdf)
