def stepsToRun = [:]

pipeline {
    agent none

    stages {
        stage ("Prepare Stages"){
            steps {
                script {
                    for (int i = 1; i < 5; i++) {
                        stepsToRun["Step${i}"] = prepareStage("Step${i}")
                    }   
                    parallel stepsToRun
                }
            }
        }
    }
}

def prepareStage(def name) {
    return {
        stage (name) {
            stage("1") {
                echo "start 1"
                sleep 1
                echo "done 1"
            }
            stage("2") {
                echo "start 2"
                sleep 1
                echo "done 2"
            }
        }
    }
}
