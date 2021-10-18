pipeline {
    environment {
        KEY_PASSWORD = credentials('keyPassword')
        KEY_ALIAS = credentials('keyalias')
        KEYSTORE = credentials('keystore')
        STORE_PASSWORD = credentials('storePassword')
    }
    agent any   
    stages {
        stage('Fetch')
        {
            steps
            {
                git url : "https://github.com/Shilpa40/react-native-app.git"
            }
        }
        
        stage('Build Bundle') {
            steps {
                echo 'Building'
                script {
                    bat ".\gradlew -PstorePass=${STORE_PASSWORD} -Pkeystore=${KEYSTORE} -Palias=${KEY_ALIAS} -PkeyPass=${KEY_PASSWORD} bundlemaster"
                }
            }
        }
    }
}
