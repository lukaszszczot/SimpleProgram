import hudson.model.*
import hudson.model.ParametersDefinitionProperty


// Definicja nazw parametrów
def paramNames = ['CWUB', 'KSO', 'RA', 'RL_DOD', 'RL_PRZELICZNIKI', 'RL_RPL_ZSMOPL',
'RL_TL', 'RP', 'RPL_PL', 'RPM', 'RPWDL_RPF', 'RPWDL_RPFG', 'RPWDL_RPM',
'RPWDL_RPZDL', 'RPWDL_RPZDLG', 'RPWDL_RPZLG', 'RPWDL_RPZLP', 'RPWDL_RPZPG',
'RPWDL_RPZPP', 'RSPO', 'SC', 'SF', 'SOLR_LR', 'SOLR_RL_PODZIELNOSC', 'SOLR_RL_V2', 'SOLR_RL_ZAMIENNIKI']
properties([
        new ParametersDefinitionProperty([
       new BooleanParameterDefinition("CWUB", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("KSO", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RA", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RL_DOD", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RL_PRZELICZNIKI", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RL_RPL_ZSMOPL", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RL_TL", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RP", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPL_PL", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPM", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPWDL_RPF", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPWDL_RPFG", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPWDL_RPM", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPWDL_RPZDL", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPWDL_RPZDLG", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPWDL_RPZLG", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPWDL_RPZLP", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPWDL_RPZPG", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RPWDL_RPZPP", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("RSPO", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("SC", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("SF", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("SOLR_LR", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("SOLR_RL_PODZIELNOSC", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("SOLR_RL_V2", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("SOLR_RL_ZAMIENNIKI", true, "To jest BooleanParameterDefinition"),
       new BooleanParameterDefinition("OldVersionImport", true, "To jest BooleanParameterDefinition"),
       new StringParameterDefinition("text", "text", 'Prosze wprowadzic opis - niewymagane'),
       new TextParameterDefinition("textarea", "textarea", "Prosze wprowadzic opis - niewymagane"),
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
                    [ $class: 'hudson.model.BooleanParameterDefinition', defaultValue: false, description: 'Import starszej wersji rekordu, zostanie zastosowany do każdego zaznaczonego powyżej rejestru', name: 'OldVersionImport' ],                    ]
                    [ $class: 'hudson.model.StringParameterDefinition', defaultValue: params.text, description: 'Prosze wprowadzic opis - niewymagane', name: 'text' ],
                     [ $class: 'hudson.model.TextParameterDefinition', defaultValue: params.textarea, description: 'Prosze wprowadzic opis - niewymagane', name: 'textarea' ]]

                    // Wybór zaznaczonych parametrów
                        def selected = []
                            paramNames.each {
                                 if(userInput[it] == true) {
                                    selected.push(it)
                                                             }
                                             }

                    echo 'Zaznaczone checkboxy: ' + selected.join(',')
                    echo "Import starszej wersji rekordu: ${userInput.OldVersionImport}"
                    echo "Text: ${userInput.text}"
                    echo "Textstrs: ${userInput.textarea}"

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

