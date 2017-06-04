#!/usr/bin/env groovy

node {
    checkout scm

    parallel (
        "Test 1": {
            try {
                stage('Test 1') {
                    githubNotify(
                        context:     'Test 1',
                        description: 'Build has been scheduled.',
                        status:      'PENDING'
                    )
                    echo "@@ Starting Test 1"
                    echo "@@ Sleeping for 30 seconds"
                    sh 'sleep 30'
                    echo "@@ Finished Test 1"
                    githubNotify(
                        context:     'Test 1',
                        description: 'OK',
                        status:      'SUCCESS'
                    )
                }
            } catch (e) {
                githubNotify(
                    context:     'Test 1',
                    description: 'Not OK',
                    status:      'FAILURE'
                )
            }
        },
        "Test 2": {
            try {
                stage('Test 2') {
                    githubNotify(
                        context:     'Test 2',
                        description: 'Build has been scheduled.',
                        status:      'PENDING'
                    )
                    echo "@@ Starting Test 2"
                    echo "@@ Sleeping for 60 seconds"
                    sh 'sleep 60 && exit 1'
                    echo "@@ Finished Test 2"
                    githubNotify(
                        context:     'Test 2',
                        description: 'OK',
                        status:      'SUCCESS'
                    )
                }
            } catch (e) {
                githubNotify(
                    context:     'Test 2',
                    description: 'Not OK',
                    status:      'FAILURE'
                )
            }
        },
        "Test 3": {
            try {
                stage('Test 3') {
                    githubNotify(
                        context:     'Test 3',
                        description: 'Build has been scheduled.',
                        status:      'PENDING'
                    )
                    echo "@@ Starting Test 3"
                    echo "@@ Sleeping for 90 seconds"
                    sh 'sleep 90'
                    echo "@@ Finished Test 3"
                    githubNotify(
                        context:     'Test 3',
                        description: 'OK',
                        status:      'SUCCESS'
                    )
                }
            } catch (e) {
                githubNotify(
                    context:     'Test 3',
                    description: 'Not OK',
                    status:      'FAILURE'
                )
            }
        },
    )
}
