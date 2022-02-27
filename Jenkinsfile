pipeline{
    agent any
    stages{
        stage('SCM')
        {
            steps{git credentialsId: 'github_credentials', url: 'https://github.com/Shahiraws/spring3-mvc-maven-xml-hello-world.git' }
        }
        
        stage('Build')
        {
            steps{sh 'mvn -Dmaven.test.failure.ignore=true clean package' }
        }
        
        stage('Artifacts')
        {
            steps{archiveArtifacts 'target/*.war' }
        }
        
        stage('Deploy')
        {
            steps{sh "curl -v -u admin:adminadmin -T /var/lib/jenkins/workspace/spring3/target/spring3-mvc-maven-xml-hello-world-1.0-SNAPSHOT.war 'http://ec2-3-88-108-82.compute-1.amazonaws.com:8080/manager/text/deploy?path=/shahir&update=true'" }
        }
        
        
    }
    }

      
