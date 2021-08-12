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
