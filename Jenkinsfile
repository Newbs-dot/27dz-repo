pipeline {
	agent any
	parameters {
		string(name: 'STUDENT_NAME', defaultValue: 'MatsulevichMaksim')
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
				MY_VAR = params.STUDENT_NAME 
				sh 'python hello.py --name=${MY_VAR} > result.txt'
			}
		}
		stage("archive") {
			steps {
				archiveArtifacts artifacts: 'result.txt'
			}
		}
	}
}
