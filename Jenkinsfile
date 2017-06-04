#!/usr/bin/env groovy

node {
    checkout scm

    parallel (
        "Test 1": {
            try {
                stage('Test 1') {
                    commitStatusPending 'Test 1'
                    echo "@@ Starting Test 1"
                    echo "@@ Sleeping for 30 seconds"
                    sh 'sleep 30'
                    echo "@@ Finished Test 1"
                    commitStatusSuccess 'Test 1'
                }
            } catch (e) {
                commitStatusFailure 'Test 1'
            }
        },
        "Test 2": {
            try {
                stage('Test 2') {
                    commitStatusPending 'Test 2'
                    echo "@@ Starting Test 2"
                    echo "@@ Sleeping for 60 seconds"
                    sh 'sleep 60 && exit 1'
                    echo "@@ Finished Test 2"
                    commitStatusSuccess 'Test 2'
                }
            } catch (e) {
                commitStatusFailure 'Test 2'
            }
        },
        "Test 3": {
            try {
                stage('Test 3') {
                    commitStatusPending 'Test 3'
                    echo "@@ Starting Test 3"
                    echo "@@ Sleeping for 90 seconds"
                    sh 'sleep 90'
                    echo "@@ Finished Test 3"
                    commitStatusSuccess 'Test 3'
                }
            } catch (e) {
                commitStatusFailure 'Test 3'
            }
        },
    )
}

def commitStatusPending (String context) {
    commitStatus(context, 'PENDING')
}

def commitStatusSuccess (String context) {
    commitStatus(context, 'SUCCESS')
}

def commitStatusFailure (String context) {
    def status = 'FAILURE'
    commitStatus(context, status)
    currentBuild.result = status
}

def commitStatus (String context, String status) {
    String description
    switch (status) {
        case 'PENDING': description = 'Build has been scheduled.'; break
        case 'SUCCESS': description = 'OK'; break
        case 'FAILURE': description = 'Not OK'; break
    }
    githubNotify(
        context:     context,
        status:      status,
        description: description,
    )
}
