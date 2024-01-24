# Cybersecurity

### Basic of Linux

- whoami : Provide the username of system
- other general use commands are : ls , cd , pwd , cd .. .
- ls : list directories.
- cd : change directory

Everything in linux is file even the command are the files even the command are the compiled files

bin contain binary files

- cat : concatenate, can use to view the contents inside the file
- cp : copy --syntax : cp nameOfFile newName
- rm : remove
- sbin contain top secret command
- sudo addUser newUser --> this will add new user
- To view root folder you need special permissions ,only super user have access to access this file

Linux file system has a hierarchal file structure as it contains a root directory and its subdirectories. All other directories can be accessed from the root directory. A partition usually has only one file system, but it may have more than one file system.

- / (root filesystem): It is the top-level filesystem directory. It must include every file needed to boot the Linux system before another filesystem is mounted. Every other filesystem is mounted on a well-defined and standard mount point because of the root filesystem directories after the system is started.

- /boot: It includes the static kernel and bootLoader configuration and executable files needed to start a Linux computer.

- /bin: This directory includes user executable files.
- /dev: It includes the device file for all hardware devices connected to the system. These aren't device drivers; instead, they are files that indicate all devices on the system and provide access to these devices.
- /etc: It includes the local system configuration files for the host system.
- /lib: It includes shared library files that are needed to start the system.
- /home: The home directory storage is available for user files. All users have a subdirectory inside /home.
- /mnt: It is a temporary mount point for basic fileSystems that can be used at the time when the administrator is working or repairing a filesystem.
- /media: A place for mounting external removable media devices like USB thumb drives that might be linked to the host.
- /opt: It contains optional files like vendor supplied application programs that must be placed here.
- /root: It's the home directory for a root user. Keep in mind that it's not the '/' (root) file system.
- /tmp: It is a temporary directory used by the OS and several programs for storing temporary files. Also, users may temporarily store files here. Remember that files may be removed without prior notice at any time in this directory.
- /sbin: These are system binary files. They are executables utilized for system administration.
- /usr: They are read-only and shareable files, including executable libraries and binaries, man files, and several documentation types.
- /var: Here, variable data files are saved. It can contain things such as MySQL, log files, other database files, email inboxes, web server data files, and much more.

Shell is interpreter program which can be used to execute commands of OS

kernel is middleware between hardware and software

sudo cat /etc/shadow print username : x : 1001 : 1001 UID : groupId here x stand for shadow file

### User Management

- adduser username will add the user into the system
- cat /etc/passwd print user on the system
- usermod will modify the user account
- sudo usermod username --shell /bin/bash
- su - username will switch to username
- sudo visudo will edit the sudoers file
- sudo userdel username will delete the user
- sudo groupadd groupName
- cat /etc/group to view group
- sudo usermod -aG groupName username
- sudo gpasswd -d username remove user from the group
- sudo groupdel groupName

### start , stop , restart Linux Services (daemon hunting)

daemons are responsible for working of your linux services and they are hidden in background , processes is instance of running programs

- ps -aux | grep sublime : will list all processes running for the sublime text editor
- daemons are the processes that we don't start
- any process will have 'd' at the end of process will be daemon
- systemd is master daemon, its working includes services management, initialization of system and it is also responsible for starting other daemon processes
- pstree will print the process tree
- systemd call other daemon as units
- sudo systemctl stop nameOfDaemon
- sudo systemctl status nameOfDaemon
- sudo systemctl disable nameOfDaemon
- sudo systemctl enable nameOfDaemon
- sudo systemctl list-units
- sudo systemctl list-unit-files | grep filename : will display the daemon which is not active by default
- sudo journalctl -xe : will do the system logs for demons
- ps -u username | grep processName
- grep stands for global regular expression print
- kill processId : kill the process
- pgrep processName : return process Id
- top : runtime processes
- htop : same as top but more detailed
- ctrl + z will sleep foreground processes you can see all sleeping processes by command 'jobs'
- bg jobId will run the sleeping process in background
- fg jobId will run the sleeping process in foreground process
- kill command sends the signal there are bunch of signals use kill -l
- kill -id processID
- pkill -9 processName ex: pkill -9 ping

Offensive security is the process of breaking into computer systems, exploiting software bugs, and finding loopholes in applications to gain unauthorized access to them.In a defensive cyber role, you could be investigating infected computers or devices to understand how it was hacked, tracking down cybercriminals, or monitoring infrastructure for malicious activity.

- We will use a command-line application called "GoBuster" to brute-force FakeBank's website to find hidden directories and pages. GoBuster will take a list of potential page or directory names and tries accessing a website with each of them; if the page exists, it tells you.
- gobuster -u http://fakebank.com -w wordlist.txt dir
- In the command above, -u is used to state the website we're scanning, -w takes a list of words to iterate through to find hidden pages.

The name "Linux" is actually an umbrella term for multiple OS's that are based on UNIX (another operating system). Thanks to UNIX being open-source, variants of Linux comes in all shapes and sizes - suited best for what the system is being used for.

For example, Ubuntu & Debian are some of the more commonplace distributions of Linux because it is so extensible. I.e. you can run Ubuntu as a server (such as websites & web applications) or as a fully-fledged desktop. For this series, we're going to be using Ubuntu.

If we remember the filename, we can simply use <b>find -name passwords.txt</b> where the command will look through every folder in our current directory for that specific file like so:

We can use <b>grep</b> to search the entire contents of this file for any entries of the value that we are searching for. Going with the example of a web server's access log, we want to see everything that the IP address "81.143.211.90" has visited (note that this is fictional)

<div class="room-task-desc-data"> <p></p><p><span><a class="vzBCaqjj glossary-term" onclick="initPopOver('Linux', 'vzBCaqjj')">Linux</a> operators are a fantastic way to power up your knowledge of working with Linux. There are a few important operators that are worth noting. We'll cover the basics and break them down accordingly to bite-sized chunks.</span></p>
<p>At an overview, I'm going to be showcasing the following operators:</p><table class="table table-bordered"><tbody><tr><td>Symbol / Operator</td><td>Description</td></tr><tr><td>&amp;</td><td>This operator allows you to run commands in the background of your terminal.</td></tr><tr><td>&amp;&amp;</td><td>This operator allows you to combine multiple commands together in one line of your terminal.</td></tr><tr><td>&gt;</td><td>This operator is a redirector - meaning that we can take the output from a command (such as using cat to output a file) and direct it elsewhere.</td></tr><tr><td>&gt;&gt;</td><td><p>This operator does the same function of the <code>&gt;</code> operator but appends the output rather than replacing (meaning nothing is overwritten).</p></td></tr></tbody></table><p>Let's cover these in a bit more detail.<br><br></p>
<h2>Operator "&amp;"</h2>
<p>This operator allows us to execute commands in the background. For example,  let's say we want to copy a large file. This will obviously take quite a long time and will leave us unable to do anything else until the file successfully copies.</p>
<p>The "&amp;" shell operator allows us to execute a command and have it run in the background (such as this file copy) allowing us to do other things!</p><p><br></p>
<h2>Operator "&amp;&amp;"</h2>
<p>This shell operator is a bit misleading in the sense of how familiar is to its partner "&amp;". Unlike the "&amp;" operator, we can use "&amp;&amp;" to make a list of commands to run for example <code>command1 &amp;&amp; command2</code>. However, it's worth noting that <code>command2</code> will only run if <code>command1</code> was successful.</p><p><br></p>
<h2>Operator "&gt;"</h2>
<p>This operator is what's known as an output redirector. What this essentially means is that we take the output from a command we run and send that output to somewhere else.</p>
<p>A great example of this is redirecting the output of the <code>echo</code> command that we learned in Task 4. Of course, running something such as <code>echo howdy</code> will return "howdy" back to our terminal — that isn't super useful. What we can do instead, is redirect "howdy" to something such as a new file!</p>
<p>Let's say we wanted to create a file named "welcome" with the message "hey". We can run <code>echo hey &gt; welcome</code> where we want the file created with the contents "hey" like so:</p>

<<p></p><p><br></p><h2>Operator "&gt;&gt;"</h2><p>This operator is also an output redirector like in the previous operator (<code>&gt;</code>) we discussed. However, what makes this operator different is that rather than overwriting any contents within a file, for example, it instead just puts the output at the end.</p><p>Following on with our previous example where we have the file "welcome" that has the contents of "hey". If were to use echo to add "hello" to the file using the <code>&gt;</code> operator, the file will now only have "hello" and not "hey".</p><p>

</p><p>The <code>&gt;&gt;</code> operator allows to append the output to the bottom of the file — rather than replacing the contents like so:</p>

