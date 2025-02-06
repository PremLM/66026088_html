pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
				//แก้ตรง 66026088_html ให้เป็นชื่อเดียวกับ pipeline job/item ที่สร้างใน jenkins
                sh "scp -r /var/lib/jenkins/workspace/66026088_html/* root@43.208.241.236:~/66026088_html"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66026088_html/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66026088_html/playbooks/deploy.yaml'
            }    
        } 
    }
}
