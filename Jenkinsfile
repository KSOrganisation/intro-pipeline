pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say Hello') {
      steps {
        echo "Hello ${params.Name}"
        sh 'java -version'
        echo "TEST_USER_USR=${TEST_USER_USR}"
        echo "TEST_USER_PSW=${TEST_USER_PSW}"
      }
    }
    stage('Deploy') {
      options {
         timeout(time: 30, unit: 'SECONDS')
      }
      input {
        message "Which Version?"
        ok "Deploy"
        parameters {
            choice(name: 'APP_VERSION', choices: "v1.1\nv1.2\nv1.3", description: 'What to deploy?')
        }
      }
      steps {
        echo 'Continuing with deployment'
      }
    }
  }
  environment {
    MY_NAME = 'Kaushalya Samarasekera'
    TEST_USER = credentials('test-user')
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
  post {
    aborted {
      echo 'Why didn\'t you push my button?'
    }
  }
}
