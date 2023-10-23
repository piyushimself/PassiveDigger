# PassiveDigger Burp Suite Extension

## Overview

PassiveDigger is a comprehensive Burp Suite extension designed for passive analysis of web traffic. By targeting specific host-port combinations, this extension listens to traffic and provides hints or identifies potential vulnerabilities. It performs checks on both incoming requests and server responses, offering a wide range of features to enhance your web vulnerability assessments.

## Features

### Request Checks
- Find file upload functionalities
- Find serialized data in requests
- Find base64-Encoded data in requests

### Response Checks
- Find SQL errors in response for SQL injection
- Find reflected parameters (Possible XSS or HTML injection)
- Find possible LFI vulnerabilities
- Find sensitive files
- Fingerprint web server/application
- Find directory indexing/browsing
- Find possible Execution After Redirection (EAR)
- Find sensitive data in errors
- Find misconfigurations in Cookie flags
- Find Base64-encoded data in response
- Extract email addresses
- Extract phone numbers

### Additional Features
- Analyzer Tab for listing all findings
- Load past traffic from History or Sitemap
- Mark findings as false positives
- Send findings to "Repeater" or "Intruder" for further testing
- Headers Tab for listing unique headers and their values
- Security Headers check

## Build From Source Code
1. To build the project, you need <a href="https://gradle.org/install/">Gradle</a> installed.</br>
2. Clone the repository</br>`git clone https://github.com/moeinfatehi/PassiveDigger`
3. Open the main directory of the project (where build.gradle file exists) and run: `gradle makeJar`
4. The Jar file will be generated in "build/libs/PassiveDigger.jar"

## Installation

The quickest way to install PassiveDigger is to load the jar file (PassiveDigger.jar) into Burp Suite.

1. Open Burp Suite
2. Go to `Extender -> Extensions -> Add`
3. Load the `PassiveDigger.jar` file

A new tab will be added to the Burp Suite, and you are all set to use the extension.

## Usage

### Setting a Target
Right-click on any request-response pair in various Burp Suite tabs (Proxy, History, Repeater, Scanner, etc.) and select `Send target to Passive Digger` to set a target for analysis. You can set multiple targets, manage them in the Targets tab, and remove or clear targets as needed.

### Analyzer Tab
Enable or disable specific checks and update the results by clicking on the "Update Analyzer Tab" button. For each finding, you'll get detailed information, including:

- Severity
- URL
- Parameter
- Parameter Type
- Check Code
- Description
- CVSS Score (if applicable)
- Full Request and Response for PoC

You can double-click any row in the table for a detailed frame view of the vulnerability. You can also mark each finding as a false positive or send it to other Burp Suite tabs like "Repeater" or "Intruder" for further manual testing.

### Headers Tab
The Headers tab lists unique headers and values detected in the responses. You can also add some headers as exceptions to not list them in the table.

### Security Headers
This tab checks for the following security headers and their configured values:

- X-XSS-Protection
- X-Frame-Options
- Content-Security-Policy
- X-Content-Type-Options
- Referrer-Policy
- Strict-Transport-Security (WSTG-CONF-07)

## Fine-Tuning Tips for Best Results

To make the most out of PassiveDigger, you can fine-tune its functionality using the following approaches:

### 1. Use as Upstream Proxy with Web Scanner Software (e.g., Acunetix, Netsparker)
To set this up:
1. Open Burp Suite and enable the PassiveDigger extension. Set your target.
2. In your web scanner software, configure Burp Suite as an upstream proxy.
3. Start scanning the target in your web scanner software.

This will allow PassiveDigger to analyze the traffic generated by the web scanner, helping you identify vulnerabilities or hints.

### 2. Use as Upstream Proxy with Burp Suite Scanner
For this approach, you'll need two instances of Burp Suite:
1. In the first instance, act as the upstream proxy. Enable PassiveDigger and set your target.
2. In the second (primary) instance, configure the first Burp Suite instance as its upstream proxy.
3. Start scanning your target with the primary Burp Suite instance.

With this configuration, PassiveDigger will analyze the scanner traffic from the primary instance.

### 3. Perform Crawling on Target Using Burp Suite
To use this method:
1. Run a single instance of Burp Suite with the PassiveDigger extension enabled and the target set.
2. Navigate to `Target -> Sitemap` tab.
3. Right-click on the target and select the "Scan" option.
4. Choose "Crawl only" from the list to start crawling.

This will allow PassiveDigger to listen to the scanner traffic and identify

## Contact

For more information and updates, follow me on:
- [Twitter: @moeinfatehi](https://twitter.com/moeinfatehi)
- [GitHub: moeinfatehi](https://github.com/moeinfatehi)

