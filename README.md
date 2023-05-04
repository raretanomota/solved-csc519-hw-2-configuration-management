Download Link: https://assignmentchef.com/product/solved-csc519-hw-2-configuration-management
<br>
In this homework assignment, you will master these skills by completing the following tasks:

<strong>Using ansible</strong>, be able to automatically configure a server running mattermost.

Perform the following tasks listed in the <u><a href="https://docs.mattermost.com/install/install-ubuntu-1804.html">installation guide</a></u> for mattermost.

<ul>

 <li>Installing Ubuntu Server 18.04 LTS (This should be mostly done, you already have image! But can still run update/upgrade).</li>

 <li>Installing MySQL Database Server (5.7.x is recommended)</li>

 <li>Installing Mattermost Server</li>

</ul>

Your goal is to translate those instructions into ansible playbooks and roles.

<h2>Demonstrating mattermost server</h2>

<ul>

 <li>Finalize configuring the mattermost server by browsing <u><a href="http://192.168.33.80:8065/">http://192.168.33.80:8065</a></u><a href="http://192.168.33.80:8065/">.</a></li>

 <li>Create a team and users.</li>

 <li>Demonstrate you can actually use mattermost by posting some messages.</li>

</ul>

<h2>Constraints</h2>

Follow the following constraints when creating your server:

<ul>

 <li>Use best practices (use modules to do work, avoid shell/commands, be idempotent, use your own roles when sensible, manage secrets)  Everything is setup automatically. No manual steps.</li>

 <li><strong>Limited use ansible galaxy roles</strong>: You are limited to using galaxy roles for setting up mysql. Note you will need to update your ansible server setup script to install galaxy roles on your ansible-srv.</li>

</ul>

<h1>Extra Requirements</h1>

You can also extend your implementation to meet the following extra requirements for more credit:

<ul>

 <li>Automate the creation of teams and other mattermost server configuration using the <u><a href="https://docs.mattermost.com/administration/command-line-tools.html">mattermost CLI</a></u> (5 points)</li>

 <li>Configure the ability to send email notifications (5 points).</li>

 <li>Complete the section “Configuring NGINX as a proxy for Mattermost Server” in mattermost instalation instructions (10 points).</li>

 <li>Complete the section “Configuring NGINX with SSL and HTTP/2”. Note you can setup a local hosts file for enabling temporary testing of your ssl configuration. (5 points)</li>

</ul>

Reminder that limited technical assistance will be provided by teaching staff when attempting the extra requirements. Make sure you have completed all the basic requirements before attempting any extra requirements.

<h1>Screencast</h1>

Create a screencast of your assignment:

 Demonstrate running your code to setup your environment and running your customization and post-configuration steps (cm setup), and running your mattermost playbook (cm playbook cm/mattermost.yml cm/inventory.ini). Demonstrate your mattermost server running on your browser. Demonstrate any extra requirements fulfilled. Note some extra requirements supercede the basic requirements.

For guidelines, software, and recommendations see <u><a href="https://github.com/CSC-DevOps/Course/blob/master/HW/Screencasts.md">Screencasts</a></u><a href="https://github.com/CSC-DevOps/Course/blob/master/HW/Screencasts.md">.</a>

<h1>Progress</h1>

You can check your progress by running:

opunit verify -i test/inventory.yml

You will want to be able to pass these basic checks:

Checks




Basic checks for ansible server




version check

<ul>

 <li>ansible –version: 2.9.4 &gt; ^2.9.x =&gt; true       reachable check</li>

 <li>[/bakerx] status: true</li>

</ul>

<table width="0">

 <tbody>

  <tr>

   <td width="628">&#x2714;         [/bakerx/cm/inventory.ini] status: truecontains checkChecking if you have MSDOS style newlines in your bash scripts. Fix with dos2unix&#x2714;         […run-ansible.sh] does not contain [r] status: true message: NA  contains check&#x2714;         […server-init.sh] does not contain [r] status: true message: NAChecks Basic checks for dependencies version check&#x2716;   mysql –version: bash: mysql: command not found &gt; ^5.7.x =&gt; false          availability check&#x2716;   [vagrant] http://192.168.33.80:8065/ expected: 200 actual:ECONNREFUSEDreachable check&#x2716;   [/opt/mattermost/data] status: false&#x2716;   [/lib/systemd/system/mattermost.service] status: false  service check&#x2716;   [mattermost] expected: active actual: null    contains check&#x2716;   […config.json]  contains [“DriverName” : “mysql”] status: false message: Error: file doesn’t exist Summary 0.0% of all checks passed.         0 passed · 6 failed</td>

  </tr>

 </tbody>

</table>