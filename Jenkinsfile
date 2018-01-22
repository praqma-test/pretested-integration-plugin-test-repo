pipeline {
   agent any
   options { skipDefaultCheckout() } 
   stages {
       stage("checkout") {
           steps {
		echo "Hellow from some stage"
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
