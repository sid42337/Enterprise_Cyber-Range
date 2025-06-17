# 6. Environment Setup

---

### Setting up AD DS [project-x-dc]

1. Installing modules:
    1. Selecting Role-based or featured based installation
        
        ![image.png](./data/image%2012.png)
        
    2. Select a server from the server pool
        
        ![image.png](./data/image%2013.png)
        
    3. Add “Active Directory Domain Services”, ”DHCP Server” and “DNS Server” services 
        
        ![image.png](./data/image%2014.png)
        
    4. Then in the end click the “install” button to install the services.
    
2. Promote the server to  “AD DS (Active Directory Domain Service)”
    1. Select the “Promote this server to a domain” option
        
        ![image.png](./data/image%2015.png)
        
    2. Select the “Add a new forest” and enter the name as “corp.project-x-dc.com”. Then click “Next”
        
        ![image.png](./data/image%2016.png)
        
    3. Enter the password as “@Deeboodah1!” for the Administrator Account. Click “Next”
        
        ![image.png](./data/image%2017.png)
        
    4. Install the setting.
        
        ![image.png](./data/image%2018.png)
        
    5. Restart the system and now Sign-in to “CORP\Administrator”
        
        ![image.png](./data/image%2019.png)
        
    6. Now on the “Server Manager” dashboard we can see the additional settings like AD DS, DHCP, DNS , etc.
        
        ![image.png](./data/image%2020.png)
        
    
3. Setting up DNS service on the server.
    1. Go to the “DNS” option on the left side of the dashboard.
        
        ![image.png](./data/image%2021.png)
        
    2. Right-Click on the server present in the “Servers” dialogue box. Select “DNS Manager” option from the list.
        
        ![image.png](./data/image%2022.png)
        
    3.  Now create a lookup Zone. The lookup zone will basically allow the client machines to access the internet.
        1. Right-Click on the server present in the “DNS” option in left and select “Properties”
            
            ![image.png](./data/image%2023.png)
            
        2. Go to “Forwarders”
            
            ![image.png](./data/image%2024.png)
            
        3. Go to “Edit”
            
            ![image.png](./data/image%2025.png)
            
        4. Now add Google’s DNS server IP address (8.8.8.8)
            
            ![image.png](./data/image%2026.png)
            
        5. Click “OK” and apply the changes.
        
    4. To verify the internet connectivity ping any website. Let’s say Google
        
        ![image.png](./data/image%2027.png)
        
    
4. Check the IP address of the server using nslookup.
    
    ![image.png](./data/image%201.png)
    
5. Setting up DHCP service on the server.
    1. On the “Server Manager” Dashboard, go to the DHCP option on the left side.
        
        ![image.png](./data/image%2028.png)
        
    2. Right Click on the server present in the “Servers” dialogue box and select “DHCP Manager”
        
        ![image.png](./data/image%2029.png)
        
    3. Click on the server present under the DHCP option. 
        1. Right click on IPv4 and select “New Scope” Option. The scope will define the range of IP addressed which will be used for DHCP.
            
            ![image.png](./data/image%2030.png)
            
        2. Select “Next”
            
            ![image.png](./data/image%2031.png)
            
        3. Enter the name as “project-x-scope” and click “Next”
            
            ![image.png](./data/image%2032.png)
            
        4. Enter the “Start IP address” as 10.0.0.100 and “End IP address” as 10.0.0.200. Enter the subnet mask as “255.255.255.0”. Then click “Next”
            
            ![image.png](./data/image%2033.png)
            
        5. Set Default Gateway’s “IP address” as 10.0.0.1, then click “Next”. (10.0.0.1 is the IP of the Router)
            
            ![image.png](./data/image%2034.png)
            
        6. Click “Finish”
        
    4. Now deploy the configuration.
        1. On the “Server Manager” Dashboard, go to the DHCP option on the left side. Select the “More” on the Right side.
            
            ![image.png](./data/image%2035.png)
            
        2. Click on “Complete DHCP configuration”
            
            ![image.png](./data/image%2036.png)
            
        3. Click “Next”
            
            ![image.png](./data/image%2037.png)
            
        4. Click “Commit”
            
            ![image.png](./data/image%2038.png)
            
        
    5. The DHCP server is not active
        
        ![image.png](./data/image%2039.png)
        
    
