<h1>Credential Harvesting</h1>


<br />
<h2>Utilities Used</h2>

- <b>Windows 10 Operating System</b>
- <b>Kali Linux</b>
- <b>Browser (e.g., Google Chrome and Firefox)</b>

<h2>Environments Used</h2>

- <b>VirtualBox Hypervisor </b>

<h2>Lab Walk-through:</h2>
<p>This demonstration will hit two birds with one stone. We’ll set up a phishing campaign with the <a href="https://docs.getgophish.com/user-guide/what-is-gophish" target="_blank">Gophish</a> application where we’ll identify a victim user group, fabricate phishing emails, and launch a campaign that is configured all in one platform. Another element to this social engineering attack will be the credential harvesting tool that will clone a popular website and will act as the payload in our phishing campaign. </p>
<br />
<h3>Initialize Phishing Campaign</h3>
It's best to do this lab in an isolated environment. I have my Windows 10 VM and Kali Linux VM powered on. Both machines are in the same subnet, which is essential for this demonstration to execute properly. Let’s pull up to the Windows 10 VM. Make sure your Windows Firewall is turned off so there’s no interference for the social engineering attack.
<br/>
<img src="https://i.imgur.com/fQV0cA1.png" height="80%" width="80%" alt="Windows Firewall Turned Off"/>
<br />
Next, we'll boot up our hMailServer that was created in another <a href="https://github.com/JE99s/Create_Your_Local_EmailServer" target="_blank">demonstration</a>.
<br/>
<img src="https://i.imgur.com/lE1mdzi.png" height="60%" width="60%" alt="Please enter hMailServer passwd"/>
<br />
Next, we’ll start up our Gophish Server.
<br/>
<img src="https://i.imgur.com/s44TwHe.png" height="60%" width="60%" alt="Mouse on gophish.exe"/>
<br />
The configured Gophish executable is locally assigned. The admin dashboard is where we will be doing our work. So, on any browser. We’ll type the following URL to navigate to the Gophish admin login page.
<br/>
<img src="https://i.imgur.com/OlpWN4G.png" height="60%" width="60%" alt="URL to Gophish admin server"/>
<br />
At the login page, we’ll submit our credentials to log in to the admin dashboard.
<br/>
<img src="https://i.imgur.com/ohFw8Hr.png" height="55%" width="55%" alt="Gophish Admin sign-in page"/>
<br />

<h3>Users & Groups</h3>
On the left-side panel of the admin dashboard, we'll click the <b>Users & Groups</b> tab to establish our victim(s) for the phishing campaign. This is where we'll assign our targets for the phishing campaign to a group that could contain more than one email address, so a phishing campaign can be sent in mass. So, we'll click <b>New Group</b> to fill in the following fields:
<br/>
<img src="https://i.imgur.com/d2uXBjp.png" height="80%" width="80%" alt="New Group Fields"/>
<br />
We'll choose anything for the group name, and here we'll add some recipients. These valid email addresses created locally with help from our <a href="https://github.com/JE99s/Create_Your_Local_EmailServer" target="_blank">hMailServer</a>. Once all recipients are added, click <b>Save Changes</b>.
<br/>
<img src="https://i.imgur.com/6iAX7e2.png" height="80%" width="80%" alt="Save Changes to Group"/>
<br />

<h3>Sending Profiles</h3>
To send emails, Gophish requires us to configure some SMTP relay details called "Sending Profiles". On the left-hand sidebar of the dashboard, click <b>Sending Profiles</b>. During this configuration, it's important that the "SMTP From" address is a valid email address. We'll fill in the following fields as such and save our profile.
<br/>
<img src="https://i.imgur.com/zwMyhNU.png" height="65%" width="65%" alt="Sending Profile"/>
<br />
Ok, so we now have our Gophish server up and running. We’ve made a group of target recipients and we’ve established a Sending Profile that will launch the phishing campaign. Before we proceed, let’s go to our Kali Linux VM to setup the Credential Harvester tool. 
<br/>

<h3>Utilize SET Toolkit to Create Malicious Link</h3>
Starting on our Kali Linux VM, let’s ensure connectivity with the Windows 10VM. 
<br/>
<img src="https://i.imgur.com/5tGoJx5.png" height="75%" width="75%" alt="Kali ping to Windows 10"/>
<br />
<img src="https://i.imgur.com/Yh8LgQW.png" height="75%" width="75%" alt="Windows 10 ping to Kali"/>
<br />
It looks like there is connectivity between the two machines. Now, the credential harvester one of many available tools included in the massive framework called the Social Engineering Toolkit (a.k.a. SET). To start up the SET, we need super user rights to execute its boot command, that is what ‘sudo’ is for. Execute the following command, then press <b>Enter</b>.
<br />
<img src="https://i.imgur.com/0TxS0o3.png" height="75%" width="75%" alt="sudo setoolkit"/>
<br />
For your first time, you might be met with somewhat of a terms of service (TOS) to agree that this tool will not be used for any malicious or unethical reasons. You’re not going to go out in the real-world and utilize this to attempt to steal someone’s credentials. This is all designed for demonstrative purposes only. Agree and hit <b>Enter</b> and you should be met with the following menu:
<br />
<img src="https://i.imgur.com/v6VNBVZ.png" height="75%" width="75%" alt="SET MENU Welcome-page"/>
Now, we are going to be running a social engineering attack, so the first thing we are going to select is option <b>1</b> for <b>Social-Engineering Attacks</b>. Hit <b>Enter</b>.
<br />
<br />
<img src="https://i.imgur.com/v6VNBVZ.png" height="75%" width="75%" alt="SET MENU Welcome-page"/>
<br />
