node('linux'){
    stage('Test'){
        sh 'ant -f test.xml -v'
    }
    stage('Build'){
        sh 'ant -f build.xml -v'
    }
    stage('Deploy'){
        sh 'aws s3 cp ./dist/rectangle-*.jar s3://w10assignment/'
    }
    stage('Report'){
    	withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'e4249e21-63b6-41f6-b4e1-d4f94817c680', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
 			sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins' 
    	}
    }
    
}
