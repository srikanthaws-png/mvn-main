@Library('mylibrary')_

pipeline
{
    agent any
    stages
    {
        stage('Download_Master')
        {
            steps
            {
                script
                {
                    cicd.gitDownload("maven")
                }
            }
        }
        stage('Build_Master')
        {
            steps
            {
                script
                {
                    cicd.buildArtifact()
                }
            }
        }
        stage('Deploy_Master')
        {
            steps
            {
                script
                {
                    cicd.deployTomcat("DeclarativePipelinewithSharedLibraries","172.31.16.81","testapp")
                }
            }
        }
        stage('Test_Master')
        {
            steps
            {
                script
                {
                    cicd.gitDownload("FunctionalTesting")
                    cicd.runSelenium("DeclarativePipelinewithSharedLibraries")
                }
            }
        }
        stage('Delivery_Master')
        {
            steps
            {
                script
                {
                    cicd.deployTomcat("DeclarativePipelinewithSharedLibraries","172.31.31.60","prodapp")
                }
            }
        }
    }
}
