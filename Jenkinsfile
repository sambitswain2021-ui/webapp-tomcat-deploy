pipeline{
 tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
     agent any
	  
	  stages{
	  
	  stage("checkout"){
	   steps{
	   git 'https://github.com/sambitswain2021-ui/webapp-tomcat-deploy.git'
	   }
	                  }
	
	   stage("compile"){
	    steps{
		 sh 'mvn compile'
		}
		}
       stage("test"){
	    steps{
		 sh 'mvn test'
		}
		}
	
       stage("package"){
	    steps{
		 sh 'mvn clean package'
                 sh "mv target/*.war target/myweb.war"

		}
		}
stage(backup)
		  {
  steps{

	//nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'target/myweb.war', type: 'war']], credentialsId: 'nexus', groupId: 'com.idream', nexusUrl: '13.126.178.102:8081/repository/maven-releases/', nexusVersion: 'nexus2', protocol: 'http', repository: 'maven-releases', version: '1.5'
	sh 'mvn deploy'
  }
	
}
	}
	}
