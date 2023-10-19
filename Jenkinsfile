node {
    def var1
    stage('checkout'){
        git branch: 'main', url: 'https://github.com/Vasudeva22/WebApp.git'
    }
    stage('build'){
        sh 'mvn clean package'
    }
    stage('upload to artifactory'){
        nexusArtifactUploader artifacts: [[artifactId: 'WebApp', classifier: '', file: '/root/.jenkins/workspace/pipeline/target/WebApp.war', type: 'war']], credentialsId: '890f2357-eec0-445a-af2c-21e4455509f8', groupId: 'google', nexusUrl: '192.168.0.160:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '1.0-SNAPSHOT'
    }
    stage('security scan'){
        
    }
    stage('Deploy to Prod'){
        sh 'cp /root/.jenkins/workspace/pipeline/target/WebApp.war  /root/tomcat/apache-tomcat-9.0.80/webapps'
    }
}
