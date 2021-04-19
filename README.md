# DockerSecretsScanner

	Docker is an open-source application container engine that allows developers to package their applications and dependency libraries 
into a portable image and publish them to any popular Linux or Windows hardware, as well as virtualize them. Containers are entirely
sandboxed and don't have any interfaces to each other.
    Docker has become an important tool for enterprises to develop, test, and deploy formal services.Currently, security tools for
Docker are mainly focused on the discovery of various software vulnerabilities, and a tool that focuses on the discovery of privacy
security issues is lacked. Especially for enterprises that use self-built container repository, once the image containing privacy
information is accessed by the outside, it is extremely easy to cause privacy leakage.
    We have developed a scanning tool for container repositories that focuses on detecting potential container privacy leakage issues,
including but not limited to:

    - System account password and database account password saved in plaintext

    - Cloud service access key (AK) saved in plaintext

    - Personally identifiable information (PII) saved in plaintext


    To our knowledge, we are the first open source tool that combines expert rules, machine learning and other techniques to detect 
privacy security issues in Docker.

# Tool Details
How to use：
 python secretscanner.py --help

 Usage: secretscanner.py [options]

 Options:
    -h, --help  show this help message and exit
    -i IMAGENAME, --image=IMAGENAME  docker image name

1.	The ability of expert rules and AI models to detect the plaintext accounting and encryption information in Docker image files.
In the process of daily product development, the lack of awareness of information security and negligence of engineers will cause product account information plaintext or third-party cloud products access AK hard coding leakage. If the information are collected and utilized by hackers, it will bring known or unknown risks to the enterprise.
In order to better detect plaintext information, expert rules apply this information as the basic discovery capability of sensitive plaintext information.
Based on a large amount of unstructured sensitive plaintext data, we trained a more accurate sensitive information detection AI model, which further enhanced the scanning capability of the tool.

2.	In what scenarios is Docker image plaintext information detection applicable?
In the process of software development, various commercial or open source CI integration tools, such as Travis, Jenkins, etc., are usually used in order to better guarantee the code quality and make the product iterate quickly.
This tool can be used as a security infrastructure before the launch of the product, and can detect the plaintext information of the images to be released, as an effective means to prevent the leakage of the plaintext secret information.

3. Account detection capability currently supported by the tool
    - Encryption keys
        - PKCS8 private key
        - RSA private key
        - SSH private key
        - PGP private key
        - SSH (DSA) private key
        - SSH (EC) private key
    - Cloud Services
        - Amazon Web Services (AWS)
        - Google Cloud Platform (GCP)

