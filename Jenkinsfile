pipeline {
    agent any
    stages{
        stage('Test Category Printing') {
            steps {
                sh """#!/usr/bin/env bash
                echo "Hellooooo Boss"
                """
            }
        }
        stage('Print List of Changed Files') {
            steps {
                script{
                    def changeLogSets = currentBuild.changeSets
                    for (int i = 0; i < changeLogSets.size(); i++) {
                        def entries = changeLogSets[i].items
                        for (int j = 0; j < entries.length; j++) {
                            def entry = entries[j]
                            echo "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg}"
                            def files = new ArrayList(entry.affectedFiles)
                            for (int k = 0; k < files.size(); k++) {
                                def file = files[k]
                                echo "${file.path}"
                            }
                        }
                        
                    }    
                }
            }
            
        }    
    }
}
