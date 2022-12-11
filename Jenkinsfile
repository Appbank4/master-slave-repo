pipeline{
	agent{
		label 'slave1'
	}
		stages{
			stage('1-clone'){
				steps{
					sh 'cat /etc/passwd'
				}
			}
			stage('2-parallel jobs'){
				parallel{
					stage('1-subjob1'){
						steps{
							sh 'lscpu'
						}
					}
					stage('2-subjob2'){
						when {
							branch 'feature'
						}
						steps{
							sh 'df -h'
							sh 'free -g'
						}
					}

				}
			}
			stage('3-codetest'){
				agent {
					label 'slave1'
				}
				steps{
					sh 'pwd'
				}
			}
			stage('4-closing'){
				agent{
					lebel 'slave2'
				}
				steps{

					echo " We are done here"
				}
			}
		}
}