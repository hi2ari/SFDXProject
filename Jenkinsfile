#!groovy
import groovy.json.JsonSlurperClassic
node {

    def BUILD_NUMBER=env.BUILD_NUMBER
    def RUN_ARTIFACT_DIR="tests/${BUILD_NUMBER}"
    def SFDC_USERNAME

    def HUB_ORG=env.SF_LOGINID
    def SFDC_HOST = env.SF_URL
    def JWT_KEY_CRED_ID = env.SERVER_KEY_CREDENTALS_ID
    def CONNECTED_APP_CONSUMER_KEY=env.SF_CONSUMER_KEY

    println 'KEY IS' 
    println JWT_KEY_CRED_ID
    println HUB_ORG
    println SFDC_HOST
    println CONNECTED_APP_CONSUMER_KEY
    def toolbelt = tool 'toolbelt'

}
