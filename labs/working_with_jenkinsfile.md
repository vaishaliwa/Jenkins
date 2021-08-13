### Create Pipeline job in Jenkins
1. Go Jenkins Dashbaord & selecy `New item`.
2. Add `Name` as `firstPipeline` and select `Pipeline` Options and click OK.
3. Scroll to `Pipeline` and select `Hello World` under `try Sample pipeline`
4. Click `Save` & then Click `Build Now`
### Sample code for Hello World
```
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
```
![Single_stage](https://github.com/kul-samples/jenkins/blob/main/labs/Single_stage.PNG?raw=true)

### Adding more stages to the pipeline
1. Configure your build
2. Go to pipeline & update pipeline code with below code:
```
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('How are you?') {
            steps {
                echo 'How are you?'
            }
        }
    }
}
```
![multiple_stages](https://github.com/kul-samples/jenkins/blob/main/labs/multiple_stages.PNG?raw=true)

### Adding parallel stages in Jenkinsfile
1. update pipeline code with below code:
```
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('How are you?') {
            steps {
                echo 'How are you?'
            }
        }
        stage ('SAST'){
          parallel{
            stage ('sonar-scan'){
              steps {
                echo 'Running Sonar Scan'
              }
            }
            stage ('synk-scan'){
              steps {
                echo 'Synk scan'
              }
            }
            stage ('DC'){
              steps {
                echo 'Running Dependency Check'
              }
            }
          }
        }
    }
}
```

### Take Pipeline from SCM (GITHUB)
1. Edit the build and select Definition as `Pipeline Script from SCM` under pipeline
2. Under SCM select `Git`
3. Under `Repository URL` add Github repo where Jenkinsfile is avaiable, `https://github.com/kul-samples/jenkins.git`
4. Under `Credentials` select `Github-creds`
5. Under `Branches to build` add `*/main`
6. Under `Script Path` add the name of pipeline script, like `Jenkinsfile`
### Sample stage view
![Declarative_SCM-Checkout](https://github.com/kul-samples/jenkins/blob/main/labs/declarative_scm_checkout.PNG?raw=true)

### Using pipeline syntax
1. Go to the pipline build `http://18.191.185.219:8080/job/firstPipeline/`
2. Select `Pipeline Syntax`. Select `Snippet Generator`.
3. Under `Sample Step` select `git: Git`
4. Add `Repository URL` as `https://github.com/kul-samples/java_sample_webapp.git`, `branch` as `main`, `Credentials` as `Github credentials`.
5. Click on `Generate Pipeline Script` to prepare pipeine step.
6. Copy the synxtax and add the same in Jenkinsfile using below code:
```
stage ('Checkout Java Code'){
  steps{
    git branch: 'main', credentialsId: 'GITHUB-CREDS', url: 'https://github.com/kul-samples/java_sample_webapp.git'
  }
}
```
### Run builds on specfifc agents using labels unders agent tag
```
agent {
  label 'linux'
}
```

### Installing tool for maven builds
1. Go to Jenkins Dashboard
2. Select `Manage Jenkins`
3. Select `Global Tool Configuration`
4. Under `Maven`. Click `Add Maven`.
5. Add `Name` as `mvn_3.8.1`
6. Select `Install automatically` & Select `3.8.1` in `Version`. Click `Save`

### Update Jenkinsfile to use Installed maven version during the build
```
tools {
  maven 'mvn_3.8.1'
}
```
