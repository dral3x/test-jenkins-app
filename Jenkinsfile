properties([
	[
		$class: 'GithubProjectProperty', 
		displayName: 'Test app', 
		projectUrlStr: 'https://github.com/dral3x/test-jenkins-app/'
	], 
	pipelineTriggers([[$class: 'GitHubPushTrigger']])
])

stage("Checkout") {
	def credentialsId = 'dec9dfc6-75b8-45bb-8463-a1b6031f4a03'
	def defaultBranch = 'master'

	dir('app') {
	    checkout scm
	} 

	dir('lib') {
		def repo = 'git@github.com:dral3x/test-jenkins-lib.git'
	    try {
	        git credentialsId: "${credentialsId}", url: repo, branch: "${env.BRANCH_NAME}"
	   	}
 		catch(exc) {
	        git credentialsId: "${credentialsId}", url: repo, branch: "${defaultBranch}"
	    }
	}
}

stage("Build") {
}