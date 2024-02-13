pipeline {
    agent any

    stages {
        stage('Creating an Image') {
            steps {
                bat "docker build -t=testcaseimage ."
            }
        }
        stage('Making an Infrastructure UP') {
            steps {
                bat "docker-compose up hub chrome edge firefox"
            }
        }

        stage('Running Test Cases') {
            steps {
                bat "docker-compose up testcaseimage"
            }




post {
        always {

            emailext attachLog: true, attachmentsPattern: 'Chrometestreports/cucumber-reports/reports.html', body: '''Hey Team,
<p>Here is the details of Execution through Jenkins<br>

$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:<br>

Check console output at $BUILD_URL to view the results.<br>

Thanks,<br>
Automation Team - ATT 19-August <h3>(Himanshu)</h3>''', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS! - Execution of Maven project on Mozila FireFox Browser', to: 'himanshudalal76247@gmail.com'
        }
    }
        }

       
        

     
        
  }

}
