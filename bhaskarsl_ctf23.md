# CTF CHALLENGE WRITEUP:DEVNULL
**Challenge Description:** we are given that the webpage that they have given keeps crashing and they have stored the error in the 
error file. they also have given that they will retrive the important files from the path `home/app/uploads` given in the webpage 
.

## **Approach:** 
 _**look for possible clues:**_ sumbit the path in the query box and look for possible clues in the webpage. then  you notice that
the URL has changed and it is showing that we can change the file value in the URL.if you want you can also just use the check path to 
check what is missing in the webpage(it will show that the file parameter is missing).you can also check the payloads which is provided in the
wiki.bi0s.in webpage .some important payloads are:

**(1)**../../../../etc/passwd/etc/issue (this is to check if there is any issue in the webpage)

**(2)**../../../../etc/passwd (this to get the general login passwords of the system which are stored in the passwds file )

_**try to find the source code:**_we just try to enter these payloads with `../` which is used to traverse to the previous path 
i.e. it is mostly used to go to the root directory first.we can assume there might be clues in the source code about the error file
then we can  check for the index file which contains the source code (normally the index files store these source codes). the common index 
file names for php and html are index.php and index.html , so we can assume that the common index filenames for node.js is  index.js
.after trying this in the path we dont get it. then if we check the challange again we notice that the they had given that they will
retrive the files using the path `home/app/uploads`.so we can assume that the index filname is related to the path . so we try both 
upload.js and `app.js`in the URL path.we then get the source code after we try for app.js.(`/home/app/app.js`)

_**try to find the error file path:**_ when we check the source code we get the that the code uses the error file path to access the  
error file and we can then try to trverse to that error file path (**errorfile path:** `/var/log/apache2/error.log`).after you traverse to that
error path you will get the flag that is stored in the error.log file
## **FLAG:** flag{XT8QARuDrO7+1EAx5VITKw==}
