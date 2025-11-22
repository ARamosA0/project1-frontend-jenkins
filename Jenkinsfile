pipeline {
    agent { 
        docker { 
            image 'node:20'
            args '-u root'
        } 
    }

    environment {
        VERCEL_TOKEN = credentials('vercel_token')
        VERCEL_PROJECT = 'prj_A6fLDaRL7JVVxuU9hXZXyW2PI6nM'
    }
  
    stages {
        stage('Instalar dependencias ...') {

            steps {
                echo 'Instalando dependencias'
                sh 'npm install'
            }
        }

        stage('Ejecutar pruebas unitarias') {

            steps {
                echo 'Ejecutando tests'
                sh 'npm test || true'
            }
        }

        stage('Publicar en Vercel') {
            
            steps {
                echo 'Deploy en vercel ...'
                
                sh '''
                npx vercel --token \$VERCEL_TOKEN --yes --prod 
                '''
            }
        }
    }
}