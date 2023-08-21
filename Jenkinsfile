pipeline {
	agent any
	parameters {
		string name: 'STUDENT_NAME', defaultValue: 'MatsulevichMaksim'
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
				sh 'python hello.py --name ${STUDENT_NAME} > result.txt'
			}
		}
		stage("archive") {
			steps {
				archiveArtifacts artifacts: 'result.txt'
			}
		}
	}
}
