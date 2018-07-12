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
  }
  environment {
    MY_NAME = 'Kaushalya Samarasekera'
    TEST_USER = credentials('test-user')
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
}