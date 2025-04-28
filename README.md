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

Now let's check for any open ports by using nmap where we can ports 22 (SSH) and 80 (HTTP) are open - : <br/>
<img width="651" alt="Screenshot 2025-04-15 at 11 04 14 pm" src="https://github.com/user-attachments/assets/bfc5c4de-d03d-470e-b72f-8f215e54c76b" />

Lets check for http by going on 10.10.48.1 in the browser : <br/>
<img width="806" alt="Screenshot 2025-04-15 at 11 05 49 pm" src="https://github.com/user-attachments/assets/fee59d24-172d-41f1-b69e-e6082c452ada" />
<img width="806" alt="Screenshot 2025-04-15 at 11 06 02 pm" src="https://github.com/user-attachments/assets/a6109241-bd45-4381-a288-8c1a1441fbd7" />

Lets click on online shop link to check if we can find any further useful information : <br/>
<img width="859" alt="Screenshot 2025-04-15 at 11 06 37 pm" src="https://github.com/user-attachments/assets/808e401f-07bf-402f-add6-2409882a6e93" />

Here we found Basic, Bronse and Gold Packages. This looks like a php website based shop.php : <br/>
<img width="908" alt="Screenshot 2025-04-15 at 11 07 24 pm" src="https://github.com/user-attachments/assets/dc5bc9a0-ae85-47cc-8ea2-5abbb5b86ee0" />

Now, lets try and click on different links i.e. those given packages, if we can find something in those given packages. After clicking on Basic package, we see a well known URL dork called id?php=3 used for SQL injections. The parameter can be used to query something from database - <br/>
<img width="908" alt="Screenshot 2025-04-15 at 11 08 12 pm" src="https://github.com/user-attachments/assets/4bd868d4-a532-41f9-b390-62a19dd5b368" />

In this URL, lets try entering quote ' and check if we can fetch any results from the database as follows - <br/>
<img width="908" alt="Screenshot 2025-04-15 at 11 09 40 pm" src="https://github.com/user-attachments/assets/3938c4e2-518b-410f-a01b-c60923fd7d20" />

Looks like it didnt give any results.  <br/>
<img width="908" alt="Screenshot 2025-04-15 at 11 10 40 pm" src="https://github.com/user-attachments/assets/ba73de7b-3e9d-4b83-a180-28a809f89350" />
<img width="908" alt="Screenshot 2025-04-15 at 11 10 56 pm" src="https://github.com/user-attachments/assets/88388d22-44ed-4714-9224-2b6ef38acf9e" />

 As suggested above, lets us try SQL maps.  <br/>
<img width="653" alt="Screenshot 2025-04-15 at 11 15 06 pm" src="https://github.com/user-attachments/assets/56a50cd7-4944-4d53-82c4-e1f09bbc6a71" />

Simultenously, we can also try using SQL injection methods as follows. We have double quotes and single quotes, but, alas it hasn't given us any results - <br/>
<img width="911" alt="Screenshot 2025-04-15 at 11 15 38 pm" src="https://github.com/user-attachments/assets/ee228a73-7c5b-4801-b29c-044a7c8778c3" />
<img width="911" alt="Screenshot 2025-04-15 at 11 16 31 pm" src="https://github.com/user-attachments/assets/887454dd-6af5-4a88-a8b5-7a3f5228f676" />
<img width="911" alt="Screenshot 2025-04-15 at 11 17 15 pm" src="https://github.com/user-attachments/assets/a6e4e4a4-5e3d-456a-a29c-2efb5d8741a7" />

Now, let us try other packages such as Bronse or Gold. <br/>
<img width="911" alt="Screenshot 2025-04-15 at 11 19 14 pm" src="https://github.com/user-attachments/assets/3f13ce5c-5511-4f97-a257-0e2507292a3d" />
<img width="911" alt="Screenshot 2025-04-15 at 11 19 49 pm" src="https://github.com/user-attachments/assets/fb27c1af-d952-4b3a-be9d-9e8b56c3040c" />

We can try finding any hidden web pages using IDOR as below. I tried id=4, id=0 and id=5 <br/>
<img width="911" alt="Screenshot 2025-04-15 at 11 21 58 pm" src="https://github.com/user-attachments/assets/c46ef0e6-75cd-4545-916d-ea0eefc393c1" />
 <img width="911" alt="Screenshot 2025-04-15 at 11 22 34 pm" src="https://github.com/user-attachments/assets/63391cc4-3643-4f68-b0ba-eeae2e682b66" />

By trying id=5, we found this Development page. It is not listed on this website, however, I am assuming that this page seems to be test page or something mainly used by developers as per the given name. We can see that some characters are blocked such as ', #, DROP, -, USERNAME, @. By trying IDOR, we have found such pages which maybe used for their internal use -  <br/>
 <img width="911" alt="Screenshot 2025-04-15 at 11 23 26 pm" src="https://github.com/user-attachments/assets/e562b950-db1c-4318-b06c-ad9eaa9aa196" />

Meanwhile let us find the status of our sqlmap -  <br/>
<img width="650" alt="Screenshot 2025-04-15 at 11 25 32 pm" src="https://github.com/user-attachments/assets/0eaa9773-4e48-4695-b195-5a18c8153bd0" />

