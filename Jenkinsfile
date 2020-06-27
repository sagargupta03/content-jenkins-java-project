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
			// sh 'ant -f build.xml -v' //
                  	echo 'Building..'			
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
