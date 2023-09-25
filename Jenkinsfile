node {
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

   stage('compile code') {
      print 'ok'
      sh 'echo "Hello ${params.PERSON}"'
      sh 'echo "Password: ${params.PASSWORD}"'
      // sh 'compile code depends on code type'
   }

   if (env.BRANCH_NAME ==~ ".*" && env.TAG_NAME == null) {
      stage('test code') {
         print 'Ok'
      }
   }
   if (env.BRANCH_NAME == "main") {
      stage('code Quality') {
         print 'Ok'
         // sh 'sonar command'
      }
   }
   if (env.BRANCH_NAME == "main" && env.TAG_NAME == null) {
      stage('code security') {
         print 'Ok'
         // sh 'checkmarx sca & sast'
      }
   }
   if  (env.TAG_NAME ==~ ".*") {
      stage('Release') {
         print 'Ok-OK'
         // sh 'nexus upload command'
      }
   }
}
