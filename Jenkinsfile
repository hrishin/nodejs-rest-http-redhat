#!/usr/bin/groovy
@Library('github.com/hrishin/osio-pipeline@fix-spawn')_

osio {
    config runtime: 'oc'

    ci {
        def app = processTemplate()
        build app: app
    }

    cd {
      def resources = processTemplate(params: [
        release_version: "1.0.${env.BUILD_NUMBER}"
      ])

      echo "-------------- build default ----------------------------"
      build resources: resources
  
      echo "-------------- deploy -----------------------------------"
      deploy resources: resources, env: 'stage'

      // deploy app: app, env: 'run', approval: 'manual'
      echo "---------------------------------------------------------"
    }
}

