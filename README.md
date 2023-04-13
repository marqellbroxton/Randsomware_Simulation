# Randsomware_Simulation


1. Started with a Kali Linux (Attack) and Windows (Victim) virtual machine in VMware.

![3013E803-FC73-480C-AEA2-F289DF75DB13_1_201_a](https://user-images.githubusercontent.com/56138615/231588081-3a12d199-10b1-49e5-8095-f6a4e2a836c9.jpeg)![Screen Shot 2023-04-12 at 5 21 28 PM](https://user-images.githubusercontent.com/56138615/231588125-b235fcaa-e180-40f1-8e1c-e6b9d6970803.png)


2. Created an organization in LimaCharlie, then created a sensor to detect and monitor the Windows virtual machine.

![Screen Shot 2023-04-12 at 5 33 35 PM](https://user-images.githubusercontent.com/56138615/231591055-d8f44002-1907-45ea-afd2-9443b9cae1a1.png)
![Screen Shot 2023-04-12 at 5 44 00 PM](https://user-images.githubusercontent.com/56138615/231593160-8bc838ea-0a19-4e6b-91e4-914cfb610f9d.png)

3. SSH into a sliver server and generated an implant configuration.

![Screen Shot 2023-04-12 at 5 57 41 PM](https://user-images.githubusercontent.com/56138615/231595349-74aec4cf-6509-4828-a584-69db8b857525.png)
![Screen Shot 2023-04-12 at 5 58 29 PM](https://user-images.githubusercontent.com/56138615/231595478-8bdcb60b-463e-4a7f-91dc-8238229eabc1.png)

4. Launched a HTTP server in sliver from the Kali linux machine and used the C2 on the Windows machine to download and run the implant file, creating a session I can use remotely from the Linux machine. Under processes in LimaCharlie it has captured the connection of the two machines.

![Screen Shot 2023-04-12 at 6 13 39 PM](https://user-images.githubusercontent.com/56138615/231598210-6b6d9268-0cbf-4aa2-85e5-8f0060326675.png)
![Screen Shot 2023-04-12 at 6 14 14 PM](https://user-images.githubusercontent.com/56138615/231598230-a6c521c7-1584-4cad-9617-34be8092baf5.png)
![Screen Shot 2023-04-12 at 6 14 46 PM](https://user-images.githubusercontent.com/56138615/231598241-76a7e16e-64c6-49f6-b441-c3982b70d486.png)
![Screen Shot 2023-04-12 at 6 15 29 PM](https://user-images.githubusercontent.com/56138615/231598255-238b472d-3fa6-4406-805f-f2277c64d8ee.png)

5. Next I tried to get credentials by dumping the lsass.exe process from memory. In detections there was an alert triggered with the name of the kind of process I was attempting to execute from a detection rule I made for this attack. It alerts under the event type sensitive process access.

![Screen Shot 2023-04-13 at 12 50 10 AM](https://user-images.githubusercontent.com/56138615/231657904-b74a5c63-ad63-4b06-a384-1e35afd6881a.png)
![Screen Shot 2023-04-13 at 1 45 27 AM](https://user-images.githubusercontent.com/56138615/231664810-bba24207-73ee-4a74-9383-8f44a5543e7c.png)
![Screen Shot 2023-04-13 at 1 44 49 AM](https://user-images.githubusercontent.com/56138615/231664826-ebf39ba6-600d-45fd-a674-4c1b85ed7617.png)


6. Another attack I try is the deletion of volume shadow copies. Not only do I want to detect this attack but also terminate the command before it is executed. I configured a response rule to do just that and showed that when I try the whoami command in the shell it fails sense the parent process was terminated.

![Screen Shot 2023-04-13 at 2 03 44 AM](https://user-images.githubusercontent.com/56138615/231668865-8e920ffe-9b14-4bc1-8476-aa90c0a282e5.png)
![Screen Shot 2023-04-13 at 12 51 00 AM](https://user-images.githubusercontent.com/56138615/231668219-fe3ac613-1c64-479b-b4bd-0fcfb9dd5a17.png)
![Screen Shot 2023-04-13 at 1 08 04 AM](https://user-images.githubusercontent.com/56138615/231659233-37e6c731-274f-4336-914a-1c9d00794557.png)
![Screen Shot 2023-04-13 at 2 17 50 AM](https://user-images.githubusercontent.com/56138615/231670410-c60fa97c-16d8-4f93-9574-db67a57fe9f9.png)
![Screen Shot 2023-04-13 at 2 04 13 AM](https://user-images.githubusercontent.com/56138615/231669110-4543c5c5-044b-4dfe-9132-797850631bd8.png)














