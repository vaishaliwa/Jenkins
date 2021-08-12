### Create Pipeline job in Jenkins
1. Go Jenkins Dashbaord & selecy `New item`.
2. Add `Name` as `firstPipeline` and select `Pipeline` Options and click OK.
3. Scroll to `Pipeline` and select `Hello World` under `try Sample pipeline`
4. Click `Save`
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
