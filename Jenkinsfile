pipeline {
    agent any
    environment {
        DISCORD_WEBHOOK = credentials('discord_webhook')
    }

    stages {
        stage('Send Notifications') {
            steps {
                echo 'hello world!'
            }
            post {
                success {
                    sendDiscordNotification("finalizado correctamente!")
                }
                failure {
                    sendDiscordNotification("finalizado con errores!")
                }
            }
        }
    }
}

def sendDiscordNotification(descriptionSuffix) {
    discordSend description: "${STAGE_NAME} ${descriptionSuffix}", 
                result: currentBuild.currentResult, 
                title: JOB_NAME, 
                webhookURL: env.DISCORD_WEBHOOK
}
