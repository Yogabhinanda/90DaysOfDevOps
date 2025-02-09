**User Account Management Script - Help Guide**

**Overview**

This script is designed for user account management in Linux. It allows you to create, delete, modify passwords, and list user accounts using simple command-line arguments.

Usage

Run the script with the required action and arguments as shown below:

**1. **Create a New User****

./usermanagement.sh create USERNAME PASSWORD

Creates a new user with the specified USERNAME and PASSWORD.

If the user already exists, the script will not create a duplicate.

Example:

./usermanagement.sh create john_doe MyPassword123

**2. Delete an Existing User**

./usermanagement.sh delete USERNAME

Deletes the specified USERNAME along with its home directory.

If the user does not exist, an error message is displayed.

Example:

./usermanagement.sh delete john_doe

**3. Modify Password for an Existing User**

./usermanagement.sh modifypass USERNAME

Prompts the user to enter and confirm a new password.

Ensures that the new password matches before applying changes.

Example:

./usermanagement.sh modifypass john_doe

**4. List All Users**

./usermanagement.sh list

Displays a list of all user accounts on the system along with their UID.

Error Handling

If an invalid or missing argument is provided, the script will display a usage message.

If a user already exists when trying to create a new account, an error will be displayed.

If passwords do not match during modification, the script will prompt the user to try again.
