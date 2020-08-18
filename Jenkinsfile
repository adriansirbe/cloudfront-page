node('node'){
   stage('git checkout'){
      try {
      git credentialsId: 'git-token', url: 'https://github.com/adriansirbe/cloudfront-page.git/'
      } catch(err) {
         sh "echo error in checkout"
      }
   }

stage('upload to s3') {
      try {
      // you need cloudbees aws credentials
      withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'deploytos3', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
         sh "aws s3 ls"
         sh "aws s3 cp cloudfront-page/index.html s3://basic-web-application-2020/"
         }
      } catch(err) {
         sh "echo error in sending artifacts to s3"
      }
   }
}