<h2> Jurassic Park </h2>

<h2>Description</h2>

<img width="787" alt="Screenshot 2025-04-15 at 10 57 23 pm" src="https://github.com/user-attachments/assets/a7767d62-cf00-4fb7-9c37-f063c0cc3727" />


<h2>Environments Used </h2>

- <b>  Ubuntu 20.4.6 LTS </b>
- <b> Target Machine (Provided by Try Hack Me) </b> 

<h2>Program walk-through:</h2>


<p align="center">
  
<p align="center">
  
I am using the Try Hack Me VM to perform this CTF. As shown below, the IP address of the target machine is 10.10.48.1 : <br/>
<img width="651" alt="Screenshot 2025-04-15 at 11 00 35 pm" src="https://github.com/user-attachments/assets/3b8d938f-11aa-4f9a-bd80-c1c1dc1cf2b3" />

Now let's check for any open ports by using nmap where we can ports 22 (SSH) and 80 (HTTP) are open -
<img width="651" alt="Screenshot 2025-04-15 at 11 04 14 pm" src="https://github.com/user-attachments/assets/bfc5c4de-d03d-470e-b72f-8f215e54c76b" />

Lets check for http by going on 10.10.48.1 in the browser
<img width="806" alt="Screenshot 2025-04-15 at 11 05 49 pm" src="https://github.com/user-attachments/assets/fee59d24-172d-41f1-b69e-e6082c452ada" />
<img width="806" alt="Screenshot 2025-04-15 at 11 06 02 pm" src="https://github.com/user-attachments/assets/a6109241-bd45-4381-a288-8c1a1441fbd7" />

Lets click on online shop link to check if we can find any further useful information
<img width="859" alt="Screenshot 2025-04-15 at 11 06 37 pm" src="https://github.com/user-attachments/assets/808e401f-07bf-402f-add6-2409882a6e93" />

Here we found Basic, Bronse and Gold Packages. This looks a php website based shop.php
<img width="908" alt="Screenshot 2025-04-15 at 11 07 24 pm" src="https://github.com/user-attachments/assets/dc5bc9a0-ae85-47cc-8ea2-5abbb5b86ee0" />