6. Create User accounts on the server.
    1. On the “Server Manager” Dashboard, Click on the “Tools” option on the top right side.
        
        ![image.png](./data/image%2040.png)
        
    2. Select “Active Directory Users and Computers”
        
        ![image.png](./data/image%2041.png)
        
    3. Go to “corp.project-x-dc.com” → ”Users”
        
        ![image.png](./data/image%2042.png)
        
    4. Right click on “Users”. Go to “New” → “User”
        
        ![image.png](./data/image%2043.png)
        
    5. Creating first user. The user is a standard business user (i.e. John Doe) .
        1. Enter the details and click “Next”
            
            ![image.png](./data/image%2044.png)
            
        2. Enter the password “@password123!”. Also select the “User cannot change password”.
            
            ![image.png](./data/image%2045.png)
            
        3. Click “Next”, then click “Finish”
        4. The user has been created.
            
            ![image.png](./data/image%2046.png)
            
        
    6. Creating second user i.e. Jane Doe
        1. Enter the details and click “Next”
            
            ![image.png](./data/image%2047.png)
            
        2. Enter the password “@password123!”. Also select the “User cannot change password”.
            
            ![image.png](./data/image%2045.png)
            
        3. Click “Next”, then click “Finish”
        4. The user has been created.
            
            ![image.png](./data/image%2048.png)
            
        
7. 

---

### Setting Up Windows Client [project-x-win-client]

1. Connecting Window’s client with the domain server
    1. Search and open “Change workgroup name”.
        
        ![image.png](./data/image%2049.png)
        
    2. Click on “Change”
        
        ![image.png](./data/image%2050.png)
        
    3. Enter the details and click “OK”
        
        ![image.png](./data/image%2051.png)
        
    4. Enter the username and password of “John Doe”.
        
        ![image.png](./data/image%2052.png)
        
    5. The machine will restart. Now sign in using the John Doe’s credentials.
        
        ![image.png](./data/image%2053.png)
        
    

---

### Setting Up Linux client [project-x-linux-client]

1. Connect to the Active Directory Server using Samba’s Winbind
    1. Open terminal and run command
        
        ```python
        sudo apt -y install winbind libpam-winbind libnss-winbind krb5-config samba-dsdb-modules samba-vfs-modules
        ```
        
        ![image.png](./data/image%2054.png)
        
    2. Enter the Kerberos version
        
        ![image.png](./data/image%2055.png)
        
    3. Rename the “smb.conf” file to “smb.conf.org”
        
        ![image.png](./data/image%2056.png)
        
    4. Open the “smb.conf” file in nano and add the following configuration
        
        ```python
        [global]
        	kerberos method = secrets and keytab
        	realm = CORP.PROJECT-X-DC.COM
        	workgroup = CORP
        	security = ads
        	template shell = /bin/bash
        	winbind enum groups = Yes
        	winbind enum users = Yes
        	winbind separator = +
        	idmap config * : rangesize = 1000000
        	idmap config * : range = 1000000-19999999
        	idmap config * : backend = autorid
        ```
        
        ![image.png](./data/image%2057.png)
        
    5. Open “/etc/nsswitch.conf” in nano and add “winbind” in both “passwd” and “group” section
        
        ![image.png](./data/image%2058.png)
        
    6. On Ubuntu, every user that has an interactive logon to the system needs a home directory. For domain users, we need to set this before a user is able to successfully logon and start working.
        
        ```python
        sudo pam-auth-update
        ```
        
        ![image.png](./data/image%2059.png)
        
        Scroll down up to the point where it states:” Create home directory on login“. Use the space bar to select, tab to “OK” and hit enter.
        
        ![image.png](./data/image%2060.png)
        
    7. Change DNS settings to refer to AD DNS server (i.e. 10.0.0.5).
        
        ```python
        sudo nano /etc/resolv.conf
        ```
        
        ![image.png](./data/image%2061.png)
        
    8. Join the domain with Administrator:
        
        ```python
        sudo net ads join -U Administrator
        ```
        
        ![image.png](./data/image%2062.png)
        
    9. Restart Winbind
        
        ```python
        systemctl restart winbind
        ```
        
    10. List all available users.
        
        ```python
        wbinfo -u
        ```
        
        ![image.png](./data/image%2063.png)
        
    11. Login as “CORP+janed”
        
        ```python
        sudo login
        ```
        
        ![image.png](./data/image%2064.png)
        
    12. Issue an id command to view status:
        
        ```python
        id
        ```
        
        ![image.png](./data/image%2065.png)
        
    

---

### Setting up Email Server [project-x-corp-svr]

