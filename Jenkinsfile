pipeline
{
	agent any
	 environment {
        MAJOR_VERSION = 1
		 //hardcoded for now - need to remove below line//
		 BRANCH_NAME = master
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
			 echo "env.BRANCH_NAME  $env.BRANCH_NAME"
                                echo "env.BUILD_NUMBER  $env.BUILD_NUMBER"
		                echo 'Deploying....'
                    sh "if ! [ -d '/var/www/html/rectangles/all/${env.BRANCH_NAME}' ]; then mkdir -p /var/www/html/rectangles/all/${env.BRANCH_NAME}; fi"
                    sh "cp dist/rectangle_${env.MAJOR_VERSION}.${env.BUILD_NUMBER}.jar /var/www/html/rectangles/all/${env.BRANCH_NAME}/"
				
		      }
		}
	}
}
