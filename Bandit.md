### Level 0 &rarr; Level 1  
Once connected to **bandit0**, the password for the next level can be found in the **readme** file in the home directory.
To display the content of the file, run the following command: **cat readme**  
  
![bandit00](./Img/Bandit/bandit00.png)  

    User: bandit1
    Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
      
-------------------------------------------------------------------
### Level 1 &rarr; Level 2  
After logging into **bandit1**, the password is stored in a file named "-". To view the contents of the file,
we need to specify the full path to it: **cat ./-**  
  
![bandit01](./Img/Bandit/bandit01.png)  
    
    User: bandit2  
    Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
      
-------------------------------------------------------------------
### Level 2 &rarr; Level 3
After logging into **bandi2**, the password is in a file in the home directory. The file name contains spaces, so to view the content
of the file, we need to escape the spaces using the back-slach escape character: **cat spaces\ in\ this\ filename**   
  
![bandit02](./Img/Bandit/bandit02.png)  

    User: bandit3  
    Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx  

-------------------------------------------------------------------
### Level 3 &rarr; Level 4
As indicated on the website, the password is stored in a hidden file in the **inhere** directory, so I performed the following actions:  
- Change location to the **inhere** directory: **cd inhere**  
- Display directory content, including hidden directories and files: **ls -a**  
- Display content of the hidden file: **cat ...Hiding-From-You**  

![bandit03](./Img/Bandit/bandit03.png)  

    User: bandit4
    Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

-------------------------------------------------------------------
### Level 4 &rarr; Level 5
Once connected to **bandit4**, the password is stored in the only human-readable file in the **inhere** directory (as mentioned
on the website). I changed the location to **inhere** directory and listed the contents of the directory, I see that there are
many files starting with **-file** followed by a number, in order to identify the human-readable file, I executed this command
which tells me the type of each file: <strong>file ./*</strong> . I can see that the file **-file07** is the right one, so I printed its contents.
  
![bandit04](./Img/Bandit/bandit04.png)  

    User: bandit5
    Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
  
-------------------------------------------------------------------
### Level 5 &rarr; Level 6
The instructions on the website clearly indicated that the password is stored somewhere in the **inhere** directory in a file 
with the following characteristics:  
- human-readable
- 1033 bytes in size
- not executable   
  
Here are the steps I followed:  
- Find the file in the current directory with a size of 1033 bytes with the following command: **du -ab | grep 1033**
- Check file permissions, it must not be executable: **ls -l inhere/maybehere07/.file02**
- Check whether the file contains human-readable data (text): **file inhere/maybehere07/.file02**

![bandit05](./Img/Bandit/bandit05.png)  

    User: bandit6
    Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
  
-------------------------------------------------------------------
### Level 6 &rarr; Level 7
As explained on the website, the password for the next level is stored somewhere on the server in a file with the following properties:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

To find the required file, we need to use the **find** command, starting the search from the **root** directory (/), specifying all properties in the options and redirecting access errors to the null device in order to obtain a clean, concise result as shown in the picture below:  

![bandit6](./Img/Bandit/bandit06.png)  

    User: bandit7
    Password: z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S  
  
------------------------------------------------------------------
### Level 7 &rarr; Level 8
The password for the next level is in the **data.txt** file next to the word **millionth**.  
I printed the line containing the word **millionth** using the **grep** command.  
  
![bandit7](/Img/Bandit/bandit07.png)  
  
    User: bandit8
    Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

------------------------------------------------------------------
### Level 8 &rarr; Level 9
The password is in a file in the home directory named **data.txt**, the file contains many lines but the password is the only line of text that appears only once. I therefore sorted the file in ascending alphanumerical order, then printed only the unique lines, obtaining an output of a single line containing the password:  
  
![bandit8](/Img/Bandit/bandit08.png)

    User bandit9
    Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
  
------------------------------------------------------------------
### Level 9 &rarr; Level 10
The password is located in the file **data.txt**, which doesn't contain text but data, as you can see by executing the following command: **file data.txt**, so we need to use the **strings** command to print all the printable characters in this file, then we need to grep the lines containing the password pattern ***preceeded by several **=** characters***, which means that the line containing the password contains several **=** characters (2 or more) followed by the actual password, it is made up of numbers and letters (upper and lower case): **grep -E "={2,} ?[[:alnum]]+"**  
  
![bandit9](/Img/Bandit/bandit09.png)  
  
    User: bandit10  
    Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey  
  
------------------------------------------------------------------
### Level 10 &rarr; Level 11
As mentioned on the website, the password is stored in the **data.txt** file, which contains **base64-encoded** data, as you can see after running the **cat** command. To decode the data and obtain the password, simply run the following command: **base64 -d data.txt**  
  
![bandit10](/Img/Bandit/bandit10.png)  
  
    User: bandit11
    Password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
  
------------------------------------------------------------------
### Level 11 &rarr; Level 12
The password is in the file **data.txt** in the home directory, the file contains a single line of text, all the characters are rearranged to hide the actual password by rotating the upper and lower case letters by 13 positions. To reverse the order and find the password, we'll use the **tr** command and replace each character with the corresponding character in the next set of 13 characters of the alphabet, for example, **a** will be replaced by **n** and **N** by **A**: **cat data.txt | tr "a-mA-Mn-zN-Z" "n-zN-Za-mA-M"**  
  
![bandit11](/Img/Bandit/bandit11.png)  
  
    User: bandit12
    Password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
  
-----------------------------------------------------------------
### Level 12 &rarr; Level 13
The instructions indicate that the password is stored in a file called **data.txt** in the home directory, which is a hexdump of a file that has been repeatdly compressed.  
To solve this problem and decode the file, we need to decompress it multiple times. But first, we'll create a temporary folder and copy **data.txt** file into it. To do this, we'll execute the following commands:  
- Create a temporary folder in the **/tmp** directory: **mktemp -d**  
- Copy **data.txt** file into the temporary folder: **cp data.txt /tmp/tmp.[id]**  
- Change the directory to the temporary folder: **cd /tmp/tmp.[id]**  
  
