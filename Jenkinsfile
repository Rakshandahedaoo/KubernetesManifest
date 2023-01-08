node {
    def app

    stage('Clones repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email rakshandahedaoo31@gmail.com"
                        sh "git config user.name Rakshanda hedaoo"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+rakshandahedaoo/gitops.*+rakshandahedaoo/gitops:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/KubernetesManifest.git HEAD:main"
      }
    }
  }
}
}
