def dataVolume = '/data'
def workspaceNode = '/opt/slave_jenkins_home/workspace'
def applicationRepo = 'git@gitlabpsuts.gft.com:SORN/tseo-rest.git'
def dockerImageName = 'nsd/tseo-rest'
def dockerContainerName = 'tseo-rest'
def contextPath = 'tseo-rest'
def host= '172.22.4.39'
def port = '8083'
def version = null

node('docker'){


    stage 'clean'
    //clean job workspace
    sh 'rm -rf *'
   
    echo "${GIT_BRANCH}"
    echo "${GIT_REPO_NAME}"
    echo "${GIT_URL}"
   
    stage 'build'
    //Run build inside maven container
    docker.image('maven:3.3.3-jdk-8').inside('-v '+ workspaceNode + ':' + workspaceNode + ' -v ' + dataVolume + ":" + dataVolume) 
	{
		//if ( isDevelopBranch( branchName ) )
// 	 		git branch: branchName, credentialsId: '439eba73-7b32-4fae-9605-fb269a7ac4a5', changelog: true, poll: false, url: applicationRepo
// 	 	else
 	 		checkout scm
    } 
    
}