<div> <p>The in-browser functionality was used in <a href="https://tryhackme.com/room/linuxfundamentalspart1" target="_blank">Linux Fundamentals Part 1</a><span> to get you directly connected to your first ever <a class="UevqnTr7 glossary-term" onclick="initPopOver('Linux', 'UevqnTr7')">Linux</a> machine without any hassle.</span></p><p>In fact, the in-browser functionality uses the exact same protocol that we are going to be using today. This protocol is called <b>S</b>ecure <b>S</b>hell or <b><span><a class="6OWAQ2QF glossary-term" onclick="initPopOver('SSH', '6OWAQ2QF')">SSH</a></span></b><span> for short and is the common means of connecting to and interacting with the command line of a remote <a class="mAGnkFOk glossary-term" onclick="initPopOver('Linux', 'mAGnkFOk')">Linux</a> machine.</span></p><p>We will be deploying two machines in this room:</p><ul><li><span>Your <a class="egmAJE9g glossary-term" onclick="initPopOver('Linux', 'egmAJE9g')">Linux</a> machine</span></li><li>The TryHackMe AttackBox</li></ul><p><span style="font-size:18px"><b><u><span>What is <a class="iX3koyRr glossary-term" onclick="initPopOver('SSH', 'iX3koyRr')">SSH</a> &amp; how Does it Work?</span></u></b></span></p><p><span>Secure Shell or <a class="Ymrg4Udx glossary-term" onclick="initPopOver('SSH', 'Ymrg4Udx')">SSH</a> simply is a protocol between devices in an encrypted form. Using cryptography, any input we send in a human-readable format is encrypted for travelling over a network -- where it is then unencrypted once it reaches the remote machine, such as in the diagram below.</span></p><p style="text-align:center"><img src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/154f110d35efe47d493df29cdb773109.svg" style="width:50%"><br></p><p><span style="font-size:1rem">You can learn about the various types of encryption on a TryHackMe room. But for now, we only need to understand that:</span><br></p><ul><li><span><a class="mhUOZ8Jc glossary-term" onclick="initPopOver('SSH', 'mhUOZ8Jc')">SSH</a> allows us to remotely execute commands on another device remotely.</span></li><li>Any data sent between the devices is encrypted when it is sent over a network such as the Internet</li></ul>

the way to connect to remote services using ssh is ssh username@ip

Files and folders with "." are hidden files.

<table class="table table-bordered"><tbody><tr><td>Command</td><td>Full Name</td><td>Purpose</td></tr><tr><td>touch</td><td>touch</td><td>Create file</td></tr><tr><td>mkdir</td><td>make directory</td><td>Create a folder</td></tr><tr><td>cp</td><td>copy</td><td>Copy a file or folder</td></tr><tr><td>mv</td><td>move</td><td>Move a file or folder</td></tr><tr><td>rm</td><td>remove</td><td>Remove a file or folder</td></tr><tr><td>file</td><td>file</td><td>Determine the type of a file</td></tr></tbody></table>

<p><code>rm</code> is extraordinary out of the commands that we've covered so far. You can simply remove files by using <code>rm</code>. However, you need to provide the <code>-R</code> switch alongside the name of the directory you wish to remove.</p>

You can use these features of nano by pressing the "Ctrl" key (which is represented as an ^ on Linux)

<div class="room-task-desc-data"> <p><b><u><span style="font-size:18px">Downloading Files</span></u></b></p><p>A pretty fundamental feature of computing is the ability to transfer files. For example, you may want to download a program, a script, or even a picture. Thankfully for us, there are multiple ways in which we can retrieve these files.</p><p>&nbsp;We're going to cover the use of <code>wget </code><span>.&nbsp; This command allows us to download files from the web via <a class="qLQJyuEs glossary-term" onclick="initPopOver('HTTP', 'qLQJyuEs')">HTTP</a> -- as if you were accessing the file in your browser. We simply need to provide the address of the resource that we wish to download. For example, if I wanted to download a file named "myfile.txt" onto my machine, assuming I knew the web address it -- it would look something like this:</span></p><p> <code>wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt</code></p><p><br></p><p><b><u><span style="font-size:18px"><span>Transferring Files From Your Host - SCP (<a class="fiV9vaZY glossary-term" onclick="initPopOver('SSH', 'fiV9vaZY')">SSH</a>)</span></span></u></b></p><p><span>Secure copy, or SCP, is just that -- a means of securely copying files. Unlike the regular cp command, this command allows you to transfer files between two computers using the <a class="hCXss74z glossary-term" onclick="initPopOver('SSH', 'hCXss74z')">SSH</a> protocol to provide both authentication and encryption.</span></p><p>Working on a model of SOURCE and DESTINATION, SCP allows you to:</p><ul><li>Copy files &amp; directories from your current system to a remote system</li><li>Copy files &amp; directories&nbsp;from a remote system to your current system</li></ul><p>Provided that we know usernames and passwords for a user on your current system and a user on the remote system. For example, let's copy an example file from our machine to a remote machine, which I have neatly laid out in the table below:</p><table class="table table-bordered"><tbody><tr><td>Variable</td><td>Value</td></tr><tr><td>The IP address of the remote system&nbsp;</td><td>192.168.1.30</td></tr><tr><td>User on the remote system</td><td>ubuntu</td></tr><tr><td>Name of the file on the local system</td><td>important.txt</td></tr><tr><td>Name that we wish to store the file as on the remote system</td><td>transferred.txt</td></tr></tbody></table><p>With this information, let's craft our <code>scp</code> command (remembering that the format of SCP is just SOURCE and DESTINATION)</p><p><code>scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt</code></p><p>And now let's reverse this and layout the syntax for using <code>scp </code>to copy a file from a remote computer that we're not logged into&nbsp;</p><table class="table table-bordered" style="width:723.2px"><tbody><tr><td>Variable</td><td>Value</td></tr><tr><td>IP address of the remote system</td><td>192.168.1.30</td></tr><tr><td>User on the remote system</td><td>ubuntu</td></tr><tr><td>Name of the file on the remote system</td><td>documents.txt</td></tr><tr><td>Name that we wish to store the file as on our system</td><td>notes.txt</td></tr></tbody></table><p>The command will now look like the following: <code>scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt&nbsp;</code></p><p><b><u><span style="font-size:18px"><br>Serving Files From Your Host - WEB</span></u></b></p><p>Ubuntu machines come pre-packaged with python3. Python helpfully provides a lightweight and easy-to-use module called "HTTPServer". This module turns your computer into a quick and easy web server that you can use to serve your own files, where they can then be downloaded by another computing using commands such as <code>curl </code>and <code>wget</code>.&nbsp;</p><p>Python3's "HTTPServer" will serve the files in the directory that you run the command, but this can be changed by providing options that can be found in the manual pages. Simply, all we need to do is run <code>python3 -m&nbsp; http.server</code> to start the module! In the screenshot below, we are serving from a directory called "webserver", which has a single named "file".</p>

<div class="terminal-container">
    <div class="terminal-content">
        <div class="terminal-top">
            Using Python to start a web server
        </div>
        <pre class="terminal-code language-shell-session" tabindex="0">           <code class=" language-shell-session"><span class="token command"><span class="token info punctuation"><span class="token user">tryhackme@linux3</span><span class="token punctuation">:</span><span class="token path">/tmp</span></span><span class="token shell-symbol important">#</span> <span class="token bash language-bash">python3 -m http.server</span></span>
<span class="token output"><span>Serving <a class="duO8aFxF glossary-term" onclick="initPopOver('HTTP', 'duO8aFxF')">HTTP</a> on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...</span></span></code>
        </pre>
    </div>
</div>
<p><br></p><p>Now, let's use <code>wget </code>to download the file using the computer's IP address and the name of the file. One flaw with this module is that you have no way of indexing, so you must know the exact name and location of the file that you wish to use. This is why I prefer to use Updog. <a href="https://github.com/sc0tfree/updog" target="_blank">What's Updog</a>? A more advanced yet lightweight webserver. But for now, let's stick to using Python's "HTTP Server".</p>

<div class="terminal-container">
    <div class="terminal-content">
        <div class="terminal-top">
            Downloading a file from our webserver using wget
        </div>
        <pre class="terminal-code language-shell-session" tabindex="0">           <code class=" language-shell-session"><span class="token command"><span class="token info punctuation"><span class="token user">tryhackme@linux3</span><span class="token punctuation">:</span><span class="token path">/tmp</span></span><span class="token shell-symbol important">#</span> <span class="token bash language-bash"><span class="token function">wget</span> http://127.0.0.1:8000/file</span></span>

<span class="token output">2021-05-04 14:26:16 http://127.0.0.1:8000/file
Connecting to http://127.0.0.1:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 51095 (50K) [text]
Saving to: ‘file’

