# GitHub Documentation: Passive Information Gathering
Passive information gathering involves collecting information about a target system or organization without directly interacting with it. This technique is often used by security professionals to identify potential vulnerabilities or assess the security posture of a system.

## 1. Using Website Information

### 1.1 shodan.io
Explore the website [shodan.io](https://shodan.io) for publicly available information.

### 1.2 Google Hacking Database/Google Dork Cheatsheet
Explore the website [exploit-db.com](https://www.exploit-db.com/google-hacking-database) and [google-dork-cheatseet](https://gist.github.com/sundowndev/283efaddbcf896ab405488330d1bbc06) for Utilize Google hacking techniques to gather information.

### 1.3 Sitereport.Netcraft
Visit [sitereport.netcraft](https://sitereport.netcraft.com/) to gather information about the technology and infrastructure of a particular website.

### 1.4 Terminal Commands with Whois
Execute the following commands in the terminal:

```bash
ping website
whois ipaddress_website
```
The ping command can be used to check the connectivity to the website and determine its IP address. The whois command can be used to gather information about the IP address, including its owner, organization, and location.

## 2. Using Dirbuster by Terminal
### 2.1 Dirb
Dirbuster is a directory brute-forcing tool that can be used to find hidden directories and files on a website. The dirb -h command displays the help menu for Dirbuster. The dirb http://website command scans the specified website for hidden directories and files.

Use Dirbuster in the terminal with the following commands to identify hidden directories and files on a website:
```bash
dirb -h
dirb http://website
```
Search for hidden pages, for example, /admin.

## 3. Using Dirsearch by Terminal
Dirsearch is a web application security scanner that can be used to identify hidden files and directories on a website. The python3 dirsearch.py -u http://testphp.vulnweb.com/ -e php command scans the specified website for hidden files with the PHP extension.

### 3.1 Setup Dirsearch

Clone the Dirsearch repository:
```bash 
git clone https://github.com/maurosoria/dirsearch.git
cd dirsearch
```
### 3.2 Run Dirsearch
Execute Dirsearch with the following commands:
```bash 
python3 dirsearch.py -u http://testphp.vulnweb.com/ -e php
```
Identify hidden files, e.g., index.zip:
```
[21:37:55] 200 - 3KB - /index.zip
```
### 3.3 Download and Analyze
Download the identified file:
```
wget http://testphp.vulnweb.com/index.zip
```

Unzip the file:
```
unzip index.zip
```

Inspect the contents, for example, with less:
```
less index.php
```
### 3.4 Extract Backend Technology

Analyze the PHP file to determine the backend technology, for example:
```bash
<?PHP
if(isset($_COOKIE["login"])){
  $login = explode('/', $_COOKIE["login"]);
  $result = mysql_query("SELECT * FROM users WHERE uname='".$login[0]."' AND pass='".$login[1]."'");
  if ($row = mysql_fetch_array($result)){
    echo "<a href='logout.php'>Logout ".$row['uname']."</a>";
  }
}
?>
```
This PHP code snippet suggests that the backend technology is PHP and MySQL.

## Conclusion
Passive information gathering is a valuable technique for collecting information about a target system or organization. However, it is crucial to use it carefully and responsibly. Ensure that your objectives are legitimate and employ non-aggressive or damaging methods.

Here are some tips for using passive information gathering legally and responsibly:

1. Provide clear information about your objectives.
2. Use non-aggressive or damaging methods.
3. Exercise caution with the information you disclose.

By following these tips, you can employ passive information gathering safely and effectively.

