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
					stage('1-analysis'){
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
					sh 'free -m'
				}
			}
			stage('4a-closing1'){
				agent{
					label 'slave2'
				}
				steps{

					echo "SATZENBREAU, The Final Word"
				}
			}
			stage('4b-closing2'){
				steps{
					sh 'wc -l'
					sh 'wc -w'
				}
			}
		}
}