</span><span class="token command"><span class="token info punctuation"><span class="token path">file 100</span></span><span class="token shell-symbol important">%</span><span class="token bash language-bash"><span class="token punctuation">[</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">==</span><span class="token operator">=</span><span class="token operator">&gt;</span><span class="token punctuation">]</span> <span class="token number">49</span>.90K --.-KB/s <span class="token keyword">in</span> <span class="token number">0</span>.04s</span></span>

<span class="token output">2021-05-04 14:26:16 (1.31 MB/s) - ‘file’ saved [51095/51095]</span></code>

</pre>
</div>

</div>

<p>In the screenshot above, we can see that <code>wget</code> has successfully downloaded the file named "file" to our machine. This request is logged by SimpleHTTPServer much as any web server would, which I have captured in the screenshot below.</p>

<div class="terminal-container">
    <div class="terminal-content">
        <div class="terminal-top">
            Using Python to start a web server
        </div>
        <pre class="terminal-code language-shell-session" tabindex="0">           <code class=" language-shell-session"><span class="token command"><span class="token info punctuation"><span class="token user">tryhackme@linux3</span><span class="token punctuation">:</span><span class="token path">/tmp</span></span><span class="token shell-symbol important">#</span> <span class="token bash language-bash">python3 -m http.server</span></span>
<span class="token output"><span>Serving <a class="opZiYFAY glossary-term" onclick="initPopOver('HTTP', 'opZiYFAY')">HTTP</a> on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
127.0.0.1 - - [04/May/2021/14:26:09] "GET /file HTTP/1.1" 200 -</span></span></code>
        </pre>
    </div>
</div></div>

We can use the friendly ps command to provide a list of the running processes as our user's session and some additional information such as its status code, the session that is running it, how much usage time of the CPU it is using, and the name of the actual program or command that is being executed:

To see the processes run by other users and those that don't run from a session (i.e. system processes), we need to provide aux to the ps command like so: ps aux

How do Processes Start?

Let's start off by talking about namespaces. The Operating System (OS) uses namespaces to ultimately split up the resources available on the computer to (such as CPU, RAM and priority) processes. Think of it as splitting your computer up into slices -- similar to a cake. Processes within that slice will have access to a certain amount of computing power, however, it will be a small portion of what is actually available to every process overall.

Namespaces are great for security as it is a way of isolating processes from another -- only those that are in the same namespace will be able to see each other.

We previously talked about how PID works, and this is where it comes into play. The process with an ID of 0 is a process that is started when the system boots. This process is the system's init on Ubuntu, such as systemd, which is used to provide a way of managing a user's processes and sits in between the operating system and the user.

For example, once a system boots and it initialises, systemd is one of the first processes that are started. Any program or piece of software that we want to start will start as what's known as a child process of systemd. This means that it is controlled by systemd, but will run as its own process (although sharing the resources from systemd) to make it easier for us to identify and the likes.

With our process backgrounded using either Ctrl + Z or the & operator, we can use fg to bring this back to focus like below, where we can see the fg command is being used to bring the background process back into use on the terminal, where the output of the script is now returned to us.

<div class="card" id="task-6">
                    <div class="card-header task-header" data-toggle="collapse" href="#collapse6" aria-expanded="true">
                        <a class="card-link">
                            <span class="task-dropdown-title red">Task 6                             <span class="task-dropdown-icon"><i class="far fa-circle text-lgray"></i></span></span> Maintaining Your System: Automation
                            <span class="float-right"><i class="fas fa-chevron-down"></i></span>
                            <span class="task-resources"></span>
                        </a>
                    </div>
                    <div id="collapse6" class="collapse show" data-parent="#taskContent" style="">
                        <div class="card-body task-incomplete">
                            <div class="room-task-desc">
            <div class="room-task-desc-data"> <p><span style="font-size:1rem">Users may want to schedule a certain action or task to take place after the system has booted. Take, for example, running commands, backing up files, or launching your favourite programs on, such as Spotify or Google Chrome.</span><br></p><p>We're going to be talking about the <code>cron</code> process, but more specifically, how we can interact with it via the use of <code>crontabs</code> . Crontab is one of the processes that is started during boot, which is responsible for facilitating and managing cron jobs.</p><p><img src="https://assets.tryhackme.com/additional/linux-fundamentals/part3/cron1.png" style="width:630px;height:433.454px"><br></p><p>A crontab is simply a special file with formatting that is recognised by the <code>cron</code> process to execute each line step-by-step. Crontabs require 6 specific values:</p><table class="table table-bordered"><tbody><tr><td>Value</td><td>Description</td></tr><tr><td>MIN</td><td>What minute to execute at</td></tr><tr><td>HOUR</td><td>What hour to execute at</td></tr><tr><td>DOM</td><td>What day of the month to execute at<br></td></tr><tr><td>MON</td><td>What month of the year to execute at</td></tr><tr><td>DOW</td><td>What day of the week to execute at</td></tr><tr><td>CMD</td><td>The actual command that will be executed.</td></tr></tbody></table><p><br></p><p>Let's use the example of backing up files. You may wish to backup "cmnatic"'s&nbsp; "Documents" every 12 hours. We would use the following formatting:&nbsp;</p><p><code>0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/</code><span style="color:rgb(164, 158, 147);font-family:arial;font-size:13px;font-weight:700;white-space:pre-wrap;--darkreader-inline-color:#c4baa9"></span></p><p>An interesting feature of crontabs is that these also support the wildcard or asterisk (<code>*</code>). If we do not wish to provide a value for that specific field, i.e. we don't care what month, day, or year it is executed -- only that it is executed every 12 hours, we simply just place an asterisk.</p><p>This can be confusing to begin with, which is why there are some great resources such as the online "<a href="https://crontab-generator.org/" target="_blank">Crontab Generator</a>" that allows you to use a friendly application to generate your formatting for you! As well as the site "<a href="https://crontab.guru/" target="_blank">Cron Guru</a>"!</p><p>Crontabs can be edited by using <code>crontab -e</code>, where you can select an editor (such as Nano) to edit your crontab.</p><p><img src="https://assets.tryhackme.com/additional/linux-fundamentals/part3/cron2.png" style="width:541.105px;height:294.438px"><br></p><p><img src="https://assets.tryhackme.com/additional/linux-fundamentals/part3/cron3.png" style="width:508px;height:361.496px"></p></div>
        </div>
        
      
The file system used in modern versions of Windows is the New Technology File System or simply NTFS.
Before NTFS, there was FAT16/FAT32 (File Allocation Table) and HPFS (High Performance File System).

You still see FAT partitions in use today. For example, you typically see FAT partitions in USB devices, MicroSD cards, etc. but traditionally not on personal Windows computers/laptops or Windows servers.

NTFS is known as a journaling file system. In case of a failure, the file system can automatically repair the folders/files on disk using information stored in a log file. This function is not possible with FAT.

NTFS addresses many of the limitations of the previous file systems; such as:

Supports files larger than 4GB
Set specific permissions on folders and files
Folder and file compression
Encryption (Encryption File System or EFS)

Another feature of NTFS is Alternate Data Streams (ADS).

Alternate Data Streams (ADS) is a file attribute specific to Windows NTFS (New Technology File System).

Every file has at least one data stream ($DATA), and ADS allows files to contain more than one stream of data. Natively Window Explorer doesn't display ADS to the user. There are 3rd party executables that can be used to view this data, but Powershell gives you the ability to view ADS for files.

From a security perspective, malware writers have used ADS to hide data.

Not all its uses are malicious. For example, when you download a file from the Internet, there are identifiers written to ADS to identify that the file was downloaded from the Internet.

To learn more about ADS, refer to the following link from MalwareBytes here.
Note</p>

<p>HPFS is only supported under Windows NT versions 3.1, 3.5, and 3.51. Windows NT 4.0 does not support and cannot access HPFS partitions. Also, support for the FAT32 file system became available in Windows 98/Windows 95 OSR2 and Windows 2000.</p>
</div>
<div class="heading-wrapper" data-heading-level="h2"><a class="anchor-link docon docon-link" href="#fat-overview" aria-label="Section titled: FAT overview"></a><h2 id="fat-overview" class="heading-anchor">FAT overview</h2></div>
<p>FAT is by far the most simplistic of the file systems supported by Windows NT. The FAT file system is characterized by the file allocation table (FAT), which is really a table that resides at the very "top" of the volume. To protect the volume, two copies of the FAT are kept in case one becomes damaged. In addition, the FAT tables and the root directory must be stored in a fixed location so that the system's boot files can be correctly located.</p>
<p>A disk formatted with FAT is allocated in clusters, whose size is determined by the size of the volume. When a file is created, an entry is created in the directory and the first cluster number containing data is established. This entry in the FAT table either indicates that this is the last cluster of the file, or points to the next cluster.</p>
<p>Updating the FAT table is very important as well as time consuming. If the FAT table is not regularly updated, it can lead to data loss. It is time consuming because the disk read heads must be repositioned to the drive's logical track zero each time the FAT table is updated.</p>
<p>There is no organization to the FAT directory structure, and files are given the first open location on the drive. In addition, FAT supports only read-only, hidden, system, and archive file attributes.</p>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#fat-naming-convention" aria-label="Section titled: FAT naming convention"></a><h3 id="fat-naming-convention" class="heading-anchor">FAT naming convention</h3></div>
<p>FAT uses the traditional 8.3 file naming convention and all filenames must be created with the ASCII character set. The name of a file or directory can be up to eight characters long, then a period (.) separator, and up to a three character extension. The name must start with either a letter or number and can contain any characters except for the following:</p>
<p><code>. " / \ [ ] : ; | = ,</code></p>
<p>If any of these characters are used, unexpected results may occur. The name cannot contain any spaces.</p>
<p>The following names are reserved:</p>
<p>CON, AUX, COM1, COM2, COM3, COM4, LPT1, LPT2, LPT3, PRN, NUL</p>
<p>All characters will be converted to uppercase.</p>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#advantages-of-fat" aria-label="Section titled: Advantages of FAT"></a><h3 id="advantages-of-fat" class="heading-anchor">Advantages of FAT</h3></div>
<p>It is not possible to perform an undelete under Windows NT on any of the supported file systems. Undelete utilities try to directly access the hardware, which cannot be done under Windows NT. However, if the file was located on a FAT partition, and the system is restarted under MS-DOS, the file can be undeleted. The FAT file system is best for drives and/or partitions under approximately 200 MB, because FAT starts out with very little overhead. For further discussion of FAT advantages, see the following:</p>
<ul>
<li><p>Windows NT Server "Concepts and Planning Guide," Chapter 5, section titled "Choosing a File System"</p>
</li>
<li><p>Windows NT Workstation 4.0 Resource Kit, Chapter 18, "Choosing a File System"</p>
</li>
<li><p>Windows NT Server 4.0 Resource Kit "Resource Guide," Chapter 3, section titled "Which File System to Use on Which Volumes"</p>
</li>
</ul>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#disadvantages-of-fat" aria-label="Section titled: Disadvantages of FAT"></a><h3 id="disadvantages-of-fat" class="heading-anchor">Disadvantages of FAT</h3></div>
<p>Preferably, when using drives or partitions of over 200 MB the FAT file system should not be used. This is because as the size of the volume increases, performance with FAT will quickly decrease. It is not possible to set permissions on files that are FAT partitions.</p>
<p>FAT partitions are limited in size to a maximum of 4 Gigabytes (GB) under Windows NT and 2 GB in MS-DOS.</p>
<p>For further discussion of other disadvantages of FAT, see the following:</p>
<ul>
<li><p>Windows NT Server "Concepts and Planning Guide," Chapter 5, section titled "Choosing a File System"</p>
</li>
<li><p>Windows NT Workstation 4.0 Resource Kit, Chapter 18, "Choosing a File System"</p>
</li>
<li><p>Microsoft Windows NT Server 4.0 Resource Kit "Resource Guide," Chapter 3, section titled "Which File System to Use on Which Volumes"</p>
</li>
</ul>
<div class="heading-wrapper" data-heading-level="h2"><a class="anchor-link docon docon-link" href="#hpfs-overview" aria-label="Section titled: HPFS overview"></a><h2 id="hpfs-overview" class="heading-anchor">HPFS overview</h2></div>
<p>The HPFS file system was first introduced with OS/2 1.2 to allow for greater access to the larger hard drives that were then appearing on the market. Additionally, it was necessary for a new file system to extend the naming system, organization, and security for the growing demands of the network server market. HPFS maintains the directory organization of FAT, but adds automatic sorting of the directory based on filenames. Filenames are extended to up to 254 double byte characters. HPFS also allows a file to be composed of "data" and special attributes to allow for increased flexibility in terms of supporting other naming conventions and security. In addition, the unit of allocation is changed from clusters to physical sectors (512 bytes), which reduces lost disk space.</p>
<p>Under HPFS, directory entries hold more information than under FAT. As well as the attribute file, this includes information about the modification, creation, and access date and times. Instead of pointing to the first cluster of the file, the directory entries under HPFS point to the FNODE. The FNODE can contain the file's data, or pointers that may point to the file's data or to other structures that will eventually point to the file's data.</p>
<p>HPFS attempts to allocate as much of a file in contiguous sectors as possible. This is done in order to increase speed when doing sequential processing of a file.</p>
<p>HPFS organizes a drive into a series of 8-MB bands, and whenever possible a file is contained within one of these bands. Between each of these bands are 2K allocation bitmaps, which keep track of which sectors within a band have and have not been allocated. Banding increases performance because the drive head does not have to return to the logical top (typically cylinder 0) of the disk, but to the nearest band allocation bitmap to determine where a file is to be stored.</p>
<p>Additionally, HPFS includes a couple of unique special data objects:</p>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#super-block" aria-label="Section titled: Super Block"></a><h3 id="super-block" class="heading-anchor">Super Block</h3></div>
<p>The Super Block is located in logical sector 16 and contains a pointer to the FNODE of the root directory. One of the biggest dangers of using HPFS is that if the Super Block is lost or corrupted due to a bad sector, so are the contents of the partition, even if the rest of the drive is fine. It would be possible to recover the data on the drive by copying everything to another drive with a good sector 16 and rebuilding the Super Block. However, this is a very complex task.</p>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#spare-block" aria-label="Section titled: Spare Block"></a><h3 id="spare-block" class="heading-anchor">Spare Block</h3></div>
<p>The Spare Block is located in logical sector 17 and contains a table of "hot fixes" and the Spare Directory Block. Under HPFS, when a bad sector is detected, the "hot fixes" entry is used to logically point to an existing good sector in place of the bad sector. This technique for handling write errors is known as hot fixing.</p>
<p>Hot fixing is a technique where if an error occurs because of a bad sector, the file system moves the information to a different sector and marks the original sector as bad. This is all done transparent to any applications that are performing disk I/O (that is, the application never knows that there were any problems with the hard drive). Using a file system that supports hot fixing will eliminate error messages such as the FAT "Abort, Retry, or Fail?" error message that occurs when a bad sector is encountered.</p>
<div class="alert is-info">
<p class="alert-title"><span class="docon docon-status-error-outline" aria-hidden="true"></span> Note</p>
<p>The version of HPFS that is included with Windows NT does not support hot fixing.</p>
</div>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#advantages-of-hpfs" aria-label="Section titled: Advantages of HPFS"></a><h3 id="advantages-of-hpfs" class="heading-anchor">Advantages of HPFS</h3></div>
<p>HPFS is best for drives in the 200-400 MB range. For more discussion of the advantages of HPFS, see the following:</p>
<ul>
<li><p>Windows NT Server "Concepts and Planning Guide," Chapter 5, section titled "Choosing a File System"</p>
</li>
<li><p>Windows NT Workstation 4.0 Resource Kit, Chapter 18, "Choosing a File System"</p>
</li>
<li><p>Windows NT Server 4.0 Resource Kit "Resource Guide," Chapter 3, section titled "Which File System to Use on Which Volumes"</p>
</li>
</ul>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#disadvantages-of-hpfs" aria-label="Section titled: Disadvantages of HPFS"></a><h3 id="disadvantages-of-hpfs" class="heading-anchor">Disadvantages of HPFS</h3></div>
<p>Because of the overhead involved in HPFS, it is not a very efficient choice for a volume of under approximately 200 MB. In addition, with volumes larger than about 400 MB, there will be some performance degradation. You cannot set security on HPFS under Windows NT.</p>
<p>HPFS is only supported under Windows NT versions 3.1, 3.5, and 3.51. Windows NT 4.0 cannot access HPFS partitions.</p>
<p>For additional disadvantages of HPFS, see the following:</p>
<ul>
<li><p>Windows NT Server "Concepts and Planning Guide," Chapter 5, section titled "Choosing a File System"</p>
</li>
<li><p>Windows NT Workstation 4.0 Resource Kit, Chapter 18, "Choosing a File System"</p>
</li>
<li><p>Windows NT Server 4.0 Resource Kit "Resource Guide," Chapter 3, section titled "Which File System to Use on Which Volumes"</p>
</li>
</ul>
<div class="heading-wrapper" data-heading-level="h2"><a class="anchor-link docon docon-link" href="#ntfs-overview" aria-label="Section titled: NTFS overview"></a><h2 id="ntfs-overview" class="heading-anchor">NTFS overview</h2></div>
<p>From a user's point of view, NTFS continues to organize files into directories, which, like HPFS, are sorted. However, unlike FAT or HPFS, there are no "special" objects on the disk and there is no dependence on the underlying hardware, such as 512-byte sectors. In addition, there are no special locations on the disk, such as FAT tables or HPFS Super Blocks.</p>
<p>The goals of NTFS are to provide:</p>
<ul>
<li><p>Reliability, which is especially desirable for high end systems and file servers</p>
</li>
<li><p>A platform for added functionality</p>
</li>
<li><p>Support POSIX requirements</p>
</li>
<li><p>Removal of the limitations of the FAT and HPFS file systems</p>
</li>
</ul>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#reliability" aria-label="Section titled: Reliability"></a><h3 id="reliability" class="heading-anchor">Reliability</h3></div>
<p>To ensure reliability of NTFS, three major areas were addressed: recoverability, removal of fatal single sector failures, and hot fixing.</p>
<p>NTFS is a recoverable file system because it keeps track of transactions against the file system. When a CHKDSK is performed on FAT or HPFS, the consistency of pointers within the directory, allocation, and file tables are being checked. Under NTFS, a log of transactions against these components is maintained so that CHKDSK need only roll back transactions to the last commit point in order to recover consistency within the file system.</p>
<p>Under FAT or HPFS, if a sector that is the location of one of the file system's special objects fails, then a single sector failure will occur. NTFS avoids this in two ways: first, by not using special objects on the disk and tracking and protecting all objects that are on the disk. Secondly, under NTFS, multiple copies (the number depends on the volume size) of the Master File Table are kept.</p>
<p>Similar to OS/2 versions of HPFS, NTFS supports hot fixing.</p>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#added-functionality" aria-label="Section titled: Added functionality"></a><h3 id="added-functionality" class="heading-anchor">Added functionality</h3></div>
<p>One of the major design goals of Windows NT at every level is to provide a platform that can be added to and built upon, and NTFS is no exception. NTFS provides a rich and flexible platform for other file systems to be able to use. In addition, NTFS fully supports the Windows NT security model and supports multiple data streams. No longer is a data file a single stream of data. Finally, under NTFS, a user can add his or her own user-defined attributes to a file.</p>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#posix-support" aria-label="Section titled: POSIX support"></a><h3 id="posix-support" class="heading-anchor">POSIX support</h3></div>
<p>NTFS is the most POSIX.1 compliant of the supported file systems because it supports the following POSIX.1 requirements:</p>
<p>Case-sensitive naming:</p>
<p>Under POSIX, README.TXT, Readme.txt, and readme.txt are all different files.</p>
<p>Additional time stamp:</p>
<p>The additional time stamp supplies the time at which the file was last accessed.</p>
<p>Hard links:</p>
<p>A hard link is when two different filenames, which can be located in different directories, point to the same data.</p>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#remove-limitations" aria-label="Section titled: Remove limitations"></a><h3 id="remove-limitations" class="heading-anchor">Remove limitations</h3></div>
<p>First, NTFS has greatly increased the size of files and volumes, so that they can now be up to 2^64 bytes (16 exabytes or 18,446,744,073,709,551,616 bytes). NTFS has also returned to the FAT concept of clusters in order to avoid HPFS problem of a fixed sector size. This was done because Windows NT is a portable operating system and different disk technology is likely to be encountered at some point. Therefore, 512 bytes per sector was viewed as having a large possibility of not always being a good fit for the allocation. This was accomplished by allowing the cluster to be defined as multiples of the hardware's natural allocation size. Finally, in NTFS all filenames are Unicode based, and 8.3 filenames are kept along with long filenames.</p>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#advantages-of-ntfs" aria-label="Section titled: Advantages of NTFS"></a><h3 id="advantages-of-ntfs" class="heading-anchor">Advantages of NTFS</h3></div>
<p>NTFS is best for use on volumes of about 400 MB or more. This is because performance does not degrade under NTFS, as it does under FAT, with larger volume sizes.</p>
<p>The recoverability designed into NTFS is such that a user should never have to run any sort of disk repair utility on an NTFS partition. For additional advantages of NTFS, see the following:</p>
<ul>
<li><p>Windows NT Server "Concepts and Planning Guide," Chapter 5, section titled "Choosing a File System"</p>
</li>
<li><p>Windows NT Workstation 4.0 Resource Kit, Chapter 18, "Choosing a File System"</p>
</li>
<li><p>Windows NT Server 4.0 Resource Kit "Resource Guide," Chapter 3, section titled "Which File System to Use on Which Volumes"</p>
</li>
</ul>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#disadvantages-of-ntfs" aria-label="Section titled: Disadvantages of NTFS"></a><h3 id="disadvantages-of-ntfs" class="heading-anchor">Disadvantages of NTFS</h3></div>
<p>It is not recommended to use NTFS on a volume that is smaller than approximately 400 MB, because of the amount of space overhead involved in NTFS. This space overhead is in the form of NTFS system files that typically use at least 4 MB of drive space on a 100-MB partition.</p>
<p>Currently, there is no file encryption built into NTFS. Therefore, someone can boot under MS-DOS, or another operating system, and use a low-level disk editing utility to view data stored on an NTFS volume.</p>
<p>It is not possible to format a floppy disk with the NTFS file system; Windows NT formats all floppy disks with the FAT file system because the overhead involved in NTFS will not fit onto a floppy disk.</p>
<p>For further discussion of NTFS disadvantages, see the following:</p>
<ul>
<li><p>Windows NT Server "Concepts and Planning Guide," Chapter 5, section titled "Choosing a File System"</p>
</li>
<li><p>Windows NT Workstation 4.0 Resource Kit, Chapter 18, "Choosing a File System"</p>
</li>
<li><p>Windows NT Server 4.0 Resource Kit "Resource Guide," Chapter 3, section titled "Which File System to Use on Which Volumes"</p>
</li>
</ul>
<div class="heading-wrapper" data-heading-level="h3"><a class="anchor-link docon docon-link" href="#ntfs-naming-conventions" aria-label="Section titled: NTFS naming conventions"></a><h3 id="ntfs-naming-conventions" class="heading-anchor">NTFS naming conventions</h3></div>
<p>File and directory names can be up to 255 characters long, including any extensions. Names preserve case, but are not case-sensitive. NTFS makes no distinction of filenames based on case. Names can contain any characters except for the following:</p>
<p><code>? " / \ &lt; &gt; * | :</code></p>
<p>Currently, from the command line, you can only create file names of up to 253 characters.</p>
<div class="alert is-info">
<p class="alert-title"><span class="docon docon-status-error-outline" aria-hidden="true"></span> Note</p>
<p>Underlying hardware limitations may impose additional partition size limitations in any file system. Particularly, a boot partition can be only 7.8 GB in size, and there is a 2-terabyte limitation in the partition table.</p>
</div>
<p>For more information about the supported file systems for Windows NT, see the Windows NT Resource Kit.</p>

link : https://www.malwarebytes.com/blog/news/2015/07/introduction-to-alternate-data-streams

What are Alternate Data Streams?
Alternate Data Streams (ADS) are a file attribute only found on the NTFS file system.

In this system a file is built up from a couple of attributes, one of them is $Data, aka the data attribute. Looking at the regular data stream of a text file there is no mystery. It simply contains the text inside the text file. But that is only the primary data stream.

This one is sometimes referred to as the unnamed data stream since the name string of this attribute is empty ( “” ) . So any data stream that has a name is considered alternate.

These data streams suffer from a bad reputation since they have been used and abused to write hidden data. Varying from data about where a file came from to complete malware files (e.g. Backdoor.Rustock.A)

If you are up for an experiment, we can easily create and read an alternate data stream.

Streams
The first tool you can use was developed by Sysinternals (later bought by Microsoft) and is called Streams (nomen est omen).

voorbeeld
In the example above we used the echo command to create an empty file called example with an alternate data stream called showme.

By using streams we can check which files have alternate data-streams. In the results visible in the above command prompt, $Data is the name of the attribute (as discussed earlier) and the 8 tells us the size.

But since we are looking at it, we obviously would like to see what is inside the alternate data streams. Unfortunately, streams do not offer that option.

Get-Item
If you are using Windows 8 (or newer) there is a built-in option to read ADS. You can use PowerShell commands to achieve this. For those that have no experience with it, you can start it by typing PowerShell in the Run box (Windows key + R) and follow the lines in this screenshot.

powershell
Set-item
Another thing that you can do with Powershell is add streams to a file. The Powershell command syntax is:

set-content - path {path to the file} - stream {name of the stream}
Doing so will initiate a cmdlet where you can enter the content of the stream under Value[i]

PSsetcontent
Search for ADS
If you want to search a directory or drive for ADS you can use this command in the root of the target:

gci -recurse | % { gi $_.FullName -stream * } | where stream -ne ':$Data'
PSsearch
Be warned that if you include the Windows directory in your search you will likely receive an enormous list.

Remove ADS
A word of warning here. Removing ADS is not always advisable. Some of them are needed for the proper use of the software that created the streams. So make sure you have done your research before removing them. The syntax is:

remove-item –path {path to the file} –stream {name of the stream}
Malwarebytes Anti-Malware scans for and removes unwanted ADS (as Rootkit.ADS)

Summary
Alternate Data Streams (ADS) have been given a bad reputation because their capability to hide data from us on our own computer, has been abused by malware writers in the past. Hopefully this article will clear up some of the questions and mystique you had about ADS.

<<<<<<< HEAD
"Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders".

Dynamic Link Library (DLL) files are shared library files used by Windows programs — both utilities built into Windows and third-party programs you install — to perform various functions.

How does UAC work? When a user with an account type of administrator logs into a system, the current session doesn't run with elevated permissions. When an operation requiring higher-level privileges needs to execute, the user will be prompted to confirm if they permit the operation to run.

Let's look at the program on the account you're currently logged into, the built-in administrator account—Right-click to view its Properties.

In the Security tab, we can see the users/groups and their permissions to this file. Notice that the standard user is not listed.

=======

> > > > > > > 4108875ec1be1a7d41fdef6a56ccb0750ca2eefc

# cyber-security

The System Configuration utility (MSConfig) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues.

<div class="room-task-desc-data"> <p>We're continuing with Tools that are available through the&nbsp;<span style="font-weight:bolder">System Configuration</span>&nbsp;panel.<br></p><p>The <b>Computer Management </b>(<code>compmgmt</code><b></b>)<b>&nbsp;</b>utility has three primary sections:&nbsp;<span style="font-weight:bolder">System Tools</span>,&nbsp;<span style="font-weight:bolder">Storage</span>, and&nbsp;<span style="font-weight:bolder">Services and Applications</span>.</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/compmgmt1.png" style="width:372px"><br></p><p><b>System Tools</b></p><p>Let's start with <b>Task Scheduler</b>. Per Microsoft, with Task Scheduler, we can create and manage common tasks that our computer will carry out automatically at the times we specify.</p><p>A task can run an application, a script, etc., and tasks can be configured to run at any point. A task can run at log in or at log off. Tasks can also be configured to run on a specific schedule, for example, every five mins.</p><p>To create a basic task, click on <code>Create Basic Task</code> under <b>Actions</b> (right pane).</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/create-task.png" style="width:233px"><br></p><p>Next is <b>Event Viewer</b>.</p><p>Event Viewer allows us to view events that have occurred on the computer. These records of events can be seen as an audit trail that can be used to understand the activity of the computer system. This information is often used to diagnose problems and investigate actions executed on the system.&nbsp;</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/event-viewer.png" style="width:489px"><br></p><div>Event Viewer has three panes.</div><ol><li>The pane on the left provides a hierarchical tree listing of the event log providers. (as shown in the image above)</li><li>The pane in the middle will display a general overview and summary of the events specific to a selected provider.</li><li>The pane on the right is the actions pane.</li></ol><div>There are five types of events that can be logged. Below is a table from&nbsp;<a href="https://docs.microsoft.com/en-us/windows/win32/eventlog/event-types">docs.microsoft.com</a>&nbsp;providing a brief description for each.</div><div><br></div><div><img src="https://assets.tryhackme.com/additional/win-event-logs/five-event-types.png" alt=""></div><div><br></div><div>The standard logs are visible under&nbsp;<span style="font-weight:bolder">Windows Logs</span>. Below is a table from&nbsp;<a href="https://docs.microsoft.com/en-us/windows/win32/eventlog/eventlog-key">docs.microsoft.com</a>&nbsp;providing a brief description for each.</div><div><br></div><div><img src="https://assets.tryhackme.com/additional/win-event-logs/standard-event-logs.png" alt=""></div><div><br></div><p>For more information about Event Viewer and Event Logs, please refer to the Windows Event Log <a href="https://tryhackme.com/room/windowseventlogs" target="_blank">room</a>.&nbsp;</p><p><b>Shared Folders</b> is where you will see a complete list of shares and folders shared that others can connect to.&nbsp;</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/shared-folders.png" style="width:548px"><br></p><p>In the above image, under Shares, are the default share of Windows, C$, and default remote administration shares created by Windows, such as ADMIN$.&nbsp;</p><p><span style="font-size:1rem">As with any object in Windows, you can right-click on a folder to view its properties, such as Permissions (who can access the shared resource).&nbsp;</span></p><p><span style="font-size:1rem">Under <b>Sessions</b>, you will see a list of users who are currently connected to the shares. In this VM, you won't see anybody connected to the shares.</span></p><p>All the folders and/or files that the connected users access will list under <b>Open Files</b>.</p><p><span style="font-size:1rem">The <b>Local Users and Groups</b> section you should be familiar with from <a href="https://tryhackme.com/room/windowsfundamentals1xbx" target="_blank">Windows Fundamentals 1</a> because it's </span><code>lusrmgr.msc</code><span style="font-size:1rem">.</span></p><p><span style="font-size:1rem">In <b>Performance</b>, you'll see a utility called <b>Performance Monitor</b> (</span><code>perfmon</code><span style="font-size:1rem">). </span></p><p><span style="font-size:1rem">Perfmon is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote.&nbsp;</span></p><p><img src="https://assets.tryhackme.com/additional/win-fun2/perfmon.png" style="width:687px"></p><p><b>Device Manager</b> allows us to view and configure the hardware, such as disabling any hardware attached to the computer.</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/device-mgr.png" style="width:269px"><br></p><p><b>Storage</b>&nbsp;&nbsp;</p><p>Under Storage is <b>Windows Server Backup</b> and <b>Disk Management</b>. We'll only look at Disk Management in this room.</p><p><b>Note</b>: Since the virtual machine is a Windows Server operating system, there are utilities available that you will typically not see in Windows 10.&nbsp;&nbsp;</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/disk-mgmt.png" style="width:833px"><br></p><p>Disk Management is a system utility in Windows that enables you to perform advanced storage tasks.&nbsp;&nbsp;<span style="font-size:1rem">Some tasks are:</span></p><ul><li>Set up a new drive</li><li>Extend a partition</li><li>Shrink a partition</li><li>Assign or change a drive letter (ex. E:)&nbsp;</li></ul><p><b>Services and Applications</b></p><p><img src="https://assets.tryhackme.com/additional/win-fun2/services-apps.png" style="width:808px"><br></p><p>Recall from the previous task; a<span style="font-size:1rem">&nbsp;service is a special type of application that runs in the background. Here you can do more than enable and disable a service, such as view the Properties for the service.&nbsp;</span></p><p><img src="https://assets.tryhackme.com/additional/win-fun2/service.png" style="width:403px"><br></p><p><span style="font-size:1rem">WMI Control configures and controls the <b>Windows Management Instrumentation</b> (WMI) service.</span></p><p><span style="font-size:1rem">Per Wikipedia, "</span><i>WMI allows scripting languages (such as VBScript or Windows PowerShell) to manage Microsoft Windows personal computers and servers, both locally and remotely. Microsoft also provides a command-line interface to WMI called Windows Management Instrumentation Command-line (WMIC).</i>"</p><p><b>Note</b>: The WMIC tool is deprecated in Windows 10, version 21H1. Windows PowerShell supersedes this tool for WMI.&nbsp;</p></div>

<div class="room-task-desc-data"> <p>We're continuing with Tools that are available through the&nbsp;<span style="font-weight:bolder">System Configuration</span>&nbsp;panel.<br></p><p>What is the <b>System Information</b> (<code>msinfo32</code>) tool?</p><p>Per Microsoft, "<i>Windows includes a tool called Microsoft System Information (Msinfo32.exe).&nbsp; This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues.</i>"</p><p>The&nbsp; information in <b>System Summary</b> is divided into three sections:</p><ul><li><b>Hardware Resources</b></li><li><b>Components</b></li><li><b>Software Environment</b></li></ul><p>System Summary will display general technical specifications for the computer, such as processor brand and model.</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/system-summary.png" style="width:970px"><br></p><p>The information displayed in <b>Hardware Resources</b> is not for the average computer user. If you want to learn more about this section, refer to the official Microsoft <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/kernel/hardware-resources#:~:text=Hardware%20resources%20are%20the%20assignable,of%20bus%2Drelative%20memory%20addresses." target="_blank">page</a>.</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/hardware-resources.png" style="width:216px"><br></p><p>Under <b>Components</b>, you can see specific information about the hardware devices installed on the computer. Some sections don't show any information, but some sections do, such as <b>Display</b> and <b>Input</b>.</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/components.png" style="width:166px"><br></p><p>In the <b>Software Environmen</b>t section, you can see information about software baked into the operating system and software you have installed. Other details are visible in this section as well, such as the <b>Environment Variables</b> and <b>Network Connections</b>.&nbsp;</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/software-env.png" style="width:210px"></p><p>Recall from the <a href="https://tryhackme.com/room/windowsfundamentals1xbx" target="_blank">Windows Fundamentals 1 room&nbsp;</a>(The Windows\System32 Folder task) where&nbsp;<b>Environment Variables</b>&nbsp;was briefly touched on.&nbsp;</p><p>Per <a href="https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.1" target="_blank">Microsoft</a>, "<i>Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.</i></p><p><i>The environment variables store data that is used by the operating system and other programs. For example, the WINDIR environment variable contains the location of the Windows installation directory. Programs can query the value of this variable to determine where Windows operating system files are located</i>".</p><p>Click on <code>Environment Variables</code> to see the assigned values for the virtual machine.</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/env-variables.png" style="width:1076px"><br></p><p>Another method to view environment variables is <code>Control Panel &gt; System and Security &gt; System &gt; Advanced system settings &gt; Environment Variables</code> <b>OR</b> <code>Settings &gt; System &gt; About &gt; system info &gt; Advanced system settings &gt; Environment Variables</code>.</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/env-variables2.png" style="width:628px"><br></p><p>The detour is over. Let's redirect our attention back to <code>msinfo32</code> and pick up where we left off.</p><p>Towards the very bottom of this utility, there is a search bar. Please give it a go. Select Components and search for <code>IP address</code>.</p><p><img src="https://assets.tryhackme.com/additional/win-fun2/msinfo32-search.png" style="width:1076px"><br></p></div>

Traffic flows into and out of devices via what we call ports. A firewall is what controls what is - and more importantly isn't - allowed to pass through those ports. You can think of it like a security guard standing at the door, checking the ID of everything that tries to enter or exit

What is BitLocker?

Per Microsoft, "BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers".

On devices with TPM installed, BitLocker offers the best protection.

Per Microsoft, "BitLocker provides the most protection when used with a Trusted Platform Module (TPM) version 1.2 or later. The TPM is a hardware component installed in many newer computers by the computer manufacturers. It works with BitLocker to help protect user data and to ensure that a computer has not been tampered with while the system was offline".

Refer to the official Microsoft documentation to learn more about BitLocker here.

Note: The BitLocker feature is not included in the attached VM.

computer network is interconnectin between computer devices that can share data and resoures. this network devices use system rules to connect called connection protocols

# Networking

<div class="room-task-desc-data"> <p>The OSI (<b>O</b>pen <b>S</b>ystems <b>I</b>nterconnection) Model is a standardised model which we use to demonstrate the theory behind computer networking. In practice, it's actually the more compact TCP/IP model that real-world networking is based off; however the OSI model, in many ways, is easier to get an initial understanding from.</p><p>The OSI model consists of seven layers:</p><p><img style="width:134px" alt="Table showing the OSI layers: Application, Presentation, Session, Transport, Network, Data Link, Physical" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/02/OSI-Table.png"></p><p>There are many mnemonics floating around to help you learn the layers of the OSI model -- search around until you find one that you like.</p><p>I personally favour: <b>A</b>nxious <b>P</b>ale <b>S</b>hakespeare <b>T</b>reated <b>N</b>ervous <b>D</b>runks <b>P</b>atiently</p><p>Let's briefly take a look at each of these in turn:</p><p><u>Layer 7 -- Application</u><u>:</u></p><p>The application layer of the OSI model essentially provides networking options to programs running on a computer. It works almost exclusively with applications, providing an interface for them to use in order to transmit data. When data is given to the application layer, it is passed down into the presentation layer.<br></p><p><u>Layer 6 -- Presentation</u><u>:</u></p><p>The presentation layer receives data from the application layer. This data tends to be in a format that the application understands, but it's not necessarily in a standardised format that could be understood by the application layer in the <i>receiving</i>&nbsp;computer. The presentation layer translates the data into a standardised format, as well as handling any encryption, compression or other transformations to the data. With this complete, the data is passed down to the session layer.</p><p><u>Layer 5 -- Session</u><u>:</u></p><p>When the session layer receives the correctly formatted data from the presentation layer, it looks to see if it can set up a connection with the other computer across the network. If it can't then it sends back an error and the process goes no further. If a session <i>can</i>&nbsp;be established then it's the job of the session layer to maintain it, as well as co-operate with the session layer of the remote computer in order to synchronise communications. The session layer is particularly important as the session that it creates is unique to the communication in question. This is what allows you to make multiple requests to different endpoints simultaneously without all the data getting mixed up (think about opening two tabs in a web browser at the same time)! When the session layer has successfully logged a connection between the host and remote computer the data is passed down to Layer 4: the transport Layer.</p><p><u>Layer 4 -- Transport</u><u>:</u></p><p>The transport layer is a very interesting layer that serves numerous important functions. Its first purpose is to choose the protocol over which the data is to be transmitted. The two most common protocols in the transport layer are TCP (<b>T</b>ransmission <b>C</b>ontrol <b>P</b>rotocol) and UDP (<b>U</b>ser <b>D</b>atagram<b> P</b>rotocol); with TCP the transmission is <i>connection-based</i> which means that a connection between the computers is established and maintained for the duration of the request. This allows for a reliable transmission, as the connection can be used to ensure that the packets <i>all</i>&nbsp;get to the right place. A TCP connection allows the two computers to remain in constant communication to ensure that the data is sent at an acceptable speed, and that any lost data is re-sent. With UDP, the opposite is true; packets of data are essentially thrown at the receiving computer -- if it can't keep up then that's <i>its </i>problem (this is why a video transmission over something like Skype can be pixelated if the connection is bad). What this means is that TCP would usually be chosen for situations where accuracy is favoured over speed (e.g. file transfer, or loading a webpage), and UDP would be used in situations where speed is more important (e.g. video streaming).</p><p>With a protocol selected, the transport layer then divides the transmission up into bite-sized pieces (over TCP these are called <i>segments</i>, over UDP they're called <i>datagrams</i>), which makes it easier to transmit the message successfully.&nbsp;</p><p><u>Layer 3 -- Network:</u></p><p>The network layer is responsible for locating the destination of your request. For example, the Internet is a huge network; when you want to request information from a webpage, it's the network layer that takes the IP address for the page and figures out the best route to take. At this stage we're working with what is referred to as <i>Logical </i>addressing (i.e. IP addresses) which are still software controlled. Logical addresses are used to provide order to networks, categorising them and allowing us to properly sort them. Currently the most common form of logical addressing is the IPV4 format, which you'll likely already be familiar with (i.e 192.168.1.1 is a common address for a home router).</p><p><u>Layer 2 -- Data Link:</u></p><p>The data link layer focuses on the <i>physical </i>addressing of the transmission. It receives a packet from the network layer (that includes the IP address for the remote computer) and adds in the physical (MAC) address of the receiving endpoint. I<span style="font-size:1rem">nside every network enabled computer is a&nbsp;</span><span style="font-size:1rem;font-weight:bolder">N</span><span style="font-size:1rem">etwork&nbsp;</span><span style="font-size:1rem;font-weight:bolder">I</span><span style="font-size:1rem">nterface&nbsp;</span><span style="font-size:1rem;font-weight:bolder">C</span><span style="font-size:1rem">ard (NIC) which comes with a unique MAC (</span><span style="font-size:1rem;font-weight:bolder">M</span><span style="font-size:1rem">edia&nbsp;</span><span style="font-size:1rem;font-weight:bolder">A</span><span style="font-size:1rem">ccess&nbsp;</span><span style="font-size:1rem;font-weight:bolder">C</span><span style="font-size:1rem">ontrol) address to identify it. </span></p><p><span style="font-size:1rem">MAC addresses are set by the manufacturer and literally burnt into the card; they can't be changed -- although they&nbsp;</span><i>can</i><span style="font-size:1rem">&nbsp;be spoofed. When information is sent across a network, it's actually the physical address that is used to identify where exactly to send the information.</span></p><p><span style="font-size:1rem"> </span></p><p><span style="font-size:1rem">Additionally, it's also the job of the data link layer to present the data in a format suitable for transmission.</span></p><p><span style="font-size:1rem">The data link layer also serves an important function when it receives data, as it checks the received information to make sure that it hasn't been corrupted during transmission, which could well happen when the data is transmitted by layer 1: the physical layer. </span></p><p><u>Layer 1 -- Physical:</u></p><p>The physical layer is right down to the hardware of the computer. This is where the electrical pulses that make up data transfer over a network are sent and received. It's the job of the physical layer to convert the binary data of the transmission into signals and transmit them across the network, as well as receiving incoming signals and converting them back into binary data.</p><hr>

