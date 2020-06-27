pipeline
{
	agent any
	 environment {
        MAJOR_VERSION = 1
          } 
	stages
	{
	  
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
