<h1>S3 Object encryption</h1>

<h2>Description</h2>
Considering the importance of data security for anyone who stores data in the cloud, encrypting data at rest ensures that only the encrypted format of the data can be viewed by anyone who gains access to the disks, thus making it useless for attackers. Though AWS offers several encryption mechanisms, in this lab I used Server-Side Encryptiion with Customer Manager Keys that were stored iin AWS Key Management services. This approach gives the customer control of the master key that generates data keys used by S3 to encrypt and decrypt data stored in its buckets.
<br />


<h2>Languages and Utilities Used</h2>

- <b>JavaScript Object Notation</b> 

<h2>Environments Used </h2>

- <b>AWS Console</b> 

<h2>Lab Walk-Through:</h2>

<p align="center">
Final Architecture after encryption: <br/>
<img src="https://github.com/TechProDavid/AWSencryption/blob/main/Cloud%20Environment%20-%20after%20encryption.png?raw=true" height="80%" width="80%" alt="Architecture"/>
<br />
<br />
Creating the Customer Managed Key:  <br/>
<img src="https://i.imgur.com/5QwrUIx.png" height="80%" width="80%" alt="Architecture"/>
<br />
<br />
Editing the key policy in JSON format: <br/>
<img src="https://i.imgur.com/pDgHVSB.png" height="80%" width="80%" alt=""/>
<br />
<br />
Editing the S3 Bucket policy to deny the upload of files that are unencrypted:  <br/>
<img src="https://i.imgur.com/3QB8QKy.png" height="80%" width="80%" alt="Architecture"/>
<br />
## The condition portion of the policy at the bottom expresses that server-side-encryption needs to be within AWS:KMS. But since the overall policy's "Effect" is "Deny", any object that was not encrypted with AWS KMS sever side encryption would not get uploaded into this bucket.

<p align="center">
Re-editing the policy to use only the customer managed key:  <br/>
<img src="https://i.imgur.com/EkKtKPc.png" height="80%" width="80%" alt="Architecture"/>
<br />
## I edited the policy a second time to be even more specific about the encryption requirements and narrow it down to the CMK that was created in the first step
<br />
<br />
<p align="center">
Verifying failed upload of unencrypted file: <br/>
<img src="https://i.imgur.com/xzQUuv6.png" height="80%" width="80%" alt="Architecture"/>
<br />
<br />
<p align="center">
Confirming successful upload of encrypted file: <br/>
<img src="https://i.imgur.com/bcWrwTT.png" height="80%" width="80%" alt="Architecture"/>


  
  
