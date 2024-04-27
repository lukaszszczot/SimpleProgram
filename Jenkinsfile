import hudson.model.*
import hudson.model.ParametersDefinitionProperty

properties([
    new ParametersDefinitionProperty([
        new StringParameterDefinition("SELECTED_CHECKBOX_NAMES", "", "To jest StringParameterDefinition"),
        new ChoiceParameterDefinition("CHECKBOX_LIST", ["checkbox1", "checkbox2", "checkbox3", "checkbox4", "checkbox5"].toArray(new String[0]), "To jest ChoiceParameterDefinition"),
        new BooleanParameterDefinition("opcja1", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja2", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja3", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja4", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja5", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja6", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja7", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja6", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja8", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja9", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja10", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja11", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja12", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja13", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja14", true, 'To jest BooleanParameterDefinition'),
        new BooleanParameterDefinition("opcja15", true, 'To jest BooleanParameterDefinition'),
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
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja1'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja2'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja3'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja4'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja5'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja6'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja7'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja8'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja9'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja10'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja11'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja12'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja13'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja14'],
                    [$class: BooleanParameterDefinition, defaultValue: false, description: 'To jest BooleanParameterDefinition', name: 'opcja15'],
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