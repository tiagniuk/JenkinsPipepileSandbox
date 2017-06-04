#!/usr/bin/env groovy

node {
    checkout scm

    parallel (
        "Test 1": {
            try {
                stage('Test 1') {
                    githubNotify(
                        description: 'Test 1 - Build has been scheduled.',
                        status:      'PENDING'
                    )
                    echo "@@ Starting Test 1"
                    echo "@@ Sleeping for 30 seconds"
                    sh 'sleep 30'
                    echo "@@ Finished Test 1"
                }
            } catch (e) {
                githubNotify(
                    description: 'Test 1 - Not OK',
                    status:      'FAILURE'
                )
            } finally {
                githubNotify(
                    description: 'Test 1 - OK',
                    status:      'SUCCESS'
                )
            }
        },
        "Test 2": {
            try {
                stage('Test 2') {
                    githubNotify(
                        description: 'Test 2 - Build has been scheduled.',
                        status:      'PENDING'
                    )
                    echo "@@ Starting Test 2"
                    echo "@@ Sleeping for 60 seconds"
                    sh 'sleep 60'
                    echo "@@ Finished Test 2"
                }
            } catch (e) {
                githubNotify(
                    description: 'Test 2 - Not OK',
                    status:      'FAILURE'
                )
            } finally {
                githubNotify(
                    description: 'Test 2 - OK',
                    status:      'SUCCESS'
                )
            }
        },
        "Test 3": {
            try {
                stage('Test 3') {
                    githubNotify(
                        description: 'Test 3 - Build has been scheduled.',
                        status:      'PENDING'
                    )
                    echo "@@ Starting Test 3"
                    echo "@@ Sleeping for 90 seconds"
                    sh 'sleep 90'
                    echo "@@ Finished Test 3"
                }
            } catch (e) {
                githubNotify(
                    description: 'Test 3 - Not OK',
                    status:      'FAILURE'
                )
            } finally {
                githubNotify(
                    description: 'Test 3 - OK',
                    status:      'SUCCESS'
                )
            }
        },
    )
}
