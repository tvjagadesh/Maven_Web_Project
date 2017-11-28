#!groovy

node {
    currentBuild.result = "SUCCESS"

    try {

       stage('Checkout'){

          checkout scm
       }

       stage('Compiling'){

          bat 'mvn deploy'
       }
	   
      stage('Sonar') {
                    //add stage sonar
                    bat 'mvn sonar:sonar'
                }
       stage('mail'){

         mail body: 'project build successful',
                     from: 'ramireddygangadhar@gmail.com',
                     replyTo: 'gangadhardevops@gmail.com',
                     subject: 'project build successful',
                     to: 'gangadhardevops@gmail.com'
       }

    }
    catch (err) {

        currentBuild.result = "FAILURE"

            mail body: "project build error is here: ${env.BUILD_URL}" ,
            from: 'ramireddygangadhar@gmail.com',
            replyTo: 'gangadhardevops@gmail.com',
            subject: 'project build failed',
            to: 'gangadhardevops@gmail.com'

        throw err
    }
}
