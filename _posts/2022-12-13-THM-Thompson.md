# TryHackMe | {name}

+++++++++++++++++++++++++++++++++++\
IP: 10.10.36.151\
Date: 13-12-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

![image](https://user-images.githubusercontent.com/115549820/207389602-cc59d731-fee9-4a0e-836c-9178bfc7ff75.png)

**Open Ports**

22 - SSH - OpenSSH 7.2p2\
8009 - Apache Jserv (Protocol v1.3)\
8080 - Apache Tomcat 8.5.5

### Webserver Enumeration

![image](https://user-images.githubusercontent.com/115549820/207410833-f24a879f-18ec-4a8c-847d-8a1620eda39b.png)

***Landing page***

![image](https://user-images.githubusercontent.com/115549820/207410987-f222883f-1255-47f0-84f0-6b3a4d59e147.png)

***/manager***

![image](https://user-images.githubusercontent.com/115549820/207411279-084a7c0b-1bb5-4e4e-9e8f-e2c5234001f0.png)

***admin::admin***

![image](https://user-images.githubusercontent.com/115549820/207411573-eb28fe06-3928-4205-bc90-73c3c722f1c5.png)

![image](https://user-images.githubusercontent.com/115549820/207411648-f5a689d8-fceb-4ffc-af65-b275d78f85f3.png)

***/manager tomcat::s3cret***

![image](https://user-images.githubusercontent.com/115549820/207411800-8e38611f-3e28-40cd-8934-cc827c4afd09.png)

![image](https://user-images.githubusercontent.com/115549820/207411868-6cc9c857-f49c-43ac-a887-a4798ed55f64.png)

![image](https://user-images.githubusercontent.com/115549820/207411938-7e1a0ae1-559e-430a-bd22-510b8020a98a.png)


## Fase 2: Getting Access

![image](https://user-images.githubusercontent.com/115549820/207412210-05648f44-5bd1-414f-8a78-a8b259d6f650.png)

![image](https://user-images.githubusercontent.com/115549820/207412394-6153fb9d-aa10-426b-af03-204d12471863.png)

https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/tomcat

![image](https://user-images.githubusercontent.com/115549820/207413049-580d1021-e0f6-4308-be86-e75e8534fd6b.png)

![image](https://user-images.githubusercontent.com/115549820/207413431-190d7a64-bcfd-4066-8a19-1cc469e6b816.png)

![image](https://user-images.githubusercontent.com/115549820/207413547-0ef4ac76-c8f4-4576-ace2-4ce9f0afea83.png)

![image](https://user-images.githubusercontent.com/115549820/207413640-80cf2a01-943e-40ab-af1a-d10adcd235f8.png)

![image](https://user-images.githubusercontent.com/115549820/207413702-692209d1-8064-432a-a494-4a427620e154.png)

![image](https://user-images.githubusercontent.com/115549820/207413885-e7ccf438-23bb-45ae-817a-da4ea16e91c2.png)
  
## Fase 3: Intern Enumeration

![image](https://user-images.githubusercontent.com/115549820/207413993-05a09aba-b174-4990-893a-0afe69bccc0d.png)

![image](https://user-images.githubusercontent.com/115549820/207414081-c573022e-ff9f-4787-a54a-4745787dd612.png)

![image](https://user-images.githubusercontent.com/115549820/207415291-27df9c47-18b7-4a19-8718-cfbc247bb49d.png)

![image](https://user-images.githubusercontent.com/115549820/207415705-06cc4646-7dd1-41c5-9beb-a2567e5b3b1e.png)

![image](https://user-images.githubusercontent.com/115549820/207417698-7a568fe0-27fc-4901-8bad-1adf556fd059.png)


![image](https://user-images.githubusercontent.com/115549820/207417055-32323c53-aa4f-44e2-aa4d-d9b28d284653.png)

![image](https://user-images.githubusercontent.com/115549820/207417130-00729063-480e-4f45-bc96-500f8e4df92d.png)

## Fase 4: PrivEsc

![image](https://user-images.githubusercontent.com/115549820/207419887-4ba1ba07-0f8d-49ec-b30b-a2d112ae6eba.png)


![image](https://user-images.githubusercontent.com/115549820/207418160-915b2ccf-8901-451c-8c7a-e5e9c60ec2f5.png)

## TryHackMe Questions

user.txt
> 39400c90bc683a41a8935e4719f181bf

root.txt
> d89d5391984c0450a95497153ae7ca3a
