// Powered by Infostretch 

timestamps {

node () {

	stage ('projet-packaging - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b17cc096-ab2b-4662-a8f3-ccdf9ff43fb8', url: 'https://github.com/ArnaudS-A5/Spring-Boot-Hello-World-Example.git']]]) 
	}
	stage ('projet-packaging - Build') {
 			// Maven build step
	withMaven(maven: 'Maven') { 
 			if(isUnix()) {
 				sh "mvn clean package " 
			} else { 
 				bat "mvn clean package " 
			} 
 		} 
	}
	stage ('projet métrique - Build') {
 	
withEnv(["JAVA_HOME=${ tool '"+JDK+"' }", "PATH=${env.JAVA_HOME}/bin"]) { 
		// Maven build step
	withMaven(jdk: '(Hérite du job)', maven: 'Maven') { 
 			if(isUnix()) {
 				sh "mvn clean test pmd:check findbugs:check checkstyle:checkstyle " 
			} else { 
 				bat "mvn clean test pmd:check findbugs:check checkstyle:checkstyle " 
			} 
 		}
// Unable to convert a build step referring to "hudson.plugins.sonar.SonarRunnerBuilder". Please verify and convert manually if required. 
	}
}
	stage ('projet-livraison - Build') {
 			// Maven build step
	withMaven(maven: 'Maven') { 
 			if(isUnix()) {
 				sh "mvn clean install " 
			} else { 
 				bat "mvn clean install " 
			} 
 		}
// Unable to convert a build step referring to "jenkins.plugins.publish__over__ssh.BapSshBuilderPlugin". Please verify and convert manually if required. 
	}
	stage ('projet deploy - Build') {
 	
// Unable to convert a build step referring to "jenkins.plugins.publish__over__ssh.BapSshBuilderPlugin". Please verify and convert manually if required. 
	}
	stage ('projet-selenium - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b17cc096-ab2b-4662-a8f3-ccdf9ff43fb8', url: 'https://github.com/ArnaudS-A5/example-springboot-automation-test-selenium.git']]]) 
	}
	stage ('projet-selenium - Build') {
 			// Shell build step
sh """ 
chmod +x driver/chromedriver.exe;
mvn clean verify 
 """		// Maven build step
	withMaven(maven: 'Maven') { 
 			if(isUnix()) {
 				sh "mvn clean verify surefire-report:report-only " 
			} else { 
 				bat "mvn clean verify surefire-report:report-only " 
			} 
 		} 
	}
	stage ('projet-tests - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b17cc096-ab2b-4662-a8f3-ccdf9ff43fb8', url: 'https://github.com/ArnaudS-A5/Spring-Boot-Hello-World-Example.git']]]) 
	}
	stage ('projet-tests - Build') {
 			// Maven build step
	withMaven(maven: 'Maven') { 
 			if(isUnix()) {
 				sh "mvn clean test " 
			} else { 
 				bat "mvn clean test " 
			} 
 		}
		// JUnit Results
		junit '**/target/surefire-reports/*.xml' 
	}
	stage ('projet-livraison - Build') {
 			// Maven build step
	withMaven(maven: 'Maven') { 
 			if(isUnix()) {
 				sh "mvn clean install " 
			} else { 
 				bat "mvn clean install " 
			} 
 		}
// Unable to convert a build step referring to "jenkins.plugins.publish__over__ssh.BapSshBuilderPlugin". Please verify and convert manually if required. 
	}
	stage ('projet deploy - Build') {
 	
// Unable to convert a build step referring to "jenkins.plugins.publish__over__ssh.BapSshBuilderPlugin". Please verify and convert manually if required. 
	}
	stage ('projet-selenium - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b17cc096-ab2b-4662-a8f3-ccdf9ff43fb8', url: 'https://github.com/ArnaudS-A5/example-springboot-automation-test-selenium.git']]]) 
	}
	stage ('projet-selenium - Build') {
 			// Shell build step
sh """ 
chmod +x driver/chromedriver.exe;
mvn clean verify 
 """		// Maven build step
	withMaven(maven: 'Maven') { 
 			if(isUnix()) {
 				sh "mvn clean verify surefire-report:report-only " 
			} else { 
 				bat "mvn clean verify surefire-report:report-only " 
			} 
 		} 
	}
}
}