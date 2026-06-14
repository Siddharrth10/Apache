# Apache
Code to automate the installation and configuration of the Apache web server using a shell script on a Linux server


Step 1: Create the Shell Script

Create a file called apache_setup.sh:

nano apache_setup.sh

Paste the following script into the file:

#!/bin/bash

echo "Updating package list..."
apt update -y

echo "Installing Apache..."
apt install apache2 -y

echo "Starting Apache service..."
systemctl start apache2

echo "Enabling Apache to start at boot..."
systemctl enable apache2

echo "Creating test web page..."
echo "Automation Works" > /var/www/html/index.html

echo "Checking Apache status..."
systemctl is-active apache2

echo "Done!"

Save and exit:

Press CTRL + X
Press Y
Press Enter
Step 2: Make the Script Executable

Run:

chmod +x apache_setup.sh

This gives the file permission to run as a program.

Step 3: Run the Script

Execute it with administrator privileges:

sudo ./apache_setup.sh

You should see messages showing the installation and configuration process.

What Each Line Does
Shebang
#!/bin/bash

Tells Linux to run the script using the Bash shell.

Update Package Information
apt update -y

Downloads the latest package information from Ubuntu repositories.

apt update = refresh package list
-y = automatically answer "yes" when prompted
Install Apache
apt install apache2 -y

Installs the Apache web server package.

Start Apache
systemctl start apache2

Starts the Apache service immediately.

Enable Apache at Boot
systemctl enable apache2

Configures Apache to start automatically whenever the server boots.

Create a Test Web Page
echo "Automation Works" > /var/www/html/index.html

Creates (or replaces) the default Apache web page with the text:

Automation Works

This helps verify that the script worked successfully.

Check Service Status
systemctl is-active apache2

Checks whether Apache is running.

Expected output:

active

If you see active, Apache is running correctly.

Completion Message
echo "Done!"

Displays a simple completion message.

Step 4: Verify from the Browser

Find your server's IP address:

hostname -I

Example output:

192.168.1.100

Open a browser and visit:

http://192.168.1.100

You should see:

Automation Works

If you see that message, the automation script successfully:

✅ Installed Apache
✅ Started the service
✅ Enabled automatic startup on boot
✅ Created a test web page
✅ Verified that Apache is running

Useful Verification Commands

Check service status:

sudo systemctl status apache2

Check if Apache is enabled on boot:

systemctl is-enabled apache2

Expected output:

enabled

Check the page content directly:

cat /var/www/html/index.html

Expected output:

Automation Works

This is a complete beginner-friendly Apache automation script for Ubuntu 24.04.
