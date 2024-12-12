# Research: Docker, Kubernetes and Database Security Practices

**Shineha Radhakrishnan**

## Introduction

Food Remedy’s reliance of APIs and containerized applications allows for ease of scalability and efficiency, however, it is vital to note that database infrastructure that is currently being used, Docker and Kubernetes, should be maintained to the highest of security practices to maintain confidentiality, integrity and availability, the 3 pillars of information security.

## Database Security

**Access Control:**

- It is recommended that role based access control is implemented to ensure that authorized members are allowed access, and ensure that this is regularly reviewed to remove any users that are no longer a part of the company to ensure security of sensitive information.

- PoLP (Principle of Least Privilege) should be implemented, therefore minimal permissions to the database shall preserve data integrity.

- Any log-in passwords shared for development should be regularly changed

**Encryption and Configuration:**

- Data that is stored at rest in the databases should be encrypted to ensure that only authorized database instances can access it, to further drive data integrity. It is recommended that encryption methods are used. 

- Recommendation: MySQL Transparent Data Encryption [1]

  - Encryption takes place before any data is written to the disk, such as data, logs etc. Features of SQL TDE is that Windows Data Protection API shall be used for the master key [1].
  - It is important to note that TDE is used for data at rest and not for when it is in transport between the database to the application.

- All database configurations should be reviewed regularly and features which may pose a threat, such as root access should be either configured with caution or disabled.


## Docker Security

Docker containers are integral to ease of deployment, however, certain security measures should be considered for good security practices.

- Recommendation 1: For container image security, ensure all images are trusted and verified. However, this alone is not enough to ensure the image is vulnerability-free [2], and additional steps are recommended.
  
- Implementation of vulnerability scanner tools are a great way to identify and fix security issues, while also giving an idea about how secure the application is.

- Recommendation 2: Tools:
  - CIS Docker Benchmarks are automated scans that look for issues with the host, daemon configuration, runtime and images [2].

  - As an extension to access control concerns raised previously, Dive is a good tool to understand permissions granted for the image [2].

  - Trivy is an open-source and free tool recommended as the scans extend further to file systems and Github repositories as well [2].

- For runtime attack prevention strategies, ensure that users that are allowed root privileges are minimized and monitored to prevent unauthorized access and data integrity.

## Kubernetes Security

As Kubernetes rises in popularity, the risk of attacks rises as well. It is imperative that configuration is secure and preventative measures are taken into account.

- Recommendation 1: Configuration vulnerabilities like usage of default settings and excess root privileges for the APIs make the application insecure and vulnerable to attacks.

- Recommendation 2: All software is regularly updated to patch security issues and other concerns. 

- Recommendation 3: Logging of information during runtime can allow for rapid incident response and flagging of suspicious behaviour [3].

- Recommendation 4: Ensure transport level security is enforced through usage of firewalls, especially for client-server, and server-server communication [3].

- Recommendation 5: The tool Kube-Bench allows for security scans on Kubernetes clusters.

## Monitoring and Logging

Finally, it is recommended that monitoring and logging to be implemented further on in the development process of this application, especially error handling within the code. It is good practice for security that prevention is focused on. 

Logging also plays an important role in forensic analysis, and logs can help in identifying areas of weakness, not only in an attack but for penetration testing as well.

- Recommendation 1: Tools like Prometheus ensure that any unusual changes in logging patterns are identified and flagged for immediate response.

## References

[1] [Data Encryption at Rest](https://learn.microsoft.com/en-us/dynamics365/business-central/dev-itpro/security/transparent-data-encryption)

[2][5 Best Vulnerability Scan Tools](https://learn.microsoft.com/en-us/dynamics365/business-central/dev-itpro/security/transparent-data-encryption)

[3] [Kubernetes Security Basics and 10 Essential Best Practices](https://www.aquasec.com/cloud-native-academy/kubernetes-in-production/kubernetes-security-best-practices-10-steps-to-securing-k8s/)
