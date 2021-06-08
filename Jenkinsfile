pipeline
	{
		agent any 
			tools {
				maven 'M3'
			}
			stages 
				{
					stage ('Git Pull')
						{
							steps
								{
									git 'https://github.com/showmikb/samplespringboot.git'
								}
						}	
					
					stage ('Build')
						{
// 							when 
// 								{
// 									$env.branch "master"
// 								}
							steps
								{
									sh 'mvn clean package'
								}
							
						}
						
// 					stage ('SonarScan')
// 						{
// 							environment
// 								{
// 									scannerHome = tool 'sonarqube'
// 								}
// 							steps
// 								{
// 									withSonarQubeEnv('sonarqube') 
// 									{
// 										sh "${scannerHome}/bin/sonar-scanner"
// 									}
// 									timeout(time: 10, unit: 'MINUTES') {
// 										waitForQualityGate abortPipeline: true
// 									}
// 								}
// 						}
				}
			
		
	}
