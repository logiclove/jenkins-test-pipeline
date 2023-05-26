pipeline {
    agent { label 'rhel87' }
    stages {
        stage('build') {
            steps {
                sh 'java --version'
            }
            script {
import org.jenkinsci.plugins.workflow.job.WorkflowJob
import hudson.model.FreeStyleProject
import hudson.model.Build.BuildExecution
import org.jenkinsci.plugins.workflow.job.WorkflowRun

def items = Jenkins.instance.getAllItems(Job.class)
items.each{
  println '"' + it.name + '"' + " class:" + it.class
  it.builds.each{ 
    if (it.building) {
      println '    "' + it + '"' + " class:" + it.class 
      it.doKill()
    }
  }
}
items.size()
            }
        }
    }
}
