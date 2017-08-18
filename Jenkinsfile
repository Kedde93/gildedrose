node {
    stage ('Github'){
        git checkout scm
    }

    stage ('Maven'){
        sh 'docker run -i --rm -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn install'    
    }

    stage ('Results'){
        junit '**/target/surefire-reports/TEST-*.xml'
    }
    
    stage ('Save'){
        archiveArtifacts '**/target/surefire-reports/TEST-*.xml'
    }
    
    stage ('Javadoc'){
        sh 'docker run -i --rm -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'    
        archiveArtifacts 'target/site/'
    }
    
    stage ('Save Jar'){
        archiveArtifacts 'target/gildedrose-*.jar'
        
    }
    

}
