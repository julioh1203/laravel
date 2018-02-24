node('php'){
    stage('Clean'){
        deleteDir()
        sh 'ls -la'
    }
    
    stage('Fetch') {
        checkout scm
    }
    
    stage('Build App'){
        sh 'composer install --no-scripts --prefer-dist --no-dev --ignore-platform-reqs'
    }
    
    stage('Docker Build') {
        sh 'docker build -t julioh1203/laravel:$BUILD_NUMBER .'
    }
    
    stage('Docker Ship') {
        sh 'docker push julioh1203/laravel:$BRANCH_NAME-$BUILD_NUMBER'
        sh 'docker rmi -f julioh1203/laravel:$BRANCH_NAME-$BUILD_NUMBER'
    }
}
