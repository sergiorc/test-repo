def dataVolume = '/data'
def workspaceNode = '/opt/slave_jenkins_home/workspace'
def applicationRepo = 'git@gitlabpsuts.gft.com:SORN/tseo-rest.git'
def dockerImageName = 'nsd/tseo-rest'
def dockerContainerName = 'tseo-rest'
def contextPath = 'tseo-rest'
def host= '172.22.4.39'
def port = '8083'
def version = null
def branchName = currentBranch()
def developmentHost = tseo-runtime.gft.com
def image

node('docker'){

	echo 'Current Branch :' + branchName

    stage 'clean'
    //clean job workspace
    sh 'rm -rf *'
   
    stage 'build'
    //Run build inside maven container
    docker.image('maven:3.3.3-jdk-8').inside('-v '+ workspaceNode + ':' + workspaceNode + ' -v ' + dataVolume + ":" + dataVolume) 
	{
 		checkout scm
    } 
    
}
    

def isDevelopBranch ( jobName ) {
    jobName.startsWith("develop")
}

def currentBranch() {
  def jobName = "${env.JOB_NAME}"
  if ( isDevelopBranch(jobName) )
    return "develop"
  else
  {
  	def pos = jobName.indexOf ( "/" )
  	//String.substring is blocked by script-security-plugin. It's needed to active in Jenkins Management
  	//https://issues.jenkins-ci.org/browse/JENKINS-30252
  	return jobName.substring ( pos + 1);
  }
}

