pipeline {
    agent any
    environment {
        // Need to set the PATH variable that my env uses, so that Jenkins environment can find the maven executable
        PATH = "/Users/soohian/.pyenv/bin:/Users/soohian/opt/anaconda3/envs/one/bin:/Users/soohian/opt/anaconda3/condabin:/Users/soohian/apache-maven-3.9.6/bin:/Library/Frameworks/Python.framework/Versions/3.12/bin:/opt/homebrew/bin:/opt/homebrew/bin:/opt/homebrew/sbin:/usr/local/bin:/System/Cryptexes/App/usr/bin:/usr/bin:/bin:/usr/sbin:/sbin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/local/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/appleinternal/bin:/usr/local/go/bin"
    }
    stages {
        stage("Clean Up") {
            steps {
                deleteDir() // jenkins plugin to recursively delete the current directory
            }
        }
        stage("Clone Repo") {
            steps {
                sh "git clone https://github.com/jenkins-docs/simple-java-maven-app.git"
            }
        }
        stage("Build") {
            steps {
                // dir is like cd-ing into the folder we git cloned above
                dir("simple-java-maven-app") {
                    sh '''
                    mvn clean install
                    '''
                }
            }
        }
        stage("Test") {
            steps {
                dir("simple-java-maven-app") {
                    sh "mvn test"
                }
            }
        }
    }
}