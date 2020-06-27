pipeline
{
	agent any
	 environment {
                 MAJOR_VERSION = 1
		 //hardcoded for now - need to remove below line//
		 BRANCH_NAME = 'master'
		 //hardcoded -need to change for each agent//
		 NODE_IP = 'http://54.146.16.37:8080'
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
			        echo "env.USER $env.USER"
                    sh "if ! [ -d '/var/www/html/rectangles/all/${env.BRANCH_NAME}' ]; then sudo mkdir -p /var/www/html/rectangles/all/${env.BRANCH_NAME}; fi"
                    sh "sudo cp dist/rectangle_${env.MAJOR_VERSION}.${env.BUILD_NUMBER}.jar /var/www/html/rectangles/all/${env.BRANCH_NAME}/"
				
		      }
		}
	      stage("Running on CentOS") {
     
              steps {
		      echo "wget -6 ${env.NODE_IP}/rectangles/all/${env.BRANCH_NAME}/rectangle_${env.MAJOR_VERSION}.${env.BUILD_NUMBER}.jar"
		      echo "java -jar rectangle_${env.MAJOR_VERSION}.${env.BUILD_NUMBER}.jar 3 4"
		      sh "wget -6 ${env.NODE_IP}/rectangles/all/${env.BRANCH_NAME}/rectangle_${env.MAJOR_VERSION}.${env.BUILD_NUMBER}.jar"
                      sh "java -jar rectangle_${env.MAJOR_VERSION}.${env.BUILD_NUMBER}.jar 3 4"
                    }
               }
		
	}
}
