pipeline {
	agent any
	parameters {
		string(name: 'STUDENT_NAME', defaultValue: 'МацулевичМаксим')
	}
	
	triggers {
		pollSCM('* * * * *')
	}
	
	stages {
		stage("install") {
			steps {
				sh 'pip install -r requirements.txt'
			}
		}
		stage("run") {
			steps {
				sh 'python hello.py --name=${params.STUDENT_NAME} > result.txt'
			}
		}
	}
	post {
        always {
            archiveArtifacts artifacts: 'result.txt'
        }
    }
}