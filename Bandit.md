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
  
> openssl command [options...] [parameters...]  
  
Browsing the man page, I found a command to create an SSL\TLS client (**s_client**), we can specify the host and port to connect to as parameters:  
    
    openssl s_client localhost:30001  
  
After executing the command, we first received an SSL/TLS certificate from the server, then the SSL/TLS handshake took place:  
  
![bandit15_01](/Img/Bandit/bandit15_01.png)  
  
We can now communicate with the server, it's waiting for us to enter a block of characters, I entered the password, and got the password for the next level:  
  
![bandit15_02](/Img/Bandit/bandit15_02.png)  
  
    User: bandit16
    Password: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
-------------------------------------------------------------------------------------------------------
### Level 16 &rarr; Level 17
As the website indicates, top-level credentials can be obtained by sending the current password to **localhost** in the range of ports **31000** to **32000**.  
First, we need to scan the ports to find out which of these ports has a listening server, we'll do this using **nmap** tool :
    
    nmap -sV -p31000-32000 localhost
  
The above command will scan all ports from **31000** to **32000** and display the service running on each open port. See the result:
  
![bandit16_01](/Img/Bandit/bandit16_01.png)  
  
We can clearly see that 5 ports are in listening mode, 2 of them have SSL encryption, 31518 and 31790, the first has the echo service, which means it will return whatever I send to it. The second has an unknown service running, so let's take the only option we have:  
  
![bandit16_02](/Img/Bandit/bandit16_02.png)  
  
Now that we're connected in, let's submit the current password:  
  
![bandit16_03](/Img/Bandit/bandit16_03.png)  
  
We got KEYUPDATE, so I checked CONNECTED COMMANDS on the man page, and found that if **-quiet** or **-ign-eof** are given, every first letter of the submitted line will be interpreted as a command. The first letter of the password is “k”, this actually a command that will send a key update message to the server, hence the “KEYUPDATE” response. Let's try again, but this time we'll use **-quiet** option:  
  
![bandit16_04](/Img/Bandit/bandit16_04.png)  
  
Great! The credentials for the next level are in fact private keys:  
  
    User: bandit17
    Private key:    
        -----BEGIN RSA PRIVATE KEY-----
    MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
    imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
    Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
    DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
    JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
    x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
    KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
    J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
    d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
    YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
    vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
    +TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
    8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
    SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
    HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
    SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
    R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
    Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
    R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
    L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
    blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
    YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
    77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
    dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
    vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
    -----END RSA PRIVATE KEY-----

---------------------------------------------------------------------------------------