<div class="room-task-desc">
            <div class="room-task-desc-data"> <p style="margin-bottom:1rem">As the data is passed down each layer of the model, more information containing details specific to the layer in question is added on to the start of the transmission. As an example, the header added by the Network Layer would include things like the source and destination IP addresses, and the header added by the Transport Layer would include (amongst other things) information specific to the protocol being used.&nbsp;<span style="font-size:1rem">The data link layer also adds a piece on at the&nbsp;</span><i>end</i><span style="font-size:1rem">&nbsp;of the transmission, which is used to verify that the data has not been corrupted on transmission; this also has the added bonus of increased security, as the data can't be intercepted and tampered with without breaking the trailer.&nbsp;</span><span style="font-size:1rem">This whole process is referred to as&nbsp;</span><i>encapsulation;&nbsp;</i><span style="font-size:1rem">the process by which data can be sent from one computer to another.</span></p><p style="margin-bottom:1rem"><img alt="Encapsulation process" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/02/image.jpeg" style="width:869px;float:none"></p><p style="margin-bottom:1rem">Notice that the encapsulated data is given a different name at different steps of the process. In layers 7,6 and 5, the data is simply referred to as data. In the transport layer the encapsulated data is referred to as a segment or a datagram (depending on whether TCP or UDP has been selected as a transmission protocol). At the Network Layer, the data is referred to as a packet. When the packet gets passed down to the Data Link layer it becomes a frame, and by the time it's transmitted across a network the frame has been broken down into bits.</p><p style="margin-bottom:1rem">When the message is received by the second computer, it reverses the process -- starting at the physical layer and working up until it reaches the application layer, stripping off the added information as it goes. This is referred to as&nbsp;<i>de-encapsulation.&nbsp;</i>As such you can think of the layers of the OSI model as existing inside every computer with network capabilities. Whilst it's not actually as clear cut in practice, computers all follow the same process of encapsulation to send data and de-encapsulation upon receiving it.</p><p style="margin-bottom:1rem">The processes of encapsulation and de-encapsulation are very important -- not least because of their practical use, but also because they give us a standardised method for sending data. This means that all transmissions will consistently follow the same methodology, allowing any network enabled device to send a request to any other reachable device and be sure that it will be understood -- regardless of whether they are from the same manufacturer; use the same operating system; or any other factors.<br></p></div>
        </div>
