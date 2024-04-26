pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                git 'https://github.com/lukaszszczot/SimpleProgram.git'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('User Input') {
            steps {
                script {
                    def userInput = input(id: 'userInput', message: 'Zatwierdź wykonanie następnego kroku', parameters: [
                        booleanParam(defaultValue: true, description: 'Czy kontynuować?', name: 'continue'),
                        string(defaultValue: '', description: 'Wpisz tekst', name: 'text'),
                        text(defaultValue: '', description: 'Wprowadź dłuższy blok tekstu', name: 'textarea'),
                        choice(choices: 'opcja1\nopcja2\nopcja3', description: 'Wybierz jedną z opcji', name: 'choice'),
                        password(defaultValue: 'SECRET', description: 'Wprowadź hasło', name: 'password')
                    ])

                    echo "Kontynuuj: ${userInput.continue}"
                    echo "Tekst: ${userInput.text}"
                    echo "Textarea: ${userInput.textarea}"
                    echo "Choice: ${userInput.choice}"
                    echo "Hasło: ${userInput.password}"
                }
            }
        }

        stage('Run program') {
            steps {
                bat 'java -cp target/classes org.example.Main'
            }
        }

    }
}