# cyberEye

A supervised cybersecurity ML model capable of detecting whether a website is legitimate or a phishing website using the XGBoost classifier. The model employs Python 3.x for feature extraction.

## Dataset
The set of phishing URLs is collected from the open-source service called PhishTank. Legitimate URLs are obtained from the open datasets of the University of New Brunswick.

## Feature Extraction
The features extracted from the URL data fall into the following categories:

### Address Bar-based Features:
In this category, 9 features are extracted.

1. **IP Address in the URL (Have_IP):**
   - Checks for the presence of an IP address in the URL.
   - 1 (phishing) if an IP address is found, 0 (legitimate) otherwise.

2. **"@" Symbol in URL (Have_At):**
   - Checks for the presence of the '@' symbol in the URL.
   - 1 (phishing) if '@' is present, 0 (legitimate) otherwise.

3. **Length of URL (URL_Length):**
   - Computes the length of the URL.
   - 1 (phishing) if the length is greater than or equal to 54 characters, 0 (legitimate) otherwise.

4. **Depth of URL (URL_Depth):**
   - Computes the depth of the URL by counting the number of subpages in the URL based on '/'.

5. **Redirection "//" in URL (Redirection):**
   - Checks the presence of "//" in the URL, indicating redirection.
   - 1 (phishing) if "//" is found, 0 (legitimate) otherwise.

6. **"http/https" in Domain name (https_Domain):**
   - Checks for the presence of "http/https" in the domain part of the URL.
   - 1 (phishing) if present, 0 (legitimate) otherwise.

7. **Using URL Shortening Services “TinyURL” (Tiny_URL):**
   - Checks if the URL is using URL shortening services.
   - 1 (phishing) if using, 0 (legitimate) otherwise.

8. **Prefix or Suffix "-" in Domain (Prefix/Suffix):**
   - Checks the presence of '-' in the domain part of the URL.
   - 1 (phishing) if '-' is present, 0 (legitimate) otherwise.

### Domain-based Features:
In this category, 4 features are extracted.

9. **DNS Record availability (DNS_Record):**
   - Checks if the DNS record is empty or not found.
   - 1 (phishing) if empty or not found, 0 (legitimate) otherwise.

10. **Web Traffic (Web_Traffic):**
   - Measures the popularity of the website by determining the number of visitors and pages visited.
   - 1 (phishing) if the rank of the domain is less than 100,000, 0 (legitimate) otherwise.

11. **Age of Domain (Domain_Age):**
   - Extracts the age of the domain from the WHOIS database.
   - 1 (phishing) if the age is less than 12 months, 0 (legitimate) otherwise.

12. **End Period of Domain (Domain_End):**
   - Extracts the remaining domain time by finding the difference between expiration time and the current time.
   - 1 (phishing) if the end period is greater than 6 months, 0 (legitimate) otherwise.

### HTML & JavaScript-based Features:
In this category, 4 features are extracted.

13. **IFrame Redirection (iFrame):**
    - Checks for the presence of the "iframe" tag and makes it invisible without frame borders.
    - 1 (phishing) if the iframe is empty or not found, 0 (legitimate) otherwise.

14. **Status Bar Customization (Mouse_Over):**
    - Checks if JavaScript is used to show a fake URL in the status bar to users.
    - 1 (phishing) if the response is empty or "onmouseover" is found, 0 (legitimate) otherwise.

15. **Disabling Right Click (Right_Click):**
    - Checks if JavaScript is used to disable the right-click function.
    - 1 (phishing) if the response is empty or "event.button==2" is found, 0 (legitimate) otherwise.

16. **Website Forwarding (Web_Forwards):**
    - Checks the number of forwardings on the website.
    - 1 (phishing) if the number of forwardings is greater than 2, 0 (legitimate) otherwise.

<br> All the above mentioned features have been extracted using the FeatureExtraction.py in the git-repository.