<div class="room-task-desc">
            <div class="room-task-desc-data"> <p><span style="font-size:1rem">The TCP/IP model is, in many ways, very similar to the OSI model. It's a few years older, and serves as the basis for real-world networking.&nbsp;</span><span style="font-size:1rem">The TCP/IP model consists of four layers: Application, Transport, Internet and Network Interface. Between them, these cover the same range of functions as the seven layers of the OSI Model.</span></p><p><img alt="The layesrs of the TCP/IP model: Application, Transport,Internet, Network Interface" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/02/image-4.png" style="width:153px"></p><p><i><b>Note: </b>Some recent sources split the TCP/IP model into five layers -- breaking the Network Interface layer into Data Link and Physical layers (as with the OSI model). This is accepted and well-known; however, it is not officially defined (unlike the original four layers which are defined in RFC1122). It's up to you which version you use -- both are generally considered valid.</i><br></p><p>You would be justified in asking why we bother with the OSI model if it's not actually used for anything in the real-world. The answer to that question is quite simply that the OSI model (due to being less condensed and more rigid than the TCP/IP model) tends to be easier for learning the initial theory of networking. <br></p><p>The two models match up something like this:</p><p><img alt="Comparison between the TCP/IP and OSI models." src="https://muirlandoracle.co.uk/wp-content/uploads/2020/02/image-3.png" style="width:259px"></p><p>The processes of encapsulation and de-encapsulation work in exactly the same way with the TCP/IP model as they do with the OSI model. At each layer of the TCP/IP model a header is added during encapsulation, and removed during de-encapsulation.</p><hr><p>Now let's get down to the practical side of things.</p><p>A layered model is great as a visual aid -- it shows us the general process of how data can be encapsulated and sent across a network, but how does it actually happen?</p><p>When we talk about TCP/IP, it's all well and good to think about a table with four layers in it, but we're actually talking about a suite of protocols -- sets of rules that define how an action is to be carried out. TCP/IP takes its name from the two most important of these: the <b>T</b>ransmission <b>C</b>ontrol <b>P</b>rotocol (which we touched upon earlier in the OSI model) that controls the flow of data between two endpoints, and the <b>I</b>nternet <b>P</b>rotocol, which controls how packets are addressed and sent. There are many more protocols that make up the TCP/IP suite; we will cover some of these in later tasks. For now though, let's talk about TCP.</p><p>As mentioned earlier, TCP is a <i>connection-based</i> protocol. In other words, before you send any data via TCP, you must first form a stable connection between the two computers. The process of forming this connection is called the <i>three-way handshake</i>. </p><p>When you attempt to make a connection, your computer first sends a special request to the remote server indicating that it wants to initialise a connection. This request contains something called a <i>SYN</i> (short for <i>synchronise</i>) bit, which essentially makes first contact in starting the connection process. The server will then respond with a packet containing the SYN bit, as well as another "acknowledgement" bit, called <i>ACK</i>. Finally, your computer will send a packet that contains the ACK bit by itself, confirming that the connection has been setup successfully. With the three-way handshake successfully completed, data can be reliably transmitted between the two computers. Any data that is lost or corrupted on transmission is re-sent, thus leading to a connection which appears to be lossless.</p><p><img alt="The three way handshake" style="width:50%" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/03/image-2.png"></p><p><br></p><p><img alt="Frank Syn-acktra -- humour value only" style="width:50%" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/02/syn-acktra.jpeg"></p><p><i>(Credit Kieran Smith, Abertay University)</i></p><p>We're not going to go into exactly <i>how</i>&nbsp;this works on a step-to-step level -- not in this room at any rate. It is sufficient to know that the three-way handshake must be carried out before a connection can be established using TCP.</p><hr><p><b><u>History:</u></b></p><p>It's important to understand exactly <i>why</i>&nbsp;the TCP/IP and OSI models were originally created. To begin with there was no standardisation -- different manufacturers followed their own methodologies, and consequently systems made by different manufacturers were completely incompatible when it came to networking. The TCP/IP model was introduced by the American DoD in 1982 to provide a standard -- something for all of the different manufacturers to follow. This sorted out the inconsistency problems. Later the OSI model was also introduced by the International Organisation for Standardisation (<a href="https://www.iso.org/home.html" target="_blank">ISO</a>); however, it's mainly used as a more comprehensive guide for learning, as the TCP/IP model is still the standard upon which modern networking is based.</p></div>
        </div>
