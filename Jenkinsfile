pipeline {
   agent any
   options { skipDefaultCheckout() } 
   triggers { scm('* * * * *') }
   stages {
       stage("checkout") {
           steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/ready/**']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout'], pretestedIntegration(gitIntegrationStrategy: squash(), integrationBranch: 'master', repoName: 'origin')], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/praqma-test/pretested-integration-plugin-test-repo.git']]])
           }
       }
       stage("publish") {
           steps {
               pretestedIntegrationPublisher()
           }
       }
   }
}