1. Clone the “project-x-linux-client” VM and then we will make changes in it.
2. Change the hostname to “sec-box”
    
    ```python
    sudo hostnamectl set-hostname corp-svr
    ```
    
    ![image.png](./data/image%2066.png)
    
3. Changing the default account from “jane” to “project-x-admin”
    1. Create the user : sudo adduser project-x-admin
        
        ![image.png](./data/image%2067.png)
        
    2. Give sudo permission to the user: sudo usermod -aG sudo project-x-admin
        
        ![image.png](./data/image%2068.png)
        
    
4. Connect to AD DS
    1. Restart Winbind
        
        ```python
        systemctl restart winbind
        ```
        
        ![image.png](./data/image%2069.png)
        
    2. Join to the AD DS 
        
        ```python
        sudo net ads join -U Admininstrator
        ```
        
        ![image.png](./data/image%2070.png)
        
    3. List all available users.
        
        ```python
        wbinfo -u
        ```
        
        ![image.png](./data/image%2071.png)
        
    4. Login as “CORP+Administrator”
        
        ```python
        sudo login
        ```
        
        ![image.png](./data/image%2072.png)
        
    5. Issue an “id” command to view status:
        
        ![image.png](./data/image%2073.png)
        
    
5. Now install Docker on Ubuntu Desktop
    1. Go to the link : https://docs.docker.com/engine/install/ubuntu/
        
        ![image.png](./data/image%2074.png)
        
    2. Run the following command present on the docker website, to setup the Docker’s apt repository.
        
        ```python
        # Add Docker's official GPG key:
        sudo apt-get update
        sudo apt-get install ca-certificates curl
        sudo install -m 0755 -d /etc/apt/keyrings
        sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
        sudo chmod a+r /etc/apt/keyrings/docker.asc
        
        # Add the repository to Apt sources:
        echo \
          "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
          $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
          sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
        sudo apt-get update
        ```
        
        ![image.png](./data/image%2075.png)
        
    3. Run the following command present on the docker website, to install the Docker packages
        
        ```python
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
        ```
        
        ![image.png](./data/image%2076.png)
        
    4. Run the test container “hello-world” to check if docker is running smoothly.
        
        ```python
        sudo docker run hello-world
        ```
        
        ![image.png](./data/image%2077.png)
        
    

---

### Setting Up MailHog in Docker Container

1. Install Mailhog in a Docker Container
    1. Go to the “home” directory
        
        ```python
        cd /home
        ```
        
    2. Made a directory called “mailhog” and go in that directory
        
        ![image.png](./data/image%2078.png)
        
    3. Configuration file for “mailhog”
        1. create a file called “docker-compose.yml”
            
            ```bash
            sudo nano docker-compose.yml
            ```
            
            ![image.png](./data/image%2079.png)
            
        2. Paste this code in the yml document and save it
            
            ```
            version: "3"
            services:
              mailhog:
                image: mailhog/mailhog
                container_name: mailhog
                ports:
                  - "1025:1025"
                  - "8025:8025"
            ```
            
            ![image.png](./data/image%2080.png)
            
        
    4. Now compose the image and run it in the background.
        
        ```bash
        sudo docker compose up -d
        ```
        
        ![image.png](./data/image%2081.png)
        
    5. Open the URL to open mailhog dashboard : http://localhost:8025
        
        ![image.png](./data/image%2082.png)
        
    6. Test mailhog by sending a local test email
        1. Create a python file.
            
            ```bash
            sudo nano test_message.py
            ```
            
            ![image.png](./data/image%2083.png)
            
        2. Paste this code and save it.
            
            ```python
            import smtplib
            from email.message import EmailMessage
            
            msg = EmailMessage()
            msg.set_content("This is a test email from Ubuntu VM.")
            msg["Subject"] = "Hello World from MailHog!"
            msg["From"] = "corpserver@example.com"
            msg["To"] = "user@example.com"
            
            with smtplib.SMTP("localhost", 1025) as server:
                server.send_message(msg)
            ```
            
            ![image.png](./data/image%2084.png)
            
        3. Convert the python file into an executable file
            
            ```bash
            sudo chmod +x test_message.py
            ```
            
            ![image.png](./data/image%2085.png)
            
        4. Run the python script
            
            ```bash
            sudo python3 test_message.py
            ```
            
            ![image.png](./data/image%2086.png)
            
        5. View the email in the mailhog inbox
            
            ![image.png](./data/image%2087.png)
            
            ![image.png](./data/image%2088.png)
            
        

