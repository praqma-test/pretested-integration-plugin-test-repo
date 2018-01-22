pipeline {
   agent any
   options { skipDefaultCheckout() }
   stages {
       stage("checkout") {
           steps {
		checkout([$class: 'GitSCM', branches: [[name: '*/ready/**']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout'], pretestedIntegration(gitIntegrationStrategy: squash(), integrationBranch: 'master', repoName: 'origin')], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/praqma-test/pretested-integration-plugin-test-repo.git']]])
		sh 'cat testOutput.txt'
           }
       }
       stage("publish") {
           steps {
               pretestedIntegrationPublisher()
           }
       }
   }
}
