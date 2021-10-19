pipeline {
    class Constants {
    static final String MASTER_BRANCH = 'master'
    static final String RELEASE_BUILD = 'Release'

}

    environment {
        KEY_PASSWORD = credentials('keyPassword')
        KEY_ALIAS = credentials('keyalias')
        KEYSTORE = credentials('keystore')
        STORE_PASSWORD = credentials('storePassword')
    }
    
    def getBuildType() {
            switch (env.BRANCH_NAME) {
                case Constants.MASTER_BRANCH:
                 return Constants.RELEASE_BUILD
                default:
                    return Constants.RELEASE_BUILD
    }
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
                 script {
                    VARIANT = getBuildType()
                    bat ".\gradlew -PstorePass=${STORE_PASSWORD} -Pkeystore=${KEYSTORE} -Palias=${KEY_ALIAS} -PkeyPass=${KEY_PASSWORD} bundle${VARIANT}"
                }
            }
        }
    }
}
