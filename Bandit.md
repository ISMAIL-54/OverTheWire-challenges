### Level 0 &rarr; Level 1  
Once connected to **bandit0**, the password for the next level can be found in the **readme** file in the home directory.  
To display the contents of the file, run the following command: **cat readme**  
  
![bandit0](./Img/bandit/bandit0.png)

-------------------------------------------------------------------
### Level 1 &rarr; Level 2  
After logging into **bandit1**, the password is stored in a file named "-". To view the contents of the file,  
we need to specify the full path to it: **cat ./-**  
  
![bandit1](./Img/bandit/bandit1.png)

-------------------------------------------------------------------
### Level 2 &rarr; Level 3
After logging into **bandi2**, the password is in a file in the home directory. The file name contains spaces,  
so to view the content of the file, we need to escape the spaces using the back-slach escape character: **cat spaces\ in\ this\ filename**  
  
![bandit2](./Img/bandit/bandit2.png)
