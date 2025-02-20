# OWASP ZAP
OWASP ZAP (Zed Attack Proxy) is an open-source security tool used for web application testing. It acts as a "man-in-the-middle proxy" between the browser and the web application to detect vulnerabilities like SQL Injection, Cross-Site Scripting (XSS), and more. ZAP is widely used by developers, security professionals, and testers to improve application security.

## Launch OWASP ZAP
Open OWASP ZAP on your computer. On the Quick Start tab, you’ll see options for different types of scans, including the Automated Scan.

## ZAP Desktop UI
The ZAP Desktop UI is composed of the following elements:
1. Menu Bar – Provides access to many of the automated and manual tools.
2. Toolbar – Includes buttons which provide easy access to most commonly used features.
3. Tree Window – Displays the Sites tree and the Scripts tree.
4. Workspace Window – Displays requests, responses, and scripts and allows you to edit them.
5. Information Window – Displays details of the automated and manual tools.
6. Footer – Displays a summary of the alerts found and the status of the main automated tools.

<img width="581" alt="image1" src="https://github.com/user-attachments/assets/9e3eb0ff-2e47-4d23-ba4b-966699f40cd3" />

## Tests Run by ZAP
By default, ZAP scans include all of the tests in a **Release** status. However, users can choose to include rules that are included in **alpha** or **beta** status if they are interested.

### Scan Policy in OWASP ZAP
A scan policy defines which security rules (Active Scan Rules) will be applied during a scan. Users can modify the policy to enable or disable specific rules based on their needs.
ZAP classifies rules into three categories:
* Release (default) – Well-tested, stable rules.
* Beta – Less tested but generally reliable rules.
* Alpha – Experimental rules that may produce false positives.
  
