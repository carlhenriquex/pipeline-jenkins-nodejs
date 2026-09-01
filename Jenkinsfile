pipeline {
    agent any

    tools {
        // Certifique-se de que a versão do Node.js configurada no seu Jenkins possui este nome
        nodejs 'NodeJS' 
    }

    stages {
        stage('Instalar Dependências') {
            steps {
                echo 'Instalando dependências do projeto...'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Executando o Build do projeto...'
                // Se o seu package.json não tiver o script de build, o comando 'npm run build --if-present' evita erros
                sh 'npm run build --if-present'
            }
        }

        stage('Testes') {
            steps {
                echo 'Executando os testes unitários...'
                sh 'npm test'
            }
        }
    }

    post {
        success {
            echo '==================================================='
            echo ' SUCCESS: O pipeline foi executado com sucesso!'
            echo '==================================================='
        }
        failure {
            echo '==================================================='
            echo ' FAILURE: Houve uma falha na execução do pipeline.'
            echo '==================================================='
        }
        always {
            echo 'Limpando o ambiente/Concluindo execução.'
        }
    }
}