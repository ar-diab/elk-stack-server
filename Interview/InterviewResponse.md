#### Domain: Network Security

**Question 1:  Faulty Firewall**

Suppose you have a firewall that's supposed to block SSH connections, but instead lets them through. How would you debug it?

Let's say that we have SSH connections being allowed to a VM that has a supposed firewall setup. The first thing I would do is verify this by SSHing. Once I verify that I can gain access, I begin thinking about the different possiblites that could have led to this occuring. Instead of blindly guessing where the firewall setup went wrong, I would take a systemic approach to ensure that I don't miss anything. I would take a ground up approach, in other words, I would retrace the steps of the setup verifying that everything is setup correctly. A summary of the specific details of the setup process that I would analyze would be:
 - Ensure that the firewall is setup for the correct VM/device.
 - Check the security group rules to see if/where access is being allowed.
    - Verify that no SSH connections are being allowed OR that you can only SSH from pre approved IPs (like a workstation for example).

This solution, while time consuming, ensures that we cover every step of the firewall setup from beginning to end making it one that will almost guaranatee that we find the bug. For the future, we should ensure that our access requirments are clearly documented and understood by those setting up the firewall. In addition, all security rules should be double checked to ensure htey meet these requirments. We should also implement monitoring controls that keep track of what kind of traffic we have coming in so that we know when something is not behaving as expected.

**Question 2: Unsecured Web Server**

Suppose you find a server running HTTP on port 80, despite compliance guidelines requiring encryption in motion. What do you do?
​​
In Project 1 we were not dealing with HTTPS traffic, just HTTP which was one reason we could use port 80. In addition, we were also in control of the traffic as there was no external access to our network so we can be sure that no malicious traffic will be coming in through this port. 

Running HTTP on port 80 is a problem because compliance guildines require encryption. Port 80 is used for unecrypted traffic leaving information exposed and vulnerable comprimising integrity and confidentiality. To solve this, I would recommend switching to the HTTPS protocol (and by extension port 443). This way we would be able to encrypt the traffic therefore assuring that a. only those who it's meant for have access to it unencrypted and b. compliance guildines are met.

In order to implement this solution we would need to ensure that all the proper changes are made in the firewall and in the respective network security rules.

In order to help clients who may require this port. We can allow them to communicate with the server over another controlled port that only they have access to. We can whitelist the specific IPs they'll be connecting from to ensure that our traffic is controlled, maintained, and authorized.