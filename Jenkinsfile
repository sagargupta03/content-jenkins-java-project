pipeline
{
	agent any
	 environment {
        MAJOR_VERSION = 1
          } 
	stages
	{
	  
		stage('Unit Tests') {
       
      steps {
           sh 'ant -f test.xml -v'
           junit 'reports/result.xml'
         }
    }
		stage('Build') 
		{
		steps {
			echo 'Ant Build from build.xml step added in Building..' 
			sh 'ant -f build.xml -v' 
                  				
		      }
			post {
                           success {
				   echo 'result of build.xml is success '
                                archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
                              }
      }
		}
		stage('Test')
		{
		steps {
		echo 'Testing..'
		      }
		}
		stage('Deploy')
		{
                
                steps {
		echo 'Deploying....'
		      }
		}
	}
}
