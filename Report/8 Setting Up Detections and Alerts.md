# 8. Setting Up Detections and Alerts

---

### [project-x-linux-client]

Wazuh has a built-in rule detection to detect authentication failures from the sshd daemon.

- Wazuh Rule ID: `5760`.
- Description: `sshd: authentication failed`.

Navigate to “Server management” ➔ “Rules”. And look up “5760” to view more detail about this rule.

![](https://docs.projectsecurity.io/assets/images/e101/p9/10.png)

![](https://docs.projectsecurity.io/assets/images/e101/p9/11.png)

Here is a sample snapshot of a log generated when the SSH attempt fails.

Go to “Explore” ➔ “Discover” tab. Look up “sshd”.

- 💡 Need a failed login attempt.

![](https://docs.projectsecurity.io/assets/images/e101/p9/12.png)

Create an alert for Failed SSH attempts. To do this, a Monitor will be set up to analyze logs. Based on certain conditions defined, a Trigger can be setup to open an Alert.

Go to “Explore” ➔ “Alerting”.

![](https://docs.projectsecurity.io/assets/images/e101/p9/13.png)

Select the “Monitors” tab on the top left.

![](https://docs.projectsecurity.io/assets/images/e101/p9/14.png)

Select “Create monitor”.

![](https://docs.projectsecurity.io/assets/images/e101/p9/15.png)

Here, create a new monitor.

Title the Monitor “3 Failed SSH Attempts”. Leave everything else default.

![](https://docs.projectsecurity.io/assets/images/e101/p9/16.png)

Scroll down to “Data source”. Add the following for the Index, hit the Enter key after typing: `wazuh-alerts-4.x-*`

For “Time Field” select: `@timestamp`

![](https://docs.projectsecurity.io/assets/images/e101/p9/17.png)

Next, add a query to select what logs and log fields user would like to monitor.

Based on a sample log of a failed ssh attempt, user can construct a query to monitor specific field or value key pairs.

![](https://docs.projectsecurity.io/assets/images/e101/p9/18.png)

Navigate to the “Data filter” ➔ “+ Add filter”

![](https://docs.projectsecurity.io/assets/images/e101/p9/19.png)

Based on the above sample log, let’s craft a query to select based on the “sshd” process name and the “authentication_failed” rule group.

![](https://docs.projectsecurity.io/assets/images/e101/p9/20.png)

![](https://docs.projectsecurity.io/assets/images/e101/p9/21.png)

“Data filter” tab should now look something like this.

![](https://docs.projectsecurity.io/assets/images/e101/p9/22.png)

Let’s add a Trigger.

![](https://docs.projectsecurity.io/assets/images/e101/p9/23.png)

Add the following conditions to the Trigger. User set the “Severity level” to 3 (Medium) and the “Trigger condition” above 2.

So what user is doing here… Once user gets more than 2 logs that have met the following query conditions from above, an alert will be generated.

![](https://docs.projectsecurity.io/assets/images/e101/p9/24.png)

There’s also an “Actions” option. Here user could create an Email, Slack, or Microsoft Teams notification of the alert. User could also launch a playbook that would follow a specific instruction set to analyze, investigate, or isolate a host. User is not going to configure this section.

![](https://docs.projectsecurity.io/assets/images/e101/p9/25.jpg)

Scroll to the bottom and Select “Create”.

![](https://docs.projectsecurity.io/assets/images/e101/p9/26.png)

---

### [project-x-win-client]

An Event ID does not exist for Enabling Win-RM as a service. However, we can detect WinRM logins through the Event ID `4624` with a `logonProcessName` of Kerberos as WinRM uses Kerberos.

Once we have enabled Security Windows logs (this should have been done in the Setup Wazuh section), we should automatically get Windows Event Logs.

Wazuh has a built-in rule detection to detect successful and unsuccessful authentication attempts into a Windows machine. The Windows Security Event IDs are `4624` (for successful) and `4625` (for failed).

- Wazuh Rule ID: `60106`
- Description: User: `Windows Logon Success`

Navigate to “Server management” ➔ “Rules”. And look up “60106” to view more detail about this rule.

Go to “Explore” ➔ “Discover” tab ➔ Make sure `wazuh-alerts-*` is selected. Look up: `data.win.eventdata.logonProcessName: Kerberos`

![](https://docs.projectsecurity.io/assets/images/e101/p9/32.png)

Here we can see the `logonProcessName`, the computer that was logged into, the EventID and the system message from a successful WinRM logon.

![](https://docs.projectsecurity.io/assets/images/e101/p9/33.png)

Let’s create an alert for WinRM. We will do something similar to the Failed SSH attempts.

Go to “Explore” ➔ “Alerting”.

![](https://docs.projectsecurity.io/assets/images/e101/p9/13.png)

Select the “Monitors” tab on the top left.

![](https://docs.projectsecurity.io/assets/images/e101/p9/14.png)

Select “Create monitor”

![](https://docs.projectsecurity.io/assets/images/e101/p9/15.png)

Title the Monitor “WinRM Logon”. Leave everything else default.

![](https://docs.projectsecurity.io/assets/images/e101/p9/34.png)

Scroll down to “Data source”. Add the following for the Index, hit the Enter key after typing: `wazuh-alerts-4.x-*`

For “Time Field” select: `@timestamp`

![](https://docs.projectsecurity.io/assets/images/e101/p9/17.png)

Next, add a query to select what logs and log fields we would like to monitor.

Based on a sample log of a WinRM attempt, we can construct a query to monitor specific field or value key pairs.

![](https://docs.projectsecurity.io/assets/images/e101/p9/33.png)

Navigate to the “Data filter” ➔ “+ Add filter”.

![](https://docs.projectsecurity.io/assets/images/e101/p9/19.png)

Based on the above sample log, let’s craft a query to select based on the “logonProcessName” and the “eventID” fields.

![](https://docs.projectsecurity.io/assets/images/e101/p9/35.png)

![image.png](image%20132.png)

“Data filter” tab should now look something like this.

![](https://docs.projectsecurity.io/assets/images/e101/p9/37.png)

add a Trigger.

![](https://docs.projectsecurity.io/assets/images/e101/p9/23.png)

Add the following conditions to the Trigger. Set the “Severity level” to 3 (Medium) and the “Trigger condition” above 1.

![](https://docs.projectsecurity.io/assets/images/e101/p9/38.png)

Scroll to the bottom and Select “Create”.

![](https://docs.projectsecurity.io/assets/images/e101/p9/26.png)

---