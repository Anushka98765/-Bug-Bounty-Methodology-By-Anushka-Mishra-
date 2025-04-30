# -Bug-Bounty-Methodology-By-Anushka-Mishra-
🐞 Introduction to Bug Bounty Methodology
Bug Bounty is a program where companies reward security researchers for finding and responsibly disclosing security vulnerabilities in their systems. To succeed in bug bounty, you need a structured methodology—a repeatable approach to finding bugs.
1.📜** **Table of Contents-**

    * Reconnaissance Subdomain Enumeration & Initial Scanning
    * Discovery HTTP Probing & Asset Discovery
    * Enumeration Advanced Techniques & Parameter Discovery
    * Testing Vulnerability Assessment
    * Two-Eye Approach Explained in Detail
    * POC Creation Proof of Concept & Documentation 7
    * Reporting Final Report Preparation

**2- Reconnaissance and Subdomain Enumeration**
   1. Passive Subdomain Enumeration
🔧 Tools Used: Subfinder, GitHub Search

**Subfinder**
    Purpose: Rapid, passive discovery of subdomains
  
**Command:**
    subfinder -d target.com -silent -all -recursive -o subfinder_subs.txt
    
GitHub Search
    Purpose: Scanning repository contents for subdomains
    
 **Command:**
       github-subdomains -d target.com -t YOUR_GITHUB_TOKEN -o github_subs.txt
       
3. **Subdomain Status Check**
    Using httpx-toolkit
    Tool Installation
    sudo apt install httpx-toolkit
   
 **Command:**
          cat subdomains.txt | httpx-toolkit -ports 80,443,8080,8000,8888 -threads 200 > subdomains_alive.txt
             cat subdomains_alive.txt | wc -l
  4. URL Discovery
          Using Katana
          Tool Installation: Katana
**commands -**
      katana -u target.example.com -silent -jc -o katana_results.txt
      7. Open Redirect and LFI Discovery
         
 **5.Using gf**
    Tool Installation: gf
**commands-**

    cat allurls.txt | gf or | sed 's/=.*$/=/' | sort -u > open_redirect.txt
    cat allurls.txt | gf lfi | sed 's/=.*$/=/' | sort -u > lfi_output.txt
 6.. **Vulnerability Testing**
      Using loxs

      Tool Installation: loxs
      
**commands**
       cd loxs
       python3 loxs.py
       
 **7.Advanced Vulnerability Scanning**
      Using Nuclei

     Tool Installation: Nuclei
**commands-**
       cat js.txt | nuclei -t /home/aung/nuclei-templates/http/exposures/
       echo www.example.com | katana -ps | grep -E "\.js$" | nuclei -t /home/aung/nuclei-templates/http/exposures/ -c 30
      -E  "\.js$" | nuclei -t /home/aung/nuclei-templates/http/exposures/ -c 30
 
 8. **Directory Bruteforcing**
Using dirsearch

Tool Installation:

**commands-**
     sudo apt install dirsearch
     
 **Command:**
   dirsearch -u https://www.example.com -e      conf,config,bak,backup,swp,old,db,sql,asp,aspx,aspx~,asp~,py,py~,rb,rb~,php,php~,bak,bkp,cache,cgi,conf,csv,html,inc,jar,js,json,jsp,jsp~,lock,log,rar,old,sql,sql.gz,http://sql.zip,sql.tar.gz,sql~,swp,swp~,tar,tar.bz2,tar.gz,txt,wadl,zip,.log,.xml,.js.,.json

 **Conclusion**

   This comprehensive bug-hunting methodology equips you with the tools and techniques needed to uncover vulnerabilities effectively. By following these steps and using the    recommended tools, you can conduct thorough penetration tests and improve the security posture of your target systems.
    
    
