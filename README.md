# GrooveRio-Stored-XSS
# tested on System version 3.2.1-b51
# tested on Groove Manage version 3.2.1


You are able to acheive Stored XSS via feature misuse on current and recent versions of Groove rio from opto22.

I have contacted them to report this vulnerability but they have labeled it as a feature so here is my writup on it. 

Step 1: Authenticate as a user. I did this by cracking weak credentials and then creating my own account as admin via /manage/accounts/users/new

Step 2: Browse to /manage/local/files/secured/

Step 3: select upload file button which which asks for the file you would like to upload and then uploads the file using /manage/api/v1/files/secured/rpc/create-file//<your file name>.html

the contents of my malicious HTML file are as follows.

"<html><script>alert("XSS")</script></html>"

Step 4: after uploading the malicious HTML file all you need to do is browse to the file using
/manage/api/v1/files/secured/rpc/get-file/<your file name>.html

Happy hacking!