<div class="room-task-desc-data"> <p>

At this stage, hopefully all of the theory has made sense and you now understand the basic models behind computer networking. For the rest of the room we're going to be taking a look at some of the command line networking tools that we can use in practical applications. Many of these tools do work on other operating systems, but for the sake of simplicity, I'm going to assume that you're running Linux for the rest of this room. The first tool that we're going to look at will be the <code>ping</code> command.</p><hr><p>

The ping command is used when we want to test whether a connection to a remote resource is possible. Usually this will be a website on the internet, but it could also be for a computer on your home network if you want to check if it's configured correctly. Ping works using the ICMP protocol, which is one of the slightly less well-known TCP/IP protocols that were mentioned earlier. The ICMP protocol works on the Network layer of the OSI Model, and thus the Internet layer of the TCP/IP model. The basic syntax for ping is <code>ping &lt;target&gt;</code>. In this example we are using ping to test whether a network connection to Google is possible:</p><p><img alt="Pinging Google -- it is possible" style="width:507px" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/03/image-14.png"></p><p>

Notice that the ping command actually returned the IP address for the Google server that it connected to, rather than the URL that was requested. This is a handy secondary application for ping, as it can be used to determine the IP address of the server hosting a website. One of the big advantages of ping is that it's pretty much ubiquitous to any network enabled device. All operating systems support it out of the box, and even most embedded devices can use ping!<br>

