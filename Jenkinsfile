pipeline{
    agent any
    stages{
        stage('Making Grid UP'){
            steps{
                bat "docker-compose -f grid.yaml up -d"
            }

        }

        stage('Running Tests'){
            steps{
                bat "docker-compose -f test_suite.yaml up"
            }

        }
      

    }
    post{
        always{
            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test_suite.yaml down"
			archiveArtifacts artifacts: "output/vendorportal/emailable-report.html", followSymlinks: false
            archiveArtifacts artifacts: "output/flightregistration/emailable-report.html", followSymlinks: false
        }
    }
   
}