# OSINT-full-guide
Hey Folks! I made this repostory to share with you how I conduct a detailed OSINT investigation and to share my notes and checklist. We call these type of engagements INVESTIGATIONS or RESEARCHES not assesments, because you should NEVER interact directly with your target. Also I suggest you to open up the checklist and follow along with the explaination (you can find it in the usage folder)

DISCLAIMER: Only conduct an OSINT research if you have explicit permission to do so. Use the tools and techniques at your own responsability. I am not accountable for any possible damage you make.

# Business OSINT

First things first, sign a contract with the client. Only start you work when you have the legal parts covered.

After that research the company using Google, DuckDuckGo, Yandex to get context. What services/products they offer? Size of the company, possible geolocation, registry data?
In this phase you have to recollect all the socials of your target: websites, LinkedIn, Facebook page, Instagram...

Here you can find two great tools to see where a company was registered, the founders, addresses...etc

https://opencorporates.com/

https://www.aihitdata.com/

Using LinkedIn and the website of the company get a list about it's employees. Collect names, email-addresses, phone numbers, websites, everything. Don't worry if you did not find everything, later you will expand this list using additional tools. Using the newly obtained information and the one that you got from the registry you can easily recreate the chain of command of your target. I prefer to use Maltego, but use whatever graphing tool you like.

Download photos from the company's website and socials and extract metadata from them.

You can use https://imginn.com/ to download all the stories from Instagram.

Check for twitter users as well:

https://tinfoleak.com/

https://tweetbeaver.com/

https://socialbearing.com/

For Facebook I use this two tools: 

https://www.sowsearch.info/

https://intelx.io/tools?tab=facebook

For snapchat you can check snapchatmaps for geolocation: https://map.snapchat.com

If you obtained an address check it out on google maps and make some good screenshots about the location and it's surroundings. Look for security measures: badges to unlock electronic locks, installed video surveillance, fences, guards...etc

# Username and email OSINT

Check the company's website and it's socials for possible usernames, look for the links between them. Like if you have a Youtube account you may leave your twitter account in the description for people to follow you and vice versa. In my experience twitter usernames are the best, for looking up other accounts.

Normally, I use sherlock once I got a username for further enumeration: 

https://github.com/sherlock-project/sherlock 

Then I move to infoga and TheHarvester to enumerate additional addresses. I use the company's domain as a search parameter and I also look up the obtained usernames to see additional information. Search engines can block your IP if you make a big amount of searches in a short period of time, use VPN while using this tools.

https://github.com/laramies/theHarvester 

https://github.com/m4ll0k/Infoga 

After this you should have a list of usernames and email addresses. Make sure to verify them using email-checkers, I'll leave two here as an example:

https://email-checker.net/

https://www.verifyemailaddress.org/

So, you have some verified email accounts, check if there has been part of a data breach and check if you get the breached passwords. I use dehashed, It's pretty useful, but use whatever tool you can find.

https://www.dehashed.com/

# Website OSINT

Identify the IP address of the company's website. Use a simply ping command or whatever you like.

Paste the IP in one of the following sites to see if the target's website is the only one hosted on that IP address:

https://www.virustotal.com/gui/home/upload

https://dnsdumpster.com/

Check what is in the backend of the website. Look for CMS, databases, programming languages, plugins and their version number. After obtaining the version number you can look up for public exploits, this will give extra value to your report.

https://builtwith.com/

https://www.wappalyzer.com/

https://github.com/urbanadventurer/WhatWeb

If the only website hosted on the IP address belongs to your target, then you can do a quick nmap scan using an ONLINE tool. Never use the one you have on your VM, you can get into a lot of trouble!

https://nmap.online/

https://hackertarget.com/nmap-online-port-scanner/

Identify additional subdomains and enumerate them as you did before on the main domain:

https://github.com/aboul3la/Sublist3r

https://github.com/darryllane/Bluto

https://crt.sh/

Use a webproxy like BurpSuite or OWASP ZAP to click throught all the pages of a website and to see additional code.

https://portswigger.net/burp

https://www.zaproxy.org/

Use the waybackmachine to see the previous states of a website. You can find interesting things in the previous version of a domain. Make sure to check the source code and look for comments!

https://archive.org/web/

Finish the enumeration using Shodan or Cenys. These tools can identify vulnerabilites and any device connected to the Internet. The firewall of the company, IP cameras, smart fridges...etc

https://www.shodan.io/dashboard

https://censys.io/

If you are not satisfied with the results use Maltego and search for more information about the people, phone numbers, emails, domains...etc. Also, make a good graph about your findings using Maltego as you did with the chain of command.

Wrap everything up, make sure you have an email list, username list, good screenshots about your findings and write your report.Your report must contain the followings:

Cover page
Table of contents
Assesment Overview ((x was tasked by y to research z, this includes…etc))
Summary
Target, info about the target (domain-list, chain of command, phone number, list of usernames..etc)
Technical evidence (Here you put the technique you used, a link to the tool you used, additional notes and a screenshot about the findings.)
Recommendations (refer to security frameworks like NIST or MITRE.)