![image2](https://github.com/user-attachments/assets/ccd61130-f4ca-4b2b-9def-3429d76dc8fd)

## Spidering the web application
Spidering a web application means crawling all the links and getting the structure of the application. ZAP will proceed to crawl the web application with its spider and passively scan each page it finds. Then ZAP will use the active scanner to attack all of the discovered pages, functionality, and parameters. ZAP provides two spiders for crawling web applications, you can use either or both of them from this screen.

### Traditional ZAP spider
The traditional ZAP spider discovers links by examining the HTML in responses from the web application. This spider is fast, but it is not always effective when exploring an AJAX web application that generates links using JavaScript.

### AJAX spider
This is more likely to be effective for AJAX applications. This spider explores the web application by invoking browsers which then follow the links that have been generated. The AJAX spider is slower than the traditional spider.

### Spidering
* Discovers URLs & links within a website by following anchor tags <a>.
* Parses HTML to extract links & follows them recursively.
* Ideal for Static websites, traditional HTML pages.

### Crawling
* More advanced—simulates user actions to explore dynamic content (e.g., JavaScript-based pages).
* Uses headless browser automation to interact with the application (like clicking buttons, expanding menus, etc.).
* Ideal for Modern web apps with JavaScript frameworks (React, Angular, Vue).

## Run an Automated Scan
The easiest way to start using ZAP is via the Quick Start tab. To run a Quick Start Automated Scan :
* Start ZAP and go to the Quick Start tab of the Workspace Window.
* Click the Automated Scan button.
* In the URL to attack text box, enter the full URL of the web application you want to attack.
* Click the Attack
ZAP will start crawling the web application with its spider and passively scan each page it finds. Then ZAP will use the active scanner to attack all of the discovered pages, functionality and parameters.

![image3](https://github.com/user-attachments/assets/05d3006f-8e4c-4ffb-88e0-45fde74d817e)

## Exploring an Application Manually 
You can launch browsers that are pre-configured to proxy through ZAP via the Quick Start tab. Browsers launched in this way will also ignore any certificate validation warnings that would otherwise be reported.
To Manually Explore the web application:
* Start ZAP and click the Quick Start tab of the Workspace Window.
* Click the large Manual Explore button.
* Enter the full URL of the web application to be explored in the ‘URL to explore’ text box.
* Select the browser you would like to use
* Click the ‘Launch Browser’ button. 

![image5](https://github.com/user-attachments/assets/9324f3a4-4b75-43b7-860b-7436ce342ae3)

Now explore all of the targeted web applications through this browser. ZAP passively scans all the requests and responses made during your exploration for vulnerabilities, continues to build the site tree, and records alerts for potential vulnerabilities found during the exploration. Here, you will be given penetration testing tools such as spiders, and if a vulnerability is discovered, an alert flag will be added to the alerts panel.

## Passive scanning
Passive scans review all HTTP requests and responses from the application, looking for indicators of security vulnerabilities. These scans do not change anything about the requests. Passive scanning is good at finding some vulnerabilities and as a way to get a feel for the basic security state of a web application.
![image](https://github.com/user-attachments/assets/41ac8fd1-3911-42ea-bc84-74bdddda63c0)

## Active scanning
Active scans, will create and modify requests being sent to the application, sending test requests that will surface vulnerabilities that would not be caught in a passive scan. Active scans are definitely a better way to test for vulnerabilities in your application. Active scanning attempts to find potential vulnerabilities by using known attacks against the selected targets. Active scanning is a real attack on those targets and can put the targets at risk, so do not use active scanning against targets you do not have permission to test. Active scans put the application at risk, so do not use active scanning against web applications you do not have permission to test.

#### Perform Active Scan
* Log in to DVWA using your browser.
* Intercept the request in ZAP:
  * Click Sites > DVWA > Right-click > Include in Context > Default Context.
  * Configure the login request.
![image](https://github.com/user-attachments/assets/0da0f508-51cf-4b70-8328-e6002836796a)
![image](https://github.com/user-attachments/assets/39caf6a6-1745-4f43-a960-899de7ceaeae)
* Go to Sites > DVWA > Right-click > Attack > Active Scan.
![image](https://github.com/user-attachments/assets/e9cf5b5e-583b-4073-b2b5-a1b9e5fe2e5c)
* Configure Attack Strength and Scan Policy (e.g., SQL Injection, XSS).
* Click Start Scan and wait for results.
![image](https://github.com/user-attachments/assets/c43df11a-9f05-437c-be39-1161326eea4f)

## Manual Testing
### Spidering (Crawling the Web App)
Spidering helps identify all accessible pages and endpoints in Damn Vulnerable Web Application (DVWA).
* Right-click on http://localhost/DVWA in the Sites tab.
* Click Attack > Spider Scan to find hidden links and pages. 
* Check the History tab for newly discovered URLs.

ZAP will crawl the application and list all discovered endpoints.
![image](https://github.com/user-attachments/assets/1ec2ec20-170f-46ff-ac30-fc6400d20ea5)
![image](https://github.com/user-attachments/assets/93e9b994-2c4a-4cc9-8dd5-9d4a33e09755)

### Fuzzing Input Fields in DVWA
Fuzzing helps test input fields for vulnerabilities by injecting various payloads.
* Navigate to an input field in DVWA, find a login form or search box.
* To Intercept the Request, go to the History tab, find the request, right-click, and select Attack → Fuzz.
* ZAP will open the Fuzzer Window.
* Select the 'name' parameter for fuzzing.
* Then click 'Add' to select a fuzzing payload (SQL Injection, XSS, etc.).
* Click Start Fuzzing 
* The Fuzzer Results tab will show responses for each payload.

**Common Choices for Name Fuzzing**
* Strings - Best for XSS, SQL Injection, and General Fuzzing
* Regex - Useful for Pattern-Based Testing
* File Fuzzers - For Large-Scale Testing
* Script - For Advanced Custom Payloads

Check for HTTP response changes, alerts, or reflected payloads.
![image](https://github.com/user-attachments/assets/721105ba-792f-4c29-84b3-d5f55957c82d)
![image](https://github.com/user-attachments/assets/d040782f-499f-4708-8a41-bcad5dd28921)
![image](https://github.com/user-attachments/assets/782cf67c-b1bf-4fec-beb5-35cafaba3b95)

Open your browser and enter
```
http://localhost/DVWA/vulnerabilities/xss_r/?name=<script>alert('XSS')</script>
```
If the alert executes, the site is vulnerable to Reflected XSS.
![image](https://github.com/user-attachments/assets/a6fa34e5-b2a9-4cd0-9387-e9e876e58ba5)

## Monitor the Scan Progress
Once the scan is complete, view findings in the Alerts tab (bottom pane). Click an alert to see the detected vulnerability and affected URL in the Information Window. Click each alert displayed in that window to display the URL and the vulnerability detected in the right side of the Information Window. In the Workspace Windows, click the Response tab to see the contents of the header and body of the response. 

### Sites Panel
Shows the structure of the target site, including all discovered URLs and resources. To examine a tree view of the explored pages, click the Sites tab in the Tree Window. You can expand the nodes to see the individual URLs accessed.

### Alerts Panel
Displays identified vulnerabilities as the scan progresses. Each alert includes details on the issue, risk level (high, medium, low), and recommendations. The left-hand side of the Footer contains a count of the Alerts found during your test, broken out into risk categories. These risk categories are
![image4](https://github.com/user-attachments/assets/a8897b70-674c-4fc1-b556-57767a11265d)
![image](https://github.com/user-attachments/assets/8232eb75-6c09-478d-be8c-1f0b7c0722d2)

## Save the Report
To generate a report for documentation or analysis:

Go to Report > Generate Report
![image](https://github.com/user-attachments/assets/34691a03-627f-4ddc-85cd-5c83140f9f69)
![image](https://github.com/user-attachments/assets/188b604a-08aa-4395-8df7-43b94f5764a1)
