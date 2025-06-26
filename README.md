<h1>🛡️ Active Directory Deployment & Management</h1>

<h2>🧠 Project Summary</h2>
<p>This tutorial demonstrates the setup and management of Microsoft Active Directory (AD) using <strong>Azure-hosted Windows Server VMs</strong> and <strong>PowerShell ISE</strong>. It walks through real-world scenarios for deploying AD, creating users via scripting, and managing Group Policies (GPOs).</p>

<p><b>Languages Used:</b> PowerShell</p>
<p><b>Environments:</b> Azure (VMs), Windows Server 2019/2022</p>
<p><b>Services:</b> Active Directory Domain Services, PowerShell ISE, Group Policy Management</p>

<h2>🖼️ Media</h2>
<ul>
  <li><img src="images/domain_setup.png" alt="Active Directory Setup" width="600"></li>
  <li><img src="images/user_creation.png" alt="User Creation with PowerShell ISE" width="600"></li>
  <li><img src="images/group_policy.png" alt="Group Policy Management" width="600"></li>
</ul>

<h2>💡 Active Directory System Setup</h2>

<h3>1️⃣ Installing & Configuring Active Directory</h3>
<ol>
  <li>Create a Windows Server VM on Azure.</li>
  <li>Set a static IP address and rename the server.</li>
  <li>Install AD DS:
    <pre><code>Install-WindowsFeature -Name AD-Domain-Services</code></pre>
  </li>
  <li>Promote server to Domain Controller:
    <pre><code>Install-ADDSForest -DomainName "yourdomain.local"</code></pre>
  </li>
</ol>

<h3>2️⃣ Creating Users with PowerShell ISE</h3>
<ol>
  <li>Launch PowerShell ISE as Administrator.</li>
  <li>Use the following script to create users:
    <pre><code>
Import-Module ActiveDirectory

New-ADUser -Name "John Doe" -GivenName "John" -Surname "Doe" `
-SamAccountName "jdoe" -UserPrincipalName "jdoe@yourdomain.local" `
-AccountPassword (ConvertTo-SecureString "P@ssword123" -AsPlainText -Force) `
-Enabled $true -Path "OU=Users,DC=yourdomain,DC=local"
    </code></pre>
  </li>
</ol>

<h3>3️⃣ Managing Group Policies</h3>
<ol>
  <li>Install Group Policy Management Console (GPMC):  
    <pre><code>Install-WindowsFeature -Name GPMC</code></pre></li>
  <li>Create and link a GPO:
    <pre><code>
New-GPO -Name "Disable USB Access"
New-GPLink -Name "Disable USB Access" -Target "OU=Users,DC=yourdomain,DC=local"
    </code></pre>
  </li>
  <li>Edit GPO via GPMC or PowerShell to configure settings like USB restriction, software installs, etc.</li>
</ol>

<h2>📂 Repository</h2>
<p>All code and documentation available here: 
  <a href="https://github.com/OmarITx/ad-disaster-recovery" target="_blank">
    https://github.com/OmarITx/ad-disaster-recovery
  </a>
</p>

<h2>📬 Connect with Me</h2>
<p>
  <a href="https://www.linkedin.com/in/omar-kassem-41baa4355/">
    <img alt="Omar | LinkedIn" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" />
  </a>
  <a href="https://www.instagram.com/omar_kassem32/">
    <img alt="Omar | Instagram" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/instagram.svg" />
  </a>
</p>
<br>
<p><i>Feedback and stars are always appreciated! ⭐</i></p>
