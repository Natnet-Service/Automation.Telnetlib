# Automation.Telnetlib

Python code for using `telnetlib` with GNS3 (Graphical Network Simulator 3).
# Prerequisites:

GNS3 installed and configured with virtual devices (like Cisco routers or switches).
Ensure the device’s console is accessible via Telnet.
Python installed (version 3.x recommended).

Step 1: Enable Telnet on the router/switches on the GNS3 Devices using cloud
Open your GNS3 project and start the desired devices (routers/switches).
Ensure the devices are configured to accept Telnet connections.

# Follow the code bellow

        import telnetlib #to import the telnet library

        Telnet connection parameters
        HOST = #GNS3 server address
        User = #the username configured on the device
        Password = #Optional: Password for the user


        tn = telnetlib.Telnet(Host)
      

        # If login is required, enter username and password
        if user:
            tn.read_until(b"Username: ")
            tn.write(User.encode('ascii') + b"\n")

        if password:
            tn.read_until(b"Password: ")
            tn.write(password.encode('ascii') + b"\n")

        #try to configure your device by entering the  commands (e.g., 'show ip interface brief')
        tn.write(b"enable\n")
        tn.write(b"#password\n")
        tn.write(b"show ip interface brief\n")
        tn.write(b"exit\n")


        # Read all output from the Telnet session
        output = tn.read_all().decode('ascii')
