# Jenkins Tutorial

------
**UserName: Liang**
**PWD     : 9--------9**

### 1. Jenkin User Management
Manage User -> 
	Create User for Developer or Admin
role-based plugin -> 
	Can not show on the download list
	
### 2. Blue Ocean Plugin
Quite easy step to combine Jenkins and GitHub with the default navigation to create the hook.

Things need to be remembered, 
	i) it will generate the personal access token on the Github website
		Setting -> Developer settings -> Personal access token

   ii) hard to find where to config that new pull request comes then build, 
   		so use Scan Repository Triggers 1 mins to work around. Scan Repository Now
   
### 3. This big image is three containers

 | DB        | Jenkin   |  Maven/Tomcat  |
| --------   | -----:   | :----:         |
|   5432     | 8080     |        8080    |

Shell file is executed on the Maven Tomcat container, 
Then, no need to expose 8080(Tomcat) to external, 
http://localhost:8080 is just runned on the internal container

### 4. Jenkins Mail Configuration
		1. E-mail Notification 
		this one can be used to test the configuration is successful or not.

		2. Jenkins Location
		this one should be fullfilled the admin mail address.(must)

		3. Extended E-mail Notification
		this one is cnfigurated for Jenkins mail because you choose extended mail on the blue ocean
		pipeline job.
	
		you need to open qq.mail smtp mail service.
		that means use qq mail server as your Jenkins sender mail address.
		the following the pwd from qq server.
		bswqpxncxgjibcdg
		adapznkpecnzbcbi

### 5. Jenkinfile
Jenkins file is configured for Jenkins,
If the branch include the Jenkinsfile, then Jenkins can automatically scan this branch to build based on the piple line.

So this file can be auto generated by Blue Ocean(not cover everything) or hand write.

Blue Ocean will auto scan the Jenkinfile from your branch.

In order to success or fail job to receive the email, I need to add post for the Jenkins.
But unfortunately blue ocean seems no API to add based on the writting time.

The confusing is the setting, anyway google is fine.

### 6. maven:3-alpine
maven:3-alpine need to be downloaded pre-requsitely because of avoiding downloading taking
too much time with internet-issue and make Jenkins down.
There is one Test need to be tested when back to NZ.

- [ ] **Need to Test One Case on yml**

### 7. Comman to Test
    1. Mac ip
    ifconfig | grep inet

    nslookup localhost

    2. to see one port among Mac 
    lsop -i tcp:8080

    3. lsof -i tcp:8080   -> you can know the pid, but you may dont know what is the pid doing
    ps -ef | grep pid  
	-> you can know what the pid is doing

    ps -ef | grep pid | grep -v grep 
	-> grep -v grep: eliminate the result contains grep character

    ps -ef | grep spring-boot:run | grep -v grep | awk '{print $2}' 
	-> awk read the one row info and print the second column info


shell how to arrange one variable
ps -ef | grep spring-boot:run | grep -v grep | awk '{print $2}'

put the above command into the character
PID=``  
PID=$()