As mentioned above in the development package, we understand some of the characters are blocked, let us refrain from using them. We can the something like this and found ... page and can see that $ value is -1  <br/>
<img width="859" alt="Screenshot 2025-04-16 at 10 34 20 pm" src="https://github.com/user-attachments/assets/0678b792-6211-455e-9242-28891020afa0" />

We have used order by column to check how many columns must be there in the database. I tried until 5 and it has given no error, but, when I tried for 6, it has given me an error  <br/>
<img width="859" alt="Screenshot 2025-04-16 at 10 40 28 pm" src="https://github.com/user-attachments/assets/522077d2-5c4d-4cbd-b8ad-8820aa9f4b9e" />
<img width="859" alt="Screenshot 2025-04-16 at 10 40 49 pm" src="https://github.com/user-attachments/assets/97309119-6fe9-46ea-b5eb-4ff2722e5dbc" />
<img width="859" alt="Screenshot 2025-04-16 at 10 41 06 pm" src="https://github.com/user-attachments/assets/4d4a3d18-a870-4d4b-a86a-c76659352770" />

This is as shown. So we understand that there are 5 columns in the database result set -  <br/>
<img width="887" alt="Screenshot 2025-04-16 at 10 41 35 pm" src="https://github.com/user-attachments/assets/2f14116e-3e59-445c-b619-cc1aa78151c8" />

The next step is, we need to fetch the data from these columns, therefore, we use UNION in our SQL query. We can see the values on the page such as 2,3,4,5 only 1 is not showing on the page -  <br/>
<img width="887" alt="Screenshot 2025-04-16 at 10 45 04 pm" src="https://github.com/user-attachments/assets/faf7e9b7-1d92-46d7-a20f-a381b8697ce3" />

There are some CTF questions, one them wants us to find the SQL database version. We use version() in our query in the URL -  <br/>
<img width="887" alt="Screenshot 2025-04-16 at 10 47 19 pm" src="https://github.com/user-attachments/assets/2007cb3c-a077-4c0d-ba46-644cf5253f5f" />

Now we need to see the name of the current database, so we will be replacing database() instead of 2. We understand that the name is Park database -  <br/>
<img width="887" alt="Screenshot 2025-04-16 at 10 48 47 pm" src="https://github.com/user-attachments/assets/c47269d9-d2a1-450b-a0cd-8581a14d3b92" />
<img width="1435" alt="Screenshot 2025-04-16 at 10 49 58 pm" src="https://github.com/user-attachments/assets/805aa752-d1ad-4b57-a9c6-0cf63e1b2ce9" />

Now, we need to get the Dennis password, for that we can use information schema in our query which will fetch all the table names. Our query is Select 1,table_name,3,4,5 from information_schema.tables where table_schema = "park". After using this query we can see that it is just showing one record, there might be a possibility that there can be multiple records and this query is just showing last record of the database. <br/>
<img width="875" alt="Screenshot 2025-04-16 at 10 52 56 pm" src="https://github.com/user-attachments/assets/a5db3129-98c6-42b3-8da6-391bd6b046f9" />

If we need to fetch the records before the above record from the database, we can use a query called concat which will fetch mutliple records. For doing that, we need to concat the value of records as below - <br/>
<img width="875" alt="Screenshot 2025-04-16 at 10 55 12 pm" src="https://github.com/user-attachments/assets/d445fca1-80da-4885-8400-bde04c7ec395" />
<img width="875" alt="Screenshot 2025-04-16 at 10 56 01 pm" src="https://github.com/user-attachments/assets/9cc4af5c-082a-453e-bf9c-48253ab66053" />

Now that we have found the table name called users package and items. The next step is to find the column name as below - <br/>
<img width="875" alt="Screenshot 2025-04-16 at 10 58 59 pm" src="https://github.com/user-attachments/assets/e1bdb056-69dd-4bde-b1e2-893a0fc6cc82" />

We know that there are total 5 coulmns as below - <br/>
<img width="1412" alt="Screenshot 2025-04-16 at 10 59 38 pm" src="https://github.com/user-attachments/assets/4a3691fd-878f-4d41-9f18-23e6fc5b9919" />

Now, to fetch Denis's password, we again use the concat in our query, but it has given us warning because initially as you remember we cannot use the username in our query as the username string is being blocked <br/>
<img width="888" alt="Screenshot 2025-04-16 at 11 03 33 pm" src="https://github.com/user-attachments/assets/92523f88-503b-4d98-994b-fc1ca495b2fd" />
<img width="888" alt="Screenshot 2025-04-16 at 11 05 56 pm" src="https://github.com/user-attachments/assets/ef54d434-4f7e-4ff7-bb23-1d360a585afd" />
<img width="1417" alt="Screenshot 2025-04-16 at 11 07 58 pm" src="https://github.com/user-attachments/assets/d5194fb7-c5fc-4677-a1fa-4df81a4da39e" />

