jenkins-maven-test
==================

SonarQube Project Setup
-----------------------

1. Open `http://localhost:9000`.
2. Login with user: `admin`, password: `admin`.
3. Click `+` then select `Create new project` link.
4. Set `Project key` to `jenkins-maven-test`.
5. Click `Set Up` button.
6. Set token name to `jenkins-token`.
7. Click `Generate` button.
8. Copy token and store somewhere secure.
9. Click `Continue` button.
10. Click `Java` button.
11. Click `Maven` button.
12. Copy `mvn sonar:sonar` code and store somewhere secure.


Jenkins Project Setup
---------------------

1. Click `New Item` link.
2. Fill in `Enter an item name` with `jenkins-maven-test`.
3. Click `Maven project`.
4. Click `OK` button.
5. Click `Git` for Source Code Management.
6. Enter `https://github.com/Algoritics/jenkins-maven-test.git`.
7. Fill `Build` -> `Goals and option` with `clean install`.
8. Click `Add post-build step`.

**Setup using SonarScanner Plugin:**

9. Fill `Path to project properties` with `sonar-project.properties`.
10. Enter project key and login in `Analysis properties` textbox. Example:

```
sonar.projectKey=jenkins-maven-test
sonar.login=ba7a9af4518eea0acb77a6b7fc19ea01a13d2f7e
```

11. Click `Save` button.
12. Click `Build Now` button to verify working.

**Setup using Maven SonarScanner:**

9. Select `Invoke top-level Maven targets`.
10. Set `Goals` to (replace login with generated sonar token):

```
sonar:sonar -Dsonar.projectKey=jenkins-maven-test -Dsonar.host.url=http://sonarqube:9000 -Dsonar.login=ba7a9af4518eea0acb77a6b7fc19ea01a13d2f7e
```

11. Click `Save` button.
12. Click `Build Now` button to verify working.


Free software: MIT license
