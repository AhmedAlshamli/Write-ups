**SQU Sec CTF write-up
can you login**


start by using Nmap or any other scanning tool to find the open ports

![Image](https://github.com/user-attachments/assets/04374048-b14a-42c2-913b-ac73c24bfddd)

2 ports are open 

SSH and HTTP

lets see what is in the web page 

![Image](https://github.com/user-attachments/assets/dd2f4eb1-7959-40fc-bae0-1f14d45ad924)

following the Instagram link https://www.instagram.com/aahh_mmeeddx

![Image](https://github.com/user-attachments/assets/b1f9e129-64bc-467b-b4ac-a12cf5e425c3)

Nice! some Infromation about the developer of the website

"I am Ahmed, born in 2000 🎉
I am a developer 🧑‍💻
I like cats 🐱"

are there any other pages ?

lets use gobuster
![Image](https://github.com/user-attachments/assets/76cf6faf-2242-469a-af56-0c4ddf93a73a)

nothing ?
we need to check that with some extensions

![Image](https://github.com/user-attachments/assets/f9188af5-fa05-405d-9894-de6b4af6734a)

Great! this was the answer of the first question

 This is the page 

![Image](https://github.com/user-attachments/assets/550df2c5-5c5d-4eb6-a14f-2a98afdd7058)

we have some information about the developer. why not to use it ?

search for any tool ( or create yours :) ) to generate common passwords using the information you know to get a wordlist and use the name of the developer as the username 

I will use CUPP for this task
![Image](https://github.com/user-attachments/assets/314ca372-673e-4367-a45c-39354cd58134)
![Image](https://github.com/user-attachments/assets/be5b41fd-2068-4a0b-ba9a-2a8e317d0817)

( a small hint : the password has _ )


to brute force websites login pages use

`hydra -l ahmed -P ahmed.txt 10.10.82.164 http-post-form "/auth.php:username=^USER^&password=^PASS^:F=Invalid" -V`


hydra : the name of the tool

-l for a username and -L for username wordlist
-p for a password and -P for passwords wordlist

the IP or the host of the website

the method or function (GET, POST)

the subdirectory
:
the parameters ( use ^USER^ and ^PASS^)
:
S=success value in the response or F= failure value in the response

-V verbose to show all the combinations used 

![Image](https://github.com/user-attachments/assets/1c03a211-1958-48d1-99de-97237a03c897)

and here is the password and the answer of the second question

finally log in to the page to find the third flag

![Image](https://github.com/user-attachments/assets/d4560bab-aae7-40f5-b481-0517e9bb3784)
![Image](https://github.com/user-attachments/assets/33ee54a5-a635-45e2-98bd-89303dca7c7f)

