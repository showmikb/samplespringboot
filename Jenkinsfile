def projectName = 'ShowmikApp'
def branchName = env.BRANCH_NAME

pipeline
	{
		agent any 
			{
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
								when 
									{
										branch "master"
									}
								steps
									{
										mvn clean package
									}
								
							}
							
						stage ('SonarScan')
							{
								environment
									{
										scannerHome = tool 'sonarqube'
									}
								steps
									{
										withSonarQubeEnv('sonarqube') 
										{
											sh "${scannerHome}/bin/sonar-scanner"
										}
										timeout(time: 10, unit: 'MINUTES') {
											waitForQualityGate abortPipeline: true
										}
									}
							}
					}
				
			}
	}