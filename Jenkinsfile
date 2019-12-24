pipeline {
    agent any
    stages{
        stage('clone the repo and removing the existing one')
        {
          steps {
              sh "sudo rm -rf /home/flobos/project"
              sh "cd /home/flobos/"
              sh "mkdir -p /home/flobos/project"
              sh "cd /home/flobos/project"
              sh "git clone https://github.com/flobos/jenkins_pipeline.git /home/flobos/project"
               
               }
         }
         
         stage("copying files to /var/www/html")
         {
           steps 
           {
              sh "sudo cp /home/flobos/project/www/html/index.html /var/www/html/"
           }
          }
          
           stage("Installing the webserver and starting its service")
          {
            steps
            {
              sh "sudo apt install apache2 -y"
              sh "sudo systemctl start apache2"
            }
          }
          
          
          stage("Restarting the apache2 service")
          {
            steps
            {
              sh "sudo systemctl restart apache2"
            }
          }
               
    }

}
