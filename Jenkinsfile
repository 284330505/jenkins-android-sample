pipeline{
    agent {
        docker {
            image 'registry.cn-hangzhou.aliyuncs.com/my02/jenkins-android:1.0.1' //①
        }
    }

    stages {
        stage('Build'){
             steps {
                sh './gradlew clean && rm -rf ./app/build/' //②
                sh './gradlew assembleRelease'  //③
             }
         }

       stage('UnitTest'){
             steps {
                sh './gradlew test'
             }
        }
          stage('Archive') {  
            steps {
                archiveArtifacts artifacts: 'app/build/outputs/**/*.apk', fingerprint: true 
           }
        }

    }

}
