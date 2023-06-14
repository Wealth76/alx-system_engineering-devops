<h1 font-family: sans-serif;>0x09-Postmortem</h1>
        
<img src="https://camo.githubusercontent.com/7f427f06243ae054b44def810f654257960cab96ad54b07a65b22b2c69d8e6dd/68747470733a2f2f6d69726f2e6d656469756d2e636f6d2f6d61782f313430302f302a6b486f574437674a30504339476d424b2e6a7067">
<h1>Issue Suummary</h1>
 <p></p>
 <p>16/02/2022 From 9:15 AM to 10:00 AM UTC+1 all requests for the homepage to our servers got a 404 response</p>
 <p></p>
<h1>Timeline</h1>
 <li>9:10 AM : Updates push</li>
 <li>9:15 AM : Noticing the problem</li>
 <li>9:15 AM : Notifying the both front end and backend teams</li>
 <li>9:20 AM : Successful change rollback</li>
 <li>9:24 AM : Server Restarts begin</li>
 <li>9:27 AM : 100% of traffic back online</li>
 <li>9:30 AM : start debugging the push with the problem</li>
 <li>9:50 AM : Probelm fixed and pushed the changes</li>
 <li>9:55 AM : Server restart begins</li>
 <li>10:00 AM : 100% traffic back online with the new updates</li>
<h1>Root cause and resolution</h1>
  <p>After rolling back changes we knew that the changes were made by the front end team so we took the broken changes and run them on a test server which replicated same problem, our server uses apache2 and apache2 error logs didn't give enought infomation about the problem so we traced the apache2 process using strace and when a request is sent strace tool catchs a lot of error and after some scaning fo these errors we found the error wich is a typo in page file extention ></p>
  <p>.phpp</p>
  <p>instead of</p>
  <p>.php</p>
  <p>and to fix that we just search in our main directory using grep for that typo</p>
  <p>grep -inR ".phpp" .</p>
  <p>after fixing the error we pushed back the changes and restarted the servers</p>
  <li>10:00 AM : 100% of trafic back online with the new updates</li>
<h1>Corrective and preventative measures</h1>
  <p>To prevent similar problems from happening again we will</p>
  <li>Create an automated test pipeline for every update push</li>
  <li>Add a monitoring software to our servers which will monitor lot of things and one of them Network Traffic resquests and responses and configure it to make an lert to the teams when too much non desired responses were sent like 404</li>
  <li>Create a tests for every new update and the teams shouuld not push until those tests pass</li>