---

### Setting up Email Poller in [project-x-linux-client]

This will allow us to get new email message notifications inside the `[project-x-linux-client]` host. 

1. Download a few dependencies.
    
    ```bash
    sudo apt install curl jq
    ```
    
    ![image.png](./data/image%2089.png)
    
2. Go to home directory 
    
    ```bash
    cd /home
    ```
    
    ![image.png](./data/image%2090.png)
    
3. Create a new bash script 
    
    ```bash
    sudo nano email_poller.sh
    ```
    
    ![image.png](./data/image%2091.png)
    
4. Paste the the following code. (This code was made using ChatGPT)
    
    ```bash
    #!/bin/bash
    
    MAILHOG_IP="10.0.0.8"  
    TO_EMAIL="janed"
    POLL_INTERVAL=30  # seconds
    
    echo "📡 Janed's Mail Watcher started... polling every $POLL_INTERVAL seconds"
    echo "🔎 Watching for new mail sent to: $TO_EMAIL@"
    
    # Keep track of seen message IDs
    SEEN_IDS_FILE="/tmp/mailhog_seen_ids_janed.txt"
    touch "$SEEN_IDS_FILE"
    
    while true; do
      # Fetch current message list
      curl -s http://$MAILHOG_IP:8025/api/v2/messages | jq -c '.items[]' | while read -r msg; do
        TO=$(echo "$msg" | jq -r '.To[].Mailbox')
        ID=$(echo "$msg" | jq -r '.ID')
    
        if [[ "$TO" == "$TO_EMAIL" && ! $(grep -Fx "$ID" "$SEEN_IDS_FILE") ]]; then
          SUBJECT=$(echo "$msg" | jq -r '.Content.Headers.Subject[0]')
          BODY=$(echo "$msg" | jq -r '.Content.Body')
    
          echo -e "\n📬 New Email Received!"
          echo "Subject: $SUBJECT"
          echo "From: $(echo "$msg" | jq -r '.Content.Headers.From[0]')"
          echo "Date: $(echo "$msg" | jq -r '.Created')"
          echo -e "Message:\n$BODY"
          echo "-----------------------------------"
    
          echo "$ID" >> "$SEEN_IDS_FILE"
        fi
      done
    
      sleep "$POLL_INTERVAL"
    done
    ```
    
    ![Capture.PNG](Capture.png)
    
5. Convert the script into an executable
    
    ```bash
    chmod +x email_poller.sh
    ```
    
    ![image.png](./data/image%2092.png)
    
6. Run the Script in the background.
    
    ```bash
    sudo ./email_poller.sh &
    ```
    
    ![image.png](./data/image%2093.png)
    
7. Stop the script if needed
    
    ```bash
    pkill -f email_poller
    ```
    

---

### Setting Up Security Server [project-x-sec-box]

1. Clone the “project-x-linux-client” VM and then we will make changes in it.
2. Change the hostname to “sec-box”
    
    ```python
    sudo nano /etc/hostname
    ```
    
    ![image.png](./data/image%2094.png)
    
3. Reboot the VM
4. Changing the default account from “jane” to “sec-user”
    1. Create the user : sudo adduser sec-user
        
        ![image.png](./data/image%2095.png)
        
    2. Give sudo permission to the user: sudo usermod -aG sudo sec-user
        
        ![image.png](./data/image%2096.png)
        
    
5. Connect to AD DS
    1. Restart Winbind
        
        ```python
        systemctl restart winbind
        ```
        
        ![image.png](./data/image%2097.png)
        
    2. Join to the AD DS 
        
        ```python
        sudo net ads join -U Admininstrator
        ```
        
        ![image.png](./data/image%2098.png)
        
    3. List all available users.
        
        ```python
        wbinfo -u
        ```
        
        ![image.png](./data/image%2099.png)
        
    4. Login as “CORP+secuser”
        
        ```python
        sudo login
        ```
        
        ![image.png](./data/image%20100.png)
        
    5. Issue an “id” command to view status:
        
        ![image.png](./data/image%20101.png)
        

---

### Setting Up Wazuh Server in [project-x-sec-box]

1. Run the curl command
    
    ```python
    curl -sO https://packages.wazuh.com/4.9/wazuh-install.sh && sudo bash ./wazuh-install.sh -a -i
    ```
    
    ![image.png](./data/image%20102.png)
    
