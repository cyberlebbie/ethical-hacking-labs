# =========================================
# SMB Enumeration and Access Validation Lab
# enum4linux + SMBClient
# =========================================

# --- Initial SMB Enumeration ---

# Enumerate SMB information from the target system
# -U : Enumerate users
# -G : Enumerate groups
# -S : Enumerate shared resources
# -P : Enumerate password policy
# -o : Enumerate OS information
# -a : Perform all enumeration techniques
enum4linux -a 10.6.6.20

# Output reveals:
# - Anonymous (null session) SMB access
# - User and group accounts
# - List of available SMB shares
# - Password policy details
# - Operating system and Samba version

# --- Validate SMB Access with SMBClient ---

# List available SMB shares using anonymous authentication
# -L : List shares
# -N : No password (null session)
smbclient -L //10.6.6.20/ -N

# Output confirms accessible shares without authentication

# --- Connect to an Exposed SMB Share ---

# Connect to the /tmp share anonymously
smbclient //10.6.6.20/tmp -N

# Successful connection indicates weak access controls

# --- Interact with the SMB Share ---

# List files and directories within the share
ls

# Create a test file on the remote share
# Demonstrates write permissions on the exposed resource
put test.txt

# Download a file from the share
# Demonstrates read permissions
get example.txt

# Exit the SMBClient interactive shell
exit
