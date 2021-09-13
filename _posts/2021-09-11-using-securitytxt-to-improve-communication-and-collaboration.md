---
title: "Using security.txt to improve communication and collaboration with the infosec community"
date: 2021-09-11
author: Kristian Bodeholt
categories:
  - security
tags:
  - Community
  - Communication
  - Collaboration
  - Disclosure 
---

There have been multiple cases in Denmark where attempts to contact various danish security teams have had a bad outcome due to missing/unclear security disclosure policies and the lack of information on how to find a relevant points of security contact within a specific company.  

## Security disclosure gone wrong 

Take the case where a danish parent/hacker found a [security flaw](https://www.version2.dk/artikel/foraeldre-finder-banale-sikkerhedshuller-i-udbredt-it-system-til-boernehaver-247985) in a kiosk system used to check-in/out kids attendance in the kindergarten, that enabled him to see personal information on some of the kids that were registered in the system. The case went sour after he failed to get a contact to the security department of the system supplier and they ended up suing him due to - what seems to be a sub-optimal process from both parties. The common problem seems to be in these cases, that the companies in question does not have a proper process to effectively handle the disclosure situation.

This have been a continues [topic](https://www.version2.dk/blog/skal-man-offentliggoere-sikkerhedshul-1077263) over the years globally on how to get a hold of, and handle disclosure of security flaws to vendors, companies and organizations.  

[Danish EnergiCERT](https://energicert.dk/) has also recently reported that they have had a case where they needed to contact 10 of the biggest companies in order to warn about a security related finding.
>“None of the companies had the security.txt file in place. Therefore, we used quite a lot time to find the right people and worse was that we had to give up on some of the companies” says [Kenneth Jørgensen](https://www.linkedin.com/in/kennethbjerregaardjoergensen/) from EnergiCERT.  

For those unfamiliar with EnergiCERT – it's the Danish Energy Sectors Computer Emergency Response Team which handles high level incident response for the critical sector.  

Other times security researchers or security interested individuals might even give up and discard their findings without sharing them due to effort required to identify the contact point with the entity or due to the risk of possible legal actions against them, as entity's security disclosure policy is unknown.    

The new [proposed IETF draft]( https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-12) for security.txt sets out to help fix that. 

## Minimum required information 

The proposed standard require that you have a `security.txt` file within the entities site `.well-known` folder with at least a [contact point](https://tools.ietf.org/html/draft-foudil-securitytxt-12#section-3.5.3) in form an mail form/address and/or phone number for the entity's information security team. The last required element is information about when the security.txt information is to [expire]( https://tools.ietf.org/html/draft-foudil-securitytxt-12#section-3.5.5) so that validity of the information can be confirmed.

## Optional information 
* [Encryption]( https://tools.ietf.org/html/draft-foudil-securitytxt-12#section-3.5.4) - A link to a key which security researchers should use to securely communicate to the security team. 
* [Acknowledgments]( https://tools.ietf.org/html/draft-foudil-securitytxt-12#section-3.5.1) - A link to a web page where the entity can say thank you to security researchers who have helped the security team. 
* [Preferred-Languages]( https://tools.ietf.org/html/draft-foudil-securitytxt-12#section-3.5.8) - A comma-separated list of language codes that the entities security team can communicate in. 
* [Canonical]( https://tools.ietf.org/html/draft-foudil-securitytxt-12#section-3.5.2) - The URLs for accessing your security.txt file. It is important to include this if the entity is digitally signing the security.txt file, so that the location of the security.txt file can be digitally signed too 
* [Policy]( https://tools.ietf.org/html/draft-foudil-securitytxt-12#section-3.5.7) - A link to a policy detailing what security researchers should do before searching for or reporting security issues 
* [Hiring]( https://tools.ietf.org/html/draft-foudil-securitytxt-12#section-3.5.6) - A link to any security-related job openings within the entity organization. 

There is even a great security.txt generator on [https://securitytxt.org/](https://securitytxt.org/) to help generate a security.txt file. 
 
You should also take a look at [policymaker at disclose.io](https://policymaker.disclose.io/policymaker/introduction) which aims to create a "one-stop-shop" policy generator for anyone launching a vulnerability disclosure program and among other things generate a security.txt file. 

## Danish Security.txt hall of fame 

Disclaimer: the list is compiled from a scan on the 1st of September 2021, please feel free to do a pull request to this post/article to update the list.  

[TV2](https://tv2.dk/.well-known/security.txt)  
[Norlys](https://norlys.dk/.well-known/security.txt)  
[William Dam](https://www.williamdam.dk/security.txt)  
[Benns Rejser](https://benns.dk/.well-known/security.txt)  
[Google](https://google.dk/.well-known/security.txt)  
[EnergiCERT](https://energicert.dk/.well-known/security.txt)  
[Jyske Bank](https://jyskebank.dk/.well-known/security.txt)  
[VSec](https://vsec.dk/.well-known/security.txt)  

## What can we do as a community?  

Reach out to your local security department and inform them of the security.txt IETF draft and point them to https://securitytxt.org/ 
You can use this Danish/English template:   

**English Version**  

> To the IT security department at xxxx.  
>   
> I'm writing on behalf of a non-profit IT security community in Denmark called VSec, to inform about a new internet standard. The standard aims to create publicly available guidelines for structured contact to security departments in connection with the discovery of IT security-related vulnerabilities in companies, organisations and associations.  
>     
> If you are interested in knowing more, you can read the following article: [https://vsec.dk/using-securitytxt-to-improve-communication-and-collaboration/](https://vsec.dk/using-securitytxt-to-improve-communication-and-collaboration/) and the draft standard: [https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-12](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-12) or go directly to the free security.txt generator at [https://securitytxt.org/](https://securitytxt.org/) to create your security.txt file with information and guidelines for external contact to your security department.  
>   
> Yours sincerely,  
> The IT security community VSec in Denmark.  

**Danish Version**  

> Til IT-sikkerhedsafdelingen hos xxxx.  
>   
> Jeg skriver på vegne af et non-profit IT-sikkerheds fællesskab i Danmark kaldet VSec, for at informere om en ny internetstandard. Standarden har til formål at skabe offentligt tilgængelige retningslinjer for struktureret kontakt til sikkerhedsafdelinger i forbindelse med fund af IT-sikkerhedsrelaterede sårbarheder hos virksomheder, organisationer og foreninger.  
>  
>Hvis du er interesseret i at vide mere, kan du læse følgende artikel: [https://vsec.dk/using-securitytxt-to-improve-communication-and-collaboration/](https://vsec.dk/using-securitytxt-to-improve-communication-and-collaboration/) og denne draft standard: [https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-12](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-12) eller gå direkte til den gratis security.txt generator på [https://securitytxt.org/](https://securitytxt.org/) for at lave jeres security.txt fil med informationer og retningslinjer for ekstern kontakt til jeres sikkerhedsafdeling.  
>  
>Med venlig hilsen  
>IT-sikkerheds fællesskabet VSec i Danmark.
 
## History of hackers.txt and the new proposed IETF standard  
Interested in the history about how security.txt came to be and why it's a proposed standard today?  
You should checkout [this article about the history of the hackerstxt and securitytxt files](https://medium.com/takeaway-tech/the-history-of-the-hackerstxt-and-securitytxt-files-95c0a3be43a9) by [Ben Peachey](https://twitter.com/potherca). 

**This article was written by [Kristian Bodeholt](https://www.linkedin.com/in/kristianbodeholt/) on behalf of the VSec Community**.  
  
> A big thank you goes out to Jonas Smedegaard, Kenneth Jørgensen and Klaus Agnoletti for contributing to the community article, giving feedback/constructive criticism and in general just for being awesome.  

### Sources  
[https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-12](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-12)  
[https://securitytxt.org/](https://securitytxt.org/)  
[https://twitter.com/securitytxt](https://twitter.com/securitytxt)  
[https://en.wikipedia.org/wiki/Security.txt](https://en.wikipedia.org/wiki/Security.txt)  
[https://www.bleepingcomputer.com/news/security/security-txt-standard-proposed-similar-to-robots-txt/](https://www.bleepingcomputer.com/news/security/security-txt-standard-proposed-similar-to-robots-txt/)  
[https://blog.cloudflare.com/security-dot-txt/](https://blog.cloudflare.com/security-dot-txt/)  
[https://www.michalspacek.com/what-is-security.txt-and-why-you-should-have-one](https://www.michalspacek.com/what-is-security.txt-and-why-you-should-have-one)  
[https://disclose.io/](https://disclose.io/)  
[https://github.com/62726164/a-survey-of-security-dot-txt](https://github.com/62726164/a-survey-of-security-dot-txt)  
