<h1>Active Directory Disaster Recovery System</h1>

<h2>🧠 Project Summary</h2>
<p>This project is a practical walkthrough/tutorial for creating a disaster recovery system for Microsoft Active Directory (AD), utilizing <strong>PowerShell scripts</strong> and <strong>Windows Server environments</strong>. It aims to simulate real-world recovery processes and demonstrate essential backup and restore procedures.</p>

<p><b>Languages Used:</b> PowerShell</p>
<p><b>Environments Used:</b> Windows Server 2019/2022 (Domain Controller), Azure (for hosting VMs)</p>
<p><b>Technologies/Services Used:</b> Active Directory Domain Services (AD DS), Windows Server Backup, PowerShell</p>

<h2>🖼️ Media</h2>
<ul>
  <li><img src="images/01_domain_setup.png" alt="Initial Domain Setup" width="600"></li>
  <li><img src="images/02_backup_schedule.png" alt="Scheduled Backup using Windows Server Backup" width="600"></li>
  <li><img src="images/03_restore_mode.png" alt="Booting into DSRM" width="600"></li>
  <li><img src="images/04_restore_progress.png" alt="Directory Services Restore in Progress" width="600"></li>
</ul>

<h2>🛠️ Demonstration</h2>
<ol>
  <li><strong>Set up the AD Domain Controller:</strong>
    <ul>
      <li>Deploy a VM in Azure or locally using Windows Server 2019/2022.</li>
      <li>Install AD DS and promote the server to a domain controller.</li>
    </ul>
  </li>
  <li><strong>Configure Backups:</strong>
    <ul>
      <li>Install Windows Server Backup:</li>
      <pre><code>Install-WindowsFeature Windows-Server-Backup</code></pre>
      <li>Schedule automatic system state backups:</li>
      <pre><code>wbadmin enable backup -addtarget:E: -schedule:12:00 -include:SystemState -quiet</code></pre>
    </ul>
  </li>
  <li><strong>Simulate Disaster:</strong>
    <ul>
      <li>Intentionally break AD by deleting objects or corrupting the database (for learning purposes).</li>
    </ul>
  </li>
  <li><strong>Recovery Process:</strong>
    <ul>
      <li>Reboot the server into Directory Services Restore Mode (DSRM).</li>
      <li>Log in with the DSRM password set during domain promotion.</li>
      <li>Use PowerShell to restore the system state:</li>
      <pre><code>wbadmin start systemstaterecovery -version:MM/DD/YYYY-HH:MM</code></pre>
    </ul>
  </li>
  <li><strong>Verification:</strong>
    <ul>
      <li>Reboot and verify Active Directory functionality using <code>Get-ADUser</code>, <code>Get-ADDomain</code>, etc.</li>
    </ul>
  </li>
</ol>

<h2>🔗 Repository</h2>
<p>All scripts and step-by-step instructions are available in this GitHub repository: <a href="https://github.com/OmarITx/ad-disaster-recovery" target="_blank">https://github.com/OmarITx/ad-disaster-recovery</a></p>

<h2>📬 Connect with Me</h2>
<p>
  <a href="https://www.linkedin.com/in/omar-kassem-41baa4355/">
    <img align="left" alt="Omar | LinkedIn" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" />
  </a>
  <a href="https://www.instagram.com/omar_kassem32/">
    <img align="left" alt="Omar | Instagram" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/instagram.svg" />
  </a>
</p>
<br>
<p><i>Feedback, stars, and memes are always welcome! 😄</i></p>