</p><p>Have a go at the following questions. Any questions about syntax can be answered using the man page for ping (<code>man ping</code> on Linux).</p></div>
<div class="room-task-desc">
            <div class="room-task-desc-data"> <p>

The logical follow-up to the ping command is 'traceroute'. Traceroute can be used to map the path your request takes as it heads to the target machine.<br><br>The internet is made up of many, many different servers and end-points, all networked up to each other. This means that, in order to get to the content you actually want, you first need to go through a bunch of other servers. Traceroute allows you to see each of these connections -- it allows you to see every intermediate step between your computer and the resource that you requested. The basic syntax for traceroute on Linux is this: <code>traceroute &lt;destination&gt;</code></p><p>By default, the Windows traceroute utility (<code>tracert</code>) operates using the same ICMP protocol that ping utilises, and the Unix equivalent operates over UDP. This can be altered with switches in both instances.</p><p><img alt="Performing a traceroute to Google.com" style="width:910px" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/03/image-15.png"></p><p>You can see that it took 13 hops to get from my router (<code>\_gateway</code>) to the Google server at 216.58.205.46</p><p>Now it's your turn. As with before, all questions about switches can be answered with the man page for traceroute<br>(<code>man traceroute</code>).<br></p></div>

</div>
<div class="room-task-desc">
            <div class="room-task-desc-data"> <p>Domain Names -- the unsung saviours of the internet.</p><p>Can you imagine how it would feel to remember the IP address of every website you want to visit? Horrible thought.</p><p>Fortunately, we've got domains.</p><p>We'll talk a little bit more about how this works in the next task, but for now suffice to know that a domain translates into an IP address so that we don't need to remember it (e.g. you can type tryhackme.com, rather than the TryHackMe IP address). Domains are leased out by companies called Domain Registrars. If you want a domain, you go and register with a registrar, then lease the domain for a certain length of time.&nbsp;</p><p>Enter Whois.</p><p>Whois essentially allows you to query who a domain name is registered to. In Europe personal details are redacted;&nbsp;<span style="font-size:1rem">however, elsewhere you can potentially get a great deal of information from a whois search.</span></p><p>There is a <a href="https://www.whois.com/whois/" target="_blank">web version</a>&nbsp;of the whois tool if you're particularly averse to the command line. Either way, let's get started!</p><p><i>(Note: You may need to install whois before using it. On Debian based systems this can be done with </i><code>sudo apt update &amp;&amp; sudo apt-get install whois</code><i>)</i></p><p>Whois lookups are very easy to perform. Just use&nbsp;<code>whois &lt;domain&gt;</code>&nbsp;to get a list of available information about the domain registration:</p><p><img style="width:100%" alt="Performing a whois lookup on bbc.co.uk" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/03/image-16.png"></p><p>This is comparatively a very small amount of information as can often be found. Notice that we've got the domain name, the company that registered the domain, the last renewal, and when it's next due, and a bunch of information about nameservers (which we'll look at in the next task).</p><p>Your Turn</p></div>
        </div>
