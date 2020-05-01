#!groovy
import groovy.json.JsonSlurperClassic
node {

    def BUILD_NUMBER=env.BUILD_NUMBER
    def RUN_ARTIFACT_DIR="tests/${BUILD_NUMBER}"
	def SFDC_USERNAME="${Workspace}/../"
def FILEPATH="C:\Program Files (x86)\Jenkins\workspace\server.key"
    def HUB_ORG=env.SF_LOGINID
    def SFDC_HOST = env.SF_URL
    def JWT_KEY_CRED_ID = env.SERVER_KEY_CREDENTALS_ID
    def CONNECTED_APP_CONSUMER_KEY=env.SF_CONSUMER_KEY

    println 'KEY IS' 
    println JWT_KEY_CRED_ID
    println HUB_ORG
    println SFDC_HOST
    println CONNECTED_APP_CONSUMER_KEY
println SFDC_USERNAME
    //println ${JWT_KEY_FILE}
    def toolbelt = tool 'toolbelt'
    
    stage('checkout source') {
        // when running in multi-branch job, one must issue this command
        checkout scm
    }
    
    //withCredentials([file(credentialsId: JWT_KEY_CRED_ID, variable: 'jwt_key_file')]) {
        stage('Authorize Dev Hub') {
		//bat("xcopy C:\\Program Files (x86)\\Jenkins\\workspace\\server.key ${WORKSPACE} ")
		//rmsg = bat returnStdout: true, script: "\"${toolbelt}\" force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile \"${JWT_KEY_FILE}\" --setdefaultdevhubusername --instanceurl ${SFDC_HOST}"
		rmsg = bat returnStdout: true, script: "\"${toolbelt}\" force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile ${FILEPATH} --setdefaultdevhubusername --instanceurl ${SFDC_HOST}"
            	//if (rc != 0) { error 'hub org authorization failed' }
            	printf rmsg
		println('Hello from a Job DSL script1!')
		def beginIndex = rmsg.indexOf('{')
		def endIndex = rmsg.indexOf('}')
		println('beginIndex' + beginIndex)
		println('endIndex' + endIndex)
		def jsobSubstring = rmsg.substring(beginIndex)
		println('jsobSubstring' + jsobSubstring)
		def jsonSlurper = new JsonSlurperClassic()
		def robj = jsonSlurper.parseText(jsobSubstring)
		if (robj.status != 0) { error 'authorization failed: ' + robj.message }
		robj = null
        }
    //}
}
