import hudson.model.*
import hudson.model.ParametersDefinitionProperty

properties([
    new ParametersDefinitionProperty([
        new StringParameterDefinition("SELECTED_CHECKBOX_NAMES", "", "To jest StringParameterDefinition"),
        new ChoiceParameterDefinition("CHECKBOX_LIST", ["checkbox1", "checkbox2", "checkbox3", "checkbox4", "checkbox5"].toArray(new String[0]), "To jest ChoiceParameterDefinition"),
        new BooleanParameterDefinition("continue", true, 'To jest BooleanParameterDefinition'),
        new StringParameterDefinition("text", "", 'To jest StringParameterDefinition'),
        new TextParameterDefinition("textarea", "", "To jest TextParameterDefinition"),
        new ChoiceParameterDefinition("choice", ['opcja1', 'opcja2', 'opcja3'].toArray(new String[0]), "To jest ChoiceParameterDefinition"),
        new PasswordParameterDefinition('password', 'SECRET', 'To jest PasswordParameterDefinition')
    ])
])

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
                    // Check checkboxes
                    String selectedCheckboxNames = params.SELECTED_CHECKBOX_NAMES
                    String selectedCheckbox = params.CHECKBOX_LIST
                    if (!selectedCheckboxNames.isEmpty()) {
                        selectedCheckboxNames += ","
                    }
                    selectedCheckboxNames += selectedCheckbox
                    echo "Selected checkboxes: " + selectedCheckboxNames

                    // User input
                    def userInput = input id: 'userInput', message: 'Zatwierdź wykonanie następnego kroku', parameters: [
                        [$class: 'hudson.model.BooleanParameterDefinition', defaultValue: params.continue, description: 'To jest BooleanParameterDefinition', name: 'continue'],
                        [$class: 'hudson.model.StringParameterDefinition', defaultValue: params.text, description: 'To jest StringParameterDefinition', name: 'text'],
                        [$class: 'hudson.model.TextParameterDefinition', defaultValue: params.textarea, description: 'To jest TextParameterDefinition', name: 'textarea'],
                        [$class: 'hudson.model.ChoiceParameterDefinition', choices: params.choice, description: 'To jest ChoiceParameterDefinition', name: 'choice'],
                        [$class: 'hudson.model.PasswordParameterDefinition', defaultValue: params.password, description: 'To jest PasswordParameterDefinition', name: 'password']
                    ]

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