<div class="room-task-desc">
            <div class="room-task-desc-data"> <p>We talked about domains in the previous task -- now lets talk about how they work.</p>
<p>Ever wondered how a URL gets converted into an IP address that your computer can understand? The answer is a TCP/IP protocol called DNS (<strong>D</strong>omain <strong>N</strong>ame <strong>S</strong>ystem).</p>
<p>At the most basic level, DNS allows us to ask a special server to give us the IP address of the website we're trying to access. For example, if we made a request to www.google.com, our computer would first send a request to a special DNS server (which your computer already knows how to find). The server would then go looking for the IP address for Google and send it back to us. Our computer could then send the request to the IP of the Google server.</p>
<hr>
<p><span class="size" style="font-size:1rem">Let's break this down a bit.</span></p>
<p>You make a request to a website. The first thing that your computer does is check its local "<b><i><a href="https://www.ionos.co.uk/digitalguide/server/configuration/hosts-file/" target="_blank">Hosts</a> File</i></b>" to see if an explicit IP-&gt;Domain mapping has been created. This is an older system than DNS and much less commonly used in modern environments; however, it still takes precedence in the search order of most operating systems. If no mapping has been manually created, the computer then checks its local DNS cache to see if it already has an IP address stored for the website; if it does, great. If not, it goes to the next stage of the process.</p>
<p>Assuming the address hasn't already been found, your computer will then send a request to what is known as a <em>recursive</em>&nbsp;DNS server. These will automatically be known to the router on your network. Many Internet Service Providers (ISPs) maintain their own recursive servers, but companies such as Google and OpenDNS also control recursive servers. This is how your computer automatically knows where to send the request for information: details for a recursive DNS server are stored in your router or computer. This server will also maintain a cache of results for popular domains; however, if the website you've requested isn't stored in the cache, the recursive server will pass the request on to a <em>root name</em>&nbsp;server.</p>
<p>Before 2004 there were precisely 13 root name DNS servers in the world. These days there are many more; however, they are still accessible using the same 13 IP addresses assigned to the original servers (balanced so that you get the closest server when you make a request). The root name servers essentially keep track of the DNS servers in the next level down, choosing an appropriate one to redirect your request to. These lower level servers are called <em>Top-Level</em>&nbsp;<em>Domain</em>&nbsp;servers.</p>
<p>Top-Level Domain (TLD) servers are split up into extensions. So, for example, if you were searching for tryhackme<b>.com</b> your request would be redirected to a TLD server that handled <code>.com</code> domains. If you were searching for bbc<b>.co.uk</b> your request would be redirected to a TLD server that handles&nbsp;<code>.co.uk</code>&nbsp;domains. As with root name servers, TLD servers keep track of the next level down: <em>Authoritative name servers</em>. When a TLD server receives your request for information, the server passes it down to an appropriate Authoritative name server.</p>
<p>Authoritative name servers are used to store DNS records for domains directly. In other words, every domain in the world will have its DNS records stored on an Authoritative name server somewhere or another; they are the source of the information. When your request reaches the authoritative name server for the domain you're querying, it will send the relevant information back to you, allowing your computer to connect to the IP address behind the domain you requested.</p>
<hr>
<p><span class="size" style="font-size:1rem">When you visit a website in your web browser this all happens automatically, but we can also do it manually with a tool called&nbsp;</span><code>dig</code><span class="size" style="font-size:1rem">&nbsp;. Like ping and traceroute, dig should be installed automatically on Linux systems.</span></p>
<p><span class="size" style="font-size:1rem">Dig allows us to manually query recursive DNS servers of our choice for information about domains:</span><br>
<code>dig &lt;domain&gt; @&lt;dns-server-ip&gt;</code><span class="size" style="font-size:1rem"></span></p>
<p>It is a very useful tool for network troubleshooting.</p>
<p><img alt="Performing a DIG DNS lookup on google.com" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/03/dig-demo.png"><span class="size" style="font-size:1rem"></span></p>
<p>This is a <em>lot</em>&nbsp;of information. We're currently most interested in the <code>ANSWER</code>&nbsp;section for this room; however, taking the time to learn what the rest of this means is a very good idea. In summary, that information is telling us that we sent it one query and successfully (i.e. No Errors) received one full answer -- which, as expected, contains the IP address for the domain name that we queried.</p>
<p>Another interesting piece of information that dig gives us is the TTL (<strong>T</strong>ime <strong>T</strong>o <strong>L</strong>ive) of the queried DNS record. As mentioned previously, when your computer queries a domain name, it stores the results in its local cache. The TTL of the record tells your computer when to stop considering the record as being valid -- i.e. when it should request the data again, rather than relying on the cached copy.</p>
<p>The TTL can be found in the second column of the answer section:</p>
<p><img alt="Results demonstrating that the TTL of the DNS record is 157" src="https://muirlandoracle.co.uk/wp-content/uploads/2020/03/TTL.png"></p>
<p>It's important to remember that TTL (in the context of DNS caching) is measured in <em>seconds,</em> so the record in the example will expire in two minutes and thirty-seven seconds.</p>
<p>Have a go at some questions about DNS and dig.</p>
</div>
        </div>
