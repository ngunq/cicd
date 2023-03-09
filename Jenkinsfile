// Replace these URL to your target projects
def project1 = "https://github.com/ngunq/project334" // you can use the scp url here as well. Doesn't matter"
def ENV = "test"
def NAMESPACE = "scdp"
def SERVICE = "unomi-gw"
def CLUSTER = ".kube"
def HTTP_NAME = "http"
def GRPC_NAME = "grpc"
def HTTP_ENABLE=true
def GRPC_ENABLE=false

pipeline {
    agent none
    // parameters {
    //     gitParameter (branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH',
    //             useRepository: "${project1}", listSize: "10", quickFilterEnabled: true,
    //             sortMode: 'DESCENDING_SMART')

    // }
    stages {
        stage ('BUILD'){
            agent any
            stages{
                stage("Git Clone") {
                    steps {
                        echo "================================ GIT CHECKOUT =============================================="
                        script {
                            currentBuild.displayName = "${BUILD_NUMBER}-${params.BRANCH}"
                        }
                        dir(".") {
                            git url: "${project1}", credentialsId:'github_local', branch: "master"
                            sh 'echo $PWD'
                            sh 'ls -lh'
                        }
                    }
                }
            }
        }
    }
}

