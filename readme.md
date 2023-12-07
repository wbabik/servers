---
editor_options:
  markdown:
    wrap: 72
output:
  html_document:
    df_print: paged
---

# Computer cluster info

Welcome! This repository contains information about computing and
storage resources available in the Institute of Environmental Sciences,
Faculty of Biology, Jagiellonian University. Please read it carefully
since it contains instructions how to get an access, reach and use the
available infrastructure.

# **Getting access**

To get an access to a given server you need to apply for it to the
cluster administrator:
[tomasz.ciaston\@uj.edu.pl](mailto:tomasz.ciaston@uj.edu.pl){.email}
Please specify for access to which machine you are applying (this has to
be fixed with your supervisor in advance). After you will be granted
access you will get an e-mail with login and password. Connection to the
servers is only possible via VPN (Virtual Private Network). Below you
will find information how to establish such connection. When you
sucesfully connect and log in to the server, please change your default
password (see below). If you will type your password wrongly 3 times your account
will be blocked and you wont be able to log in. In this situation please
contact the administrator.

# Connection via VPN

To connect to the servers one needs to start a VPN connection using
OpenVPN.

If you have yet not tested whether your account is active and whether
you can connect using OpenVPN - follow the istructions:\
1.	Please log on to  <https://orkan.bio.edu.pl/ipa/ui/> to change or
verify your password. Tutorial -\>  [How to change password using web
browser?](https://uj-campus.notion.site/5c6c78b2bd084e8abeb8664c6fcd99b4?v=4d96fc418e9e41088c2de2e5c74a7e52)\
2.	Start the OpenVPN connection according to the instructions. Tutorial
-\>  [How to connect to the molecol cluster network using
OpenVPN?](https://uj-campus.notion.site/2508eb0f22894133ac4047170750db40?v=b2d9ad84d27d4b4493d58ac03259bf78)\
3.	You can already log in to the servers using their local IP addresses,
remembering to keep the OpenVPN connection running.

# Infrastructure

**Servers**

There are 3 servers available at the moment. You will get an access to
one of them (or more if needed). Table below contains important info
like IP addressees that you will need to connect to them.

| Common name | IP address     | Port | Access service | HD   | RAM   | CPU | GPU      |
|-------------|----------------|------|----------------|------|-------|-----|----------|
| BUG         | 192.168.130.18 | 22   | ssh            | 68 T | 500 G | 149 | \-       |
| IPS         | 192.168.130.17 | 22   | ssh            | 96 T | 500 G | 96  | \-       |
| AZOR        | 192.168.130.16 | 22   | ssh            | 20 T | 250 G | 72  | Tesla T4 |
| FSM         | 192.168.130.11 | 22   | ssh            | 10 T | 500 G | 80  | \-       |

**Storage**

Servers are supposed to be our computing resources, NOT a long term
storage. To store the data that you are not currently using all servers
have access to the shared disk storage.

-   matrix (short term storage) has fast connection to machines - can be
    found in `/mnt/matrix` - this has 20TB.

-   qnap (long term storage) has slower connection to machines but
    provides more space - can be found in `/mnt/qnap` - this has 110TB.

If you are not using some of your files please transfer them there -
space is still available. Please, remember about compressing your files
while storing. Example commands for compression of all files in a
directory **`tar -cvzf name_of_output_file.tar.gz directory_name`** and
for decompression **`tar -xzvf file_to_decompress.tar.gz`**

# **How to connect to server & log in**

**Work in a command line mode**

*Windows*

To get connected to servers from the Windows machine Download
[PuTTy](https://www.putty.org/). When you run PuTTy for the first time
you need to configure new connection thus:

1.  Go to `Translation`, and select Remote character set: **UTF-8**.

2.  Go to `Session` and enter public **IP address** of the server.

3.  Select **SSH** protocol and enter server **port**.

    ![](PuTTy.png)

The above settings can be saved under any name (e.g. name of the
machine) and used for later connections.

Connect to the remote server by clicking `Open`. When connecting from a
given computer for the first time, you'll see the warning. Click: `Yes`.
Next you will be asked to enter your login and password. After you do it
you can start working on the remote server in the text terminal mode!

*MacOS i Linux*

1.  Open terminal.
2.  Enter the command
    **`ssh -p [server port] [username]@[domain name or public IP address]`**
    and press Enter (as given in the table above!).
3.  When prompted for a password, enter the appropriate information.

*Mobile (iOS/Android)*

1.  Download and install the Termius app:
    [**https://termius.com/**](https://termius.com/).
2.  Open the app and add a new server. Enter the domain name or public
    IP address, user name and password.
3.  Click on the newly added server to connect to it.

**File transfer**

Files from your local computer to servers can be transferred using:

-   [WinScp](https://winscp.net/eng/download.php) - relatively easy to
    use but slow

-   [FileZilla](https://filezilla-project.org/) -- slightly more
    difficult to use but faster

-   scp - command line way to copy files **between servers**

Unless you often transfer large number of files, there are not real
differences between them except of the user interface. In each you have
to first establish connection giving you credentials (as with PuTTy).

# Communication

-   Calendar

We have Google calendar
[molecol_cluster](https://calendar.google.com/calendar/u/0?cid=aG1jZjQ4bHJjYXAzdmZwbzRxaGFrM2U3cGdAZ3JvdXAuY2FsZW5kYXIuZ29vZ2xlLmNvbQ)
to schedule bigger jobs. To be added to it please contact one of:
[krystyna.brzyska\@gmail.com](mailto:krystyna.brzyska@gmail.com){.email},
[p.lukasik\@gmail.com](mailto:p.lukasik@gmail.com){.email},
[zielinski.piotr1987\@gmail.com](mailto:zielinski.piotr1987@gmail.com){.email}
or [w.babik76\@gmail.com](mailto:w.babik76@gmail.com){.email}.

Please, put the info about your jobs (big - more than 10 cores or 50 G
RAM, lasting more than an hour) in the calendar, so other people can
schedule their work accordingly. If anybody wants to run something very
big (more than half machine) lasting more than a week, he/she should ask
others via mailing list if they don't have anything against using more
resources. It is of high importance that you book your slots in advance
and finish jobs on schedule. Otherwise, other people can't plan their
work efficiently. If you don't follow the rules, your access to
computing power might be restricted.

-   MS Teams

To communicate with administrator and other users you might also use Ms
Teams channel
[WB-IT](https://teams.microsoft.com/l/team/19%3atBv3ZlmLBDMl55G4y3IASAMyL2vpF5VRBOAhb_seY9Y1%40thread.tacv2/conversations?groupId=369d073a-a278-4a7f-ad2b-aa11dea62e0c&tenantId=eb0e26eb-bfbe-47d2-9e90-ebd2426dbceb)
One might ask cluster administrator or somebody from the above list to
be added to the channel.

-   Google mailing list

There is also mailing list molecol_cluster\@googlegroups.com which helps
the users to communicate for example if there is a need to book
substantial part of the infrastructure for a longer time. To be added
ask somebody from the above list.

-   For direct communication with the administrator use his e-mail:
    [tomasz.ciaston\@uj.edu.pl](mailto:tomasz.ciaston@uj.edu.pl){.email}

# Maintenance

Monday mornings are default service hours (7-10 am) - this is the time
when NO jobs should be running. If you have long lasting job which has
to run at that time, you should contact administrator in advance and ask
him to cancel the restart of a particular machine, if not your job might
be killed. Please do not abuse this possibility because it might affect
safety of our machines.

# Useful tools

**Midnight Commander**

While working in the terminal many people find helpful using file
manager -- the one installed on all servers is Midnight Commander. To
run it from anywhere just type **`mc`** in shell.

**htop**

htop is an interactive system-monitor process-viewer and
process-manager. It shows a frequently updated list of the processes
running on a computer, normally ordered by the amount of CPU usage; htop
provides a full list of processes running; htop uses color and gives
visual information about processor, swap and memory status; htop can
also display the processes as a tree. To run it from anywhere type
**`htop`** in shell.

**Conda**

On some servers multiple bio-informatics tools are pre-installed in
conda "bio" environment, including blast+, samtools, gatk etc. To
activate it, for the very first time, run: \*
**`/opt/miniconda3/dist/bin/conda init`**

You may need to close and restart your shell after running the command
below.

To activate the environment when you want to use it:
**`conda activate bio`**

Your prompt will change from:
(base) [user.name\@server.name]:~$
to:
(bio) [user.name\@server.name]:~$
eg. from `(base) jan.kowalski@azor:~$ ...` to `(bio) jan.kowalski@azor:~$ ...` 

See the list of software installed in conda bio, type: **`conda list`**

All programs are now available and can be run by typing their name in
the command prompt!

**Conda basics - instruction for beginners**

Note that any string below restricted by angle brackets ("\<" and "\>", included) should
be replaced with your personalized values. "Conda" serves as a tool to
create independent environments inside your server account. Think about
them as completely separated, specialized rooms inside which you can do
your work. They are used when you want to:

-   install the software requiring administrator permissions (inside
    your environment you are the admin)

-   install the software dependent on other software (conda often allows
    you to install all dependencies alongside with software of interest)

-   install other versions of the software than those already installed
    globally (scripts often use specific versions of programming
    language or packages)

-   be sure your script will work despite any updates made globally
    share your script easily between servers without worrying about
    compatibility issues.

**Creation of the environment**

There are two ways of creating conda environments:

-   blank, novel environments in which by default you can use all global
    software unless you replace it with the other version

    **`conda create -n <environment_name>`**

    If you want to install any specific software from scratch you can
    type:
    **`conda create -n <environment_name> <software1_name>=<version1_number> <software2_name>=<version2_number>`**

    Shared environments with defined dependencies and their version
    numbers. It is often the case of scripts shared via some code
    repositories but not included in conda official libraries. This
    method requires a file with a ".yml" extension.

    **`conda env create -f <file.yml>`**

        Note that the name of the created environment is taken from the first line of the „.yml” file.

    **Activation of the environment**

    Any time you want to work within your environment, it needs to be
    activated. Otherwise you cannot use any software installed inside
    it. Do it by typing: `conda activate <environment_name>` If you want
    to use software installed in the other environment you need to
    perform nested activation. Imagine, you work on azor and you want to
    create your own environment but still be able to use software
    installed inside bio environment. Then type:
    `conda activate bio conda activate --stack <your_environment>`

-   Installation of the software inside the environment to see if given
    software/package (and/or given version) is available in conda
    library type: `conda search <software_name>`. All software included in
    conda library can be installed via:
    `conda install <software1_name> <software2_name> ...`.
    You can also specify a version of any package:
    `conda install <software1_name>=<software1_version>`. Note that it is
    highly recommended to install software after activation of the
    environment. Also, bear in mind that any software not included in
    conda library can be installed manually after environment
    activation. Sometimes, however, you would need to install it in a
    specific environmental path. If you encounter that problem, follow
    the links at the end of instruction.

-   Deactivation of the environment `conda deactivate`

-   Typical workflow when you want to reuse the environment use
    `conda activate <environment_name>` ... your work ... `conda deactivate`

-   Removing the environment `conda remove --name <environment_name>`
    or `conda remove --all`

-   Useful links if you encounter any problem or you would like to use ...