2. Copy the “Admin” password and save it
    
    ![image.png](./data/image%20103.png)
    
3. Login into the Wazuh dashboard by entering the [https://localhost](https://localhost/) in a new browser tab.
Click “Advanced…”  Accept the Risk and Continue.
    
    ![image.png](./data/image%20104.png)
    
4. Use the credentials generated to log in. 
    
    ![image.png](./data/image%20105.png)
    
5. 

---

### Setting up Wazuh Agents in VMs

1. Setting Up the agent in Windows client [project-x-win-client]
    1. Go to “Server Management” ➔ “Endpoint Summary”.
        
        ![](https://docs.projectsecurity.io/assets/images/e101/p13/18.png)
        
    2. Choose “Deploy new agent”.
        
        ![image.png](./data/image%20106.png)
        
    3. Select Windows MSI.
        
        ![image.png](./data/image%20107.png)
        
    4. Server Address: `10.0.0.10`.
        
        ![Capture.PNG](Capture%201.png)
        
    5. Assign an agent name: `project-x-win-client`.
        
        ![image.png](./data/image%20108.png)
        
    6. Groups: `default`
        
        ![image.png](./data/image%20109.png)
        
    7. Copy the command in step 4.
        
        ![image.png](./data/image%20110.png)
        
        ```powershell
        Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.9.2-1.msi -OutFile $env: tmp\wazuh-agent; msiexec.exe /1 $env: tmp\wazuh-agent/q WAZUH_MANAGER='10.0.0.18'
        WAZUH_AGENT_GROUP="default' WAZUH_AGENT_NAME='project-x-win-client'
        ```
        
    8. Go to the `[project-x-win-client]` Virtual Machine
    
    9. Login under the “John Doe” account.
        
        
    10. Open new PowerShell Session ➔ Right-click “Run as Administrator”.
        
        
    11. Paste the copied command
        
        ```powershell
        Invoke-WebRequest -Uri
        https://packages.wazuh.com/4.x/windows/wazuh-agent-4.9.2-1.msi -
        OutFile $env:tmp\wazuh-agent; msiexec.exe /i $env:tmp\wazuh-agent
        /q WAZUH_MANAGER='10.0.0.10' WAZUH_AGENT_GROUP='default'
        WAZUH_AGENT_NAME='project-x-win-client'
        ```
        
        ![image.png](./data/image%20111.png)
        
    12. Start the Wazuh Agent:
        
        ```powershell
        NET START WAZUH
        ```
        
        ![image.png](./data/image%20112.png)
        
    13. View the Agent display on the “Endpoints” dashboard in Wazuh
        
        ![image.png](./data/image%20113.png)
        
2. Setting Up the agent in Linux Client [project-linux-client]
    1. Go to “Server Management” ➔ “Endpoint Summary”.
        
        ![](https://docs.projectsecurity.io/assets/images/e101/p13/18.png)
        
    2. Choose “Deploy new agent”.
        
        ![image.png](./data/image%20114.png)
        
    3. Select Linux→ DEB amd64.
        
        ![image.png](./data/image%20115.png)
        
    4. Server Address: `10.0.0.10`.
        
        ![Capture.PNG](Capture%201.png)
        
    5. Assign an agent name: `project-x-linux-client`.
        
        ![image.png](./data/image%20116.png)
        
    6. Groups: `default`
        
        ![image.png](./data/image%20109.png)
        
    7. Copy the command in step 4.
        
        ![image.png](./data/image%20117.png)
        
        ```powershell
        Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent_4.9.2-1_amd64.deb 
        && sudo WAZUH_MANAGER='10.0.0.10' WAZUH_AGENT_NAME='project-x-linux-client' dpkg -i 
        ./Wazuh-agent_4.9.2-1_amd63.deb
        ```
        
    8. Go to the `[project-x-win-client]` Virtual Machine
    
    9. Login under the “John Doe” account.
        
        
    10. Open new PowerShell Session ➔ Right-click “Run as Administrator”.
        
        
    11. Paste the copied command
        
        ```powershell
        Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent_4.9.2-1_amd64.deb 
        && sudo WAZUH_MANAGER='10.0.0.10' WAZUH_AGENT_NAME='project-x-linux-client' dpkg -i 
        ./Wazuh-agent_4.9.2-1_amd63.deb
        ```
        
        ![image.png](./data/image%20118.png)
        
    12. Start the Wazuh Agent by running the following commands:
        1. sudo systemctl daemon-reload
        2. sudo systemctl enable wazuh-agent
        3. sudo systemctl start wazuh-agent
        
        ![image.png](./data/image%20119.png)
        
    13. View the Agent display on the “Endpoints” dashboard in Wazuh
        
        ![image.png](./data/image%20120.png)
        
    
3. Setting Up the agent in AD DC server [project-x-dc]
    1. Go to “Server Management” ➔ “Endpoint Summary”.
        
        ![](https://docs.projectsecurity.io/assets/images/e101/p13/18.png)
        
    2. Choose “Deploy new agent”.
        
        ![image.png](./data/image%20114.png)
        
    3. Select Windows MSI.
        
        ![image.png](./data/image%20115.png)
        
    4. Server Address: `10.0.0.10`.
        
        ![Capture.PNG](Capture%201.png)
        
    5. Assign an agent name: `project-x-dc`.
        
        ![image.png](./data/image%20121.png)
        
    6. Groups: `default`
        
        ![image.png](./data/image%20109.png)
        
    7. Copy the command in step 4.
        
        ![image.png](./data/image%20122.png)
        
        ```powershell
        Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.9.2-1.msi -OutFile $env: tmp\wazuh-agent; msiexec.exe /1 $env: tmp\wazuh-agent/q WAZUH_MANAGER='10.0.0.10'
        WAZUH_AGENT_GROUP="default' WAZUH_AGENT_NAME='project-x-win-client'
        ```
        
    8. Go to the `[project-x-dc]` Virtual Machine
    
    9. Login under the “Administrator” account.
        
        
    10. Open new PowerShell Session ➔ Right-click “Run as Administrator”.
        
        
    11. Paste the copied command
        
        ```powershell
        Invoke-WebRequest -Uri
        https://packages.wazuh.com/4.x/windows/wazuh-agent-4.9.2-1.msi -
        OutFile $env:tmp\wazuh-agent; msiexec.exe /i $env:tmp\wazuh-agent
        /q WAZUH_MANAGER='10.0.0.10' WAZUH_AGENT_GROUP='default'
        WAZUH_AGENT_NAME='project-x-dc'
        ```
        
        ![image.png](./data/image%20123.png)
        
    12. Start the Wazuh Agent:
        
        ```powershell
        NET START WazuhSvc
        ```
        
        ![image.png](./data/image%20124.png)
        
    13. View the Agent display on the “Endpoints” dashboard in Wazuh
        
        ![image.png](./data/image%20125.png)
        
    
4. Now create two endpoint groups named “windows” and  “linux” and add the “project-x-linux-client” to the “linux” group and “project-x-win-client” and “project-x-dc” agents to “windows” group
    
    ![image.png](./data/image%20126.png)
    
5. Configure for “linux” group. This is used to onboard specific logs native to the operating system.
    1. Go to Server Management → Endpoint groups
        
        ![image.png](./data/image%20127.png)
        
    2. Select the ✏️ icon in the “linux” group
        
        ![image.png](./data/image%20128.png)
        
    3. Add the following to the empty ”agent.conf”
        
        ```python
        <agent_config>
        	 <localfile>
        		 <log_format>syslog</log_format>
        		 <location>/var/log/auth.log</location>
        	 </localfile>
        	 <localfile>
        		 <log_format>syslog</log_format>
        		 <location>/var/log/secure</location>
        	 </localfile>
        	 <localfile>
        		 <log_format>audit</log_format>
        		 <location>/var/log/audit/audit.log</location>
        	 </localfile>
        </agent_config>
        ```
        
        ![image.png](./data/image%20129.png)
        
    4. Save it.
    
6. Similarly configure for “windows” group. This is used to onboard specific logs native to the operating system. Example Windows Event Application , Security and System logs will be used to detect host-based activity.
    1. Go to Server Management → Endpoint groups
        
        ![image.png](./data/image%20127.png)
        
    2. Select the ✏️ icon in the “windows” group
        
        ![image.png](./data/image%20128.png)
        
    3. Add the following to the empty ”agent.conf”
        
        ```python
        <agent_config>
        	 <!-- Shared agent configuration here -->
        	 <localfile>
        		 <location>Security</location>
        		 <log_format>eventchannel</log_format>
        	 </localfile>
        	 <localfile>
        		 <location>Application</location>
        		 <log_format>eventchannel</log_format>
        	 </localfile>
        </agent_config>
        ```
        
        ![image.png](./data/image%20130.png)
        
    4. Save it.
    
7. 
    
    

---