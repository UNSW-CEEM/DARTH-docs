# Access via SSH and Scripts 

This option is for more **advanced researchers** with relatively solid Python (or similar) skills who need to query the database by their scripts and the web downloader is not powerful enough for their project requirements. **Undergraduate students are strongly advised to try the downloader first.** 

1. Generate a new ssh key pair on the computer you want to access the database from (see Appendix 1 and 2). 

2. Send to Nargess (n.nourbakhsh@unsw.edu.au): 

    - the contents of the “public key” (e.g. id_rsa.pub) 

    - the data you would like to have access to from below: 

    Tables of the Datasets: 

        - Ausgrid 300 Homes Solar Data 

        - PV Bushfire Data 

        - Solar Analytics Solar Data 

        - Victorian Consumers Data 

        - Energy Data Platform (by year/month) 

        - BOM (by zone) 

    Data Tables from UNSW Buildings: 

        - photovoltaics 

        - metadatapv 

        - metadataunitpv 

        - weather 

        - metadataunitsweather 

        - units 

        - versioninfo 

Your access to the server and database will be granted accordingly and access details and list of data views will be emailed to you. You will be able to connect to the server and database using the access details and query the data views like any database table (SQL query, etc.). 

## Appendix 1: Generating a New SSH Key Pair (Windows) 

1.In a command (CMD) window or in a PowerShell window, run:  

    *ssh-keygen*

2. You will be prompted with a few questions: 

    - `Enter file in which to save the key (/home/<user>/.ssh/id_rsa):  <you can just press enter here to accept the default* >`

    - `Enter passphrase (empty for no passphrase): <Enter a phrase that you will be sure to remember as you’ll need this each time you login**>`

    - `Enter same passphrase again: <Enter the phrase again to verify>`

    \* For the file location, if you are prompted to overwrite an existing file (and you still need your previously existing file), do NOT do that as you will wipe out any other SSH keys you may have. Instead enter a different file name, but be sure to record the full pathname for use later when initiating the SSH session. 

    ** The passphrase can contain any characters including spaces. You should keep a record of it: without the passphrase you will not be able to login using SSH. 

3. If you used the default file location, you should see 2 new files in the `/home/<user>/.ssh` folder: 

    - id_rsa 

    - id_rsa.pub 

    Open the id_rsa.pub file in a text editor and send the contents as plain text, as a .txt file, or just send the whole file. 

    Note: the .pub file is your public key and can be shared without any security concerns, but the other file contains your private key which you should always keep secret. The 2 files work together to provide secure access just for you. 

## Appendix 2: Generating a New SSH Key Pair (MacOS) 

1. In Finder, choose **Utilities** from the **Applications** folder. 

2. Find **Terminal** in the Utilities list. 

3. Open Terminal. 

4. Enter the following command in the Terminal window: 

    *ssh-keygen -t rsa*

5. Enter key to accept the default location. 

6. Type in a passphrase (you will need to repeat the passphrase a second time to continue). 

7. You will see the random art created by SSH key-gen command. 

8. Your private key is saved to the *id_rsa* file in the .ssh directory and is used to verify the public key you use. 

9.  Your public key is saved to the *id_rsa.pub.*

10. You can copy your public key by the following command: 

    *pbcopy < ~/.ssh/id_rsa.pub*