![bandit12_01](/Img/Bandit/bandit12_01.png)  
  
Convert the contents of the file into binary data using the following command: **xxd -r data.txt > data**, then check the file type obtained. As you can see, it's **gzip compressed data**. We need to add the **.gz** extension to the **data** file, then decompress it using the following command: **gzip -d data.gz**  
  
![bandit12_02](/Img/Bandit/bandit12_02.png)  
  

Check the data file type again, it's **bzip2 compressed data**, we'll rename the file by adding the **.bz2** extension, then decompress it again: **bzip2 -d data.gz**  
  
![bandt12_03](/Img/Bandit/bandit12_03.png)  
  
We'll repeat the same action, checking the file type **data**, then changing its name by adding the extension **.gz**, then decompressing it: **gzip -d data.gz**
  
![bandit12_04](/Img/Bandit/bandit12_04.png)  
  
After checking the file type again, it's a **tar archive**, as you can see, we'll extract the file directly: **tar -xf data**, then we'll obtain another file named **data5.bin**, and we'll continue on this pattern, if we get a tar file we extract it or if we get a compressed file, we decompress it until we finally get an ASCII file, then we print it to get the password for the next level:

![bandit12_05](/Img/Bandit/bandit12_05.png)  
  
    User: bandit13  
    Password: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn  
  
------------------------------------------------------------------------------------------------------
### Level 13 &rarr; Level 14
This level is very simple. All we have to do is connect to the local server to access user **bandit14**'s account via ssh using the private key in the file **sshkey.private** located in user **bandit13**'s home directory, so we run the following command: **ssh -p 2220 -i sshkey.private bandit14@localhost**  
  
![bandit13_01](/Img/Bandit/bandit13_01.png)  
  
Once we're logged in as **bandit14** user, we print the password file in the following location: **cat /etc/bandit_pass/bandit14**
  
![bandit13_02](Img/Bandit/bandit13_02.png)  
  
    User: bandit14
    Password: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
  
------------------------------------------------------------------------------------------------------
### Level 14 &rarr; Level 15
In this level, we'll use the **nc** command to obtain the password for the next level:  
 - **echo "MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS" | nc localhost 30000** 
   
In the above command, we've passed the password for the current level to the **nc** command, which will submit it to the local host on port 30000:  
  
![bandit14](/Img/Bandit/bandit14.png)  
  
    User: bandit15
    Password: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
  
-------------------------------------------------------------------------------------------------------
### Level 15 &rarr; Level 16  
The next level password can be obtained by submitting the current level password to **localhost** on port **30001** using SSL/TLS encryption. To do so, we need to use an SSL/TLS client using **openssl** command :  

    openssl command [options...] [parameters...]  

Browsing the man page, I found a command to create an SSL\TLS client **s_client**, we can specify the host and port to connect to as parameters:  
    
    openssl s_client localhost:30001

After executing the command, we receive an SSL/TLS certificate as output, the SSL/TLS handshake has been completed: 
  
![bandit15](/Img/Bandit/bandit15_01.png)  
  
we can now communicate with the server, it's waiting for us to enter a block of characters, I entered the password, and got the password for the next level:  
  
![bandit15](/Img/Bandit/bandit15_02.png)  
  
    User: bandit16
    Password: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