Once we have got the password, we need perform RCE, for doing that we need to write webshell from where we can call the system. This query also didnt work as shown below - </br>
<img width="922" alt="Screenshot 2025-04-16 at 11 14 33 pm" src="https://github.com/user-attachments/assets/7e0d75b0-9aa5-4c95-81f6-fae9ef7700e7" />

We know the SSH port was open, let see if we can get any information there - </br>
<img width="713" alt="Screenshot 2025-04-16 at 11 17 29 pm" src="https://github.com/user-attachments/assets/69a5a71c-270f-4045-9910-c0c44d42d8f1" />
<img width="713" alt="Screenshot 2025-04-16 at 11 18 57 pm" src="https://github.com/user-attachments/assets/9ec1ecb6-6455-4c95-bbf5-e222b5ba2864" />

The password worked and now we need to search for the flags as mentioned - </br>
<img width="713" alt="Screenshot 2025-04-16 at 11 20 07 pm" src="https://github.com/user-attachments/assets/0a9742ba-e466-4e02-8a38-cbf59c1a1921" />
<img width="713" alt="Screenshot 2025-04-16 at 11 20 49 pm" src="https://github.com/user-attachments/assets/2faf96d9-b484-419e-95da-6e9a96d62d2c" />
<img width="1242" alt="Screenshot 2025-04-16 at 11 22 26 pm" src="https://github.com/user-attachments/assets/423b3f6b-f82d-4151-9482-dccf81ea6004" />

As we have found the flag 1, we need to search for all these files and check if find the other flags </br>
<img width="716" alt="Screenshot 2025-04-16 at 11 23 46 pm" src="https://github.com/user-attachments/assets/8c3e0312-fb64-4601-aa60-bea8a08126a4" />

We need to get perform the below steps for doing scp and getting shell from this website <>

<img width="903" alt="Screenshot 2025-04-16 at 11 25 08 pm" src="https://github.com/user-attachments/assets/a201bff6-7d32-4ff7-bd81-19fb30b7ef5a" />
<img width="708" alt="Screenshot 2025-04-16 at 11 25 57 pm" src="https://github.com/user-attachments/assets/fcef0dcd-da75-402f-a07d-69d2b6aa782f" />
<img width="708" alt="Screenshot 2025-04-16 at 11 40 48 pm" src="https://github.com/user-attachments/assets/b5140777-8e18-4e79-888c-e8513b553e87" />
<img width="708" alt="Screenshot 2025-04-16 at 11 42 48 pm" src="https://github.com/user-attachments/assets/21e464bf-f507-4b27-bfeb-f76d49c2253e" />
<img width="708" alt="Screenshot 2025-04-16 at 11 50 00 pm" src="https://github.com/user-attachments/assets/d3e0bf1b-c386-4aa5-a344-b252f8bdbbb4" />
<img width="1235" alt="Screenshot 2025-04-16 at 11 50 32 pm" src="https://github.com/user-attachments/assets/be628a39-224d-45e8-b2dd-ee375fba18bc" />

We need to find the other flags as below </br>

<img width="704" alt="Screenshot 2025-04-16 at 11 51 24 pm" src="https://github.com/user-attachments/assets/ee863ca5-3236-4d18-988f-26d7d748a74b" />
<img width="704" alt="Screenshot 2025-04-16 at 11 53 14 pm" src="https://github.com/user-attachments/assets/9c05b4dd-de53-42f4-ad61-3bde63529c83" />
<img width="1220" alt="Screenshot 2025-04-16 at 11 54 17 pm" src="https://github.com/user-attachments/assets/7ad50741-9eae-4727-971c-c5c563447129" />
<img width="699" alt="Screenshot 2025-04-16 at 11 54 50 pm" src="https://github.com/user-attachments/assets/08f5cd77-217d-4642-ade4-4663750173b5" />
<img width="699" alt="Screenshot 2025-04-17 at 12 00 02 am" src="https://github.com/user-attachments/assets/16bd1944-20aa-49fa-be9c-443e82d3e6d5" />
<img width="699" alt="Screenshot 2025-04-17 at 12 02 17 am" src="https://github.com/user-attachments/assets/9527bf1e-4112-4c46-b7a9-385543a9ae15" />
<img width="1229" alt="Screenshot 2025-04-17 at 12 05 53 am" src="https://github.com/user-attachments/assets/3670d3e8-9b1e-4012-8c5a-81997e0ee32f" />
<img width="1229" alt="Screenshot 2025-04-17 at 12 05 53 am" src="https://github.com/user-attachments/assets/e9211972-f471-4c8b-a7f4-404502edc677" />
<img width="1229" alt="Screenshot 2025-04-17 at 12 11 44 am" src="https://github.com/user-attachments/assets/fef99f74-4e9e-41f7-9979-259a2ec8b02c" />


Our output is as below </br>
<img width="1229" alt="Screenshot 2025-04-17 at 12 12 09 am" src="https://github.com/user-attachments/assets/898b03c1-4921-4ec8-8156-b707be9564c0" />
<img width="1252" alt="Screenshot 2025-04-17 at 12 12 20 am" src="https://github.com/user-attachments/assets/06110838-f00b-49c7-8839-609bf90aafa3" />
