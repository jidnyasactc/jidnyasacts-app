pipeline{
	agent{
		label{
			label "build-in"
		}
	}
	stages{
		stage("Install-httpd"){
			steps{
				sh '''
					sudo yum install httpd -y
					sudo systemctl start httpd
					sudo systemctl enable httpd
				'''
			}
		}
		stage("Git-Checkout"){
			steps{
				sudo rm -rf *
				git 'https://github.com/jidnyasactc/jidnyasacts-app.git'
			}
		}
		stage("deploy-app"){
			steps{
				sh '''
					cp index.html /var/www/html
					sudo chmod -R 777 /var/www/html/
					sudo systemctl restart httpd
				'''
			}
		}
	}
}
