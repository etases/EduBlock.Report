# Project Introduction

## Overview

### Project Information

*	Project name: BlockChain application in academic record management to support online University/College admissions
*	Project code: EduBlock
*	Group name: ETASES
*	Software type: Web app

### Project Team

#### Supervisor
| Full Name     | Email           | Phone Number | Title   |
|---------------|-----------------|--------------|---------|
| Quach Luyl Da | daql@fpt.edu.vn | 0976703075   | Lecture |

#### Team Members
| Full Name        | Email                     | Phone Number | Title  |
|------------------|---------------------------|--------------|--------|
| Huynh Quang Tien | TienHQCE150130@fpt.edu.vn | 0976608340   | Leader |
| Le Xuan Tu       | TuLXCE150344@fpt.edu.vn   | 0939774512   | Member |
| Nguyen Dang Khoa | KhoaNDCE140165@fpt.edu.vn | 0382554293   | Member |
| Cao Hoang Anh Uy | UyCHACE150661@fpt.edu.vn  | 0706456981   | Member |
| Nguyen Minh Khoi | KhoiNMCE150103@fpt.edu.vn | 0338616352   | Member |


## Background
The number of academic institutions still use manual processes to store and transfer academic records like transcripts and certifications between institutions and to potential organizations, despite the fact that many large institutions are now adopting the modern practice of maintaining electronic academic records. The process can take up to several days, just for students who want to review their own transcripts, so a common transfer for a student can take anywhere from a few weeks to a month. Due to the time required to process and submit appeal requests using the widely used paper method, more serious errors could happen, and the process could take several months. In addition to the significant wait time and the possibility of physical damage or loss of records during storage and transportation, there is also the risk of credential tampering by fraudulent parties. The cost of processing time, manual work effort, postage, and transit fees, as well as the storage and shipping of physical records, are also very expensive.

The emerging solutions are primarily based on email-based solutions or the transfer of PDF files while remaining limited by nationality, privacy and security barriers. Although the popularity of cryptocurrencies and NFTs has led to the implementation of Blockchain as a host of applications in the financial sector, the field is more diverse in both technical and application areas [1]. As distributed applications are increasingly applied in various fields such as data storage (including handling medical records and healthcare [2,5]), Cloud and Grid Computing [3], e-vote [4], Service for IoT [6], Banking system[7] and foremost is the field of Education. Academic institutions can benefit from blockchain technology to provide a decentralized and immutable ledger to confirm the integrity of academic records [10]. Then, solutions for storing and anti-fraud of online electronic degrees have also been conceived to bring the initial benefits of applying Blockchain technology [8][9]. While these solutions provide a more modern approach to the storage and the transfer of academic records, there are still limitations in terms of widespread adoption, auditability, and scalability. A successful solution for storing and exchanging electronic school records will include Security and Privacy, Scalability and at the same time benefit from the advantages of blockchain technology as Distributed, Transparency further described.

The goal of our proposed system is to address the limitations of existing solutions by utilizing Blockchain technology to provide a secure, verifiable, and tamper-proof method of storing, accessing, managing, and exchanging electronic school records between institutions.


## Existing Systems

### Blockcerts

Blockcerts is an open standard platform for developing, issuing, and verifying blockchain-backed certificates that Learning Machine and the MIT Media Lab jointly developed. The business can assess the validity of documents and identify fraudulent information by generating records like academic transcripts and certificates on a blockchain. Grades, transcripts, and even degrees can all be kept on a Blockcerts blockchain enabling immutable access to previous academic performance.

### APPII
The blockchain, smart contracts, and machine learning technologies used by APPII are used to validate the academic credentials of potential students and lecturers. Users set up a profile and complete their academic CV, which includes their academic background and transcripts. The user's background is subsequently verified by APPII using blockchain, and their data is then locked into its blockchain.

### Parchment
Students, academic institutions, and employers can use Parchment's digital certificate services. Higher education institutions use the platform to evaluate academic excellence, process applications, and generate immutable degrees, while K-12 educators use the blockchain of the company to upload any significant developmental progress. Additionally, all educational information is permanently accessible to students, and they may readily tell prospective employers about their academic accomplishments.

### Conclusion
From all systems mentioned above, in this design we presented a solution for managing and storing electronic academic records as a replacement for the traditional academic record based on distributed storage technology used by Blockchain, where the data is stored in a block and the blocks are connected on a chain by hashing. Our network enables us to manage data in the network using transactions via smart contracts. From there next, we show how to set up a multi-tier network and processes. Our network enables us to decentralize organizations and system users through arranging chain nodes, verifying transactions with smart contracts, archiving modification history and restoring data of a node using data from other nodes.

From this design, it can be concluded and proposed to organize a Permissioned Blockchain network with a multi-tier design. The main advantage of applying Permissioned Blockchain technology is its resistance to many threats and cyber attacks, rely on the hashing mechanism and the nodes on the Blockchain can prevent data breaches. And moreover, it offers a host of unique features such as improved reliability, better fault tolerance, faster and more efficient operation, and scalability.

And thus, the management of documents for the field of education has the potential to be significantly impacted by the integration of Blockchain, the hyperledger framework, and smart contract technologies across academic records.


## Business Opportunity
Although many high schools in Vietnam still keep paper records for post-graduation and enrolment in college or university, many now employ an online system to track students' academic progress and inform parents of any latest outcomes. Because they must do it for both the paper records and the internet system, teachers find it challenging to update the information on their students. There is also a minimum level of transparency for students who wish to verify their information at any time because the internet system is centralized and only administrators and teachers have access to it. As a result, a system is required to help teachers and students manage student records in an easier, quicker, and more effective manner. 

## Software Product Vision
With the use of this system, students may simply keep track of changes to their grades in their academic records, reducing teacher grade entry errors. In order to gain rapid admission to graduate programs and colleges, students can also more conveniently retrieve their transcripts. High security and restrictions on data editing also assist in limiting the issue of phony points that are inaccurate representations of reality. Additionally, it eliminates challenges with entering grades into instructors' school records because doing so will be quicker and easier with the aid of the system.

## Project Scope & Limitations
A record management system will always be the best in terms of security and purity because it must, of course, assure data security. When interacting with and storing the data, always keep it intact and unaltered. Additionally, it must be user-friendly, with an interface that is clear and unambiguous and avoids misinterpretations of the translation or the information on the screen. Without the responsible user's consent, data editing procedures cannot be carried out at will.

### Major Features

FE-01:  Using the blockchain platform, store data.

FE-02:  Transcripts can be updated by converting photos to alphanumeric data.

FE-03:  May replace paper school records entirely (electronic school records but have the nature of paper school records).

FE-04:  Enhancing the effort teachers put into entering grades.

FE-05:  Utilization dependability for admissions parties.

### Limitations & Exclusions

LI-1: It is impossible to synchronize student counts between institutions due to the dispersed nature of the data.

LI-2: The only time to use the system is at the end of the year because it only saves the semester's overall grade (can be expanded later)

LI-3: There is no option to switch schools (due to not processing student codes synchronously)


