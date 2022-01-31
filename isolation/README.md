<div id="top"></div>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]


<h3 align="center">Introduction to Resource Isolation</h3>
  <p align="center">
    This is the report for labsheets 1 to 4 by Ciara Costelloe (Student ID: X0009427).  
    <br />
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#steps-taken">Steps Taken</a></li>
    <li><a href="#outcomes">Outcomes</a></li>
    <li><a href="#conclusions">Conclusions</a></li>
  </ol>
</details>


<!-- STEPS TAKEN -->

## Steps Taken

<div id="steps-taken"></div>

1. Add credit to a Google Cloud Account and set up a project.
2. Investigated the processes running in the project enviornment and the processes within a namespace we created.
3. Investigated the different permissions level in the project environment and then within the namespace.
3. Created a script, ran it until it exceeded the resources of the namespace and was terminated.
4. Took a docker image from a repository and ran it.
5. Loaded same docker image into my own container images repo and ran it.
6. Turned on vunerability image scanner and reloaded images.  More on this below.
7. Then I ran a script inside and outside a namespace to count the CPU.  This was severely hampered by the fact I didn't know the fullstop was important in docker and I have some sort of full stop blindness.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- OUTCOMES -->

## Outcomes

<div id="outcomes"></div>

Outcomes of the vulnerability scan:
1 Critical
9 High
21 Medium
191 Total
71 Fixes

Outcomes of the cpu count:
Inside the container: CPU count 4
On the host: CPU count 4

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- CONCLUSIONS -->

## Conclusions

<div id="conclusions"></div>

Specific request to look at CVE-2019-19814 in detail.  This was the critical vulnerability in the banking app.
Vulnerability can write to out of bounds memory locations. 
Doc test on bugzilla says: An out of bounds (OOB) memory access flaw was found in the Linux kernel's F2FS file system. A local attacker could use this vulnerability to crash the system or leak kernel internal information.
Therefore this image should never be released to a production environment.  It would be especially important if that production environment was an actual banking app due to the impact a crash could have.
<br />
Should it be released to a test environment?  Ideally not as memory and cpu seems to still be shared with docker image from the machine and not hardware isolated.  
The test environment should be isolated from the outside world so they should not be in a position to be hacked (used best judgement on whether that is the case or not based on company).
<br />
Actions: Get the developer to update the OS in the image and make the relevant adjustments to the package as a matter of urgency.  The purpose of the code doesn't seem like there would be much need for it to be tied to an OS.  It's very high level. 

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png


