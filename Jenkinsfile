node {
    sh "find . | sed -e '1d' |xargs rm -rf"
    if(env.TAG_NAME ==~ ".*") {
      env.branch_name = "refs/tags/${env.TAG_NAME}"
    } else {
      env.branch_name = "${env.BRANCH_NAME}"
    }
    checkout scmGit(
        branches: [[name: branch_name]],
        userRemoteConfigs: [[url: "https://github.com/hemanthtadikonda/cart"]]
    )
    properties([
        parameters([
            [$class     : 'PasswordParameterDefinition',
             name       : 'SONARPASSWORD',
             description: "Enter your password"
            ],
        ]),
    ])

   stage('compile code') {
      print 'ok'
      sh "echo ${params.PERSON}"
      sh "echo ${params.SONARPASSWORD}"
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
