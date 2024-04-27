import hudson.model.*
import hudson.model.ParametersDefinitionProperty


// Definicja nazw parametrów
def paramNames = ['CWUB', 'KSO', 'RA', 'RL_DOD', 'RL_PRZELICZNIKI', 'RL_RPL_ZSMOPL',
'RL_TL', 'RP', 'RPL_PL', 'RPM', 'RPWDL_RPF', 'RPWDL_RPFG', 'RPWDL_RPM',
'RPWDL_RPZDL', 'RPWDL_RPZDLG', 'RPWDL_RPZLG', 'RPWDL_RPZLP', 'RPWDL_RPZPG',
'RPWDL_RPZPP', 'RSPO', 'SC', 'SF', 'SOLR_LR', 'SOLR_RL_PODZIELNOSC', 'SOLR_RL_V2', 'SOLR_RL_ZAMIENNIKI']


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

                    // User input
                    def userInput = input id: 'userInput', message: 'Prosze zaznaczyc rejestry do zaimportowania', parameters: [
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'CWUB' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'KSO' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RA' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RL_DOD' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RL_PRZELICZNIKI' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RL_RPL_ZSMOPL' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RL_TL' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RP' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPL_PL' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPM' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPWDL_RPF' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPWDL_RPFG' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPWDL_RPM' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPWDL_RPZDL' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPWDL_RPZDLG' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPWDL_RPZLG' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPWDL_RPZLP' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPWDL_RPZPG' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RPWDL_RPZPP' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'RSPO' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'SC' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'SF' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'SOLR_LR' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'SOLR_RL_PODZIELNOSC' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'SOLR_RL_V2' ],
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, name: 'SOLR_RL_ZAMIENNIKI' ],

                    [$class: 'hudson.model.StringParameterDefinition', defaultValue: params.text, description: 'To jest StringParameterDefinition', name: 'text'],
                    [$class: 'hudson.model.TextParameterDefinition', defaultValue: params.textarea, description: 'To jest TextParameterDefinition', name: 'textarea'],
                    [$class: 'hudson.model.ChoiceParameterDefinition', choices: params.choice, description: 'To jest ChoiceParameterDefinition', name: 'choice'],
                    [$class: 'hudson.model.PasswordParameterDefinition', defaultValue: params.password, description: 'To jest PasswordParameterDefinition', name: 'password']
                    ]
                    // Wybór zaznaczonych parametrów
                        def selected = []
                   paramNames.each {
                     if(params[it] == false) {
                       selected.push(it)
                     }
                   }

                    echo 'Zaznaczone checkboxy: ' + selected.join(',')

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

