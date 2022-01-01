pipeline {
    agent any
    parameters{
         string(name:'Test',defaultValue:'Testenv',description:'This is a test env');
         booleanParam(name:'Unittestenv',defaultValue:true,description:'Need to run unittest only if its test env');
         choice(name:'chooseenvversion',choices:['1.1','1.2','1.3']);
        
    }
    
    stages {
        stage('Compile') {
            steps {
               script {
                   echo "compile the job"
               }
            }
}

            

        stage('UnitTest') {
            
                when{
                    expression{
                        params.Unittestenv==true
                    }
                }
            steps {
               script {
                   
                   echo "test the job"
               }
            
        } 
      
    }
            
            
        stage('Package') {
      
            input{
                message "Select a pckg version"
                ok "click version"
                parameters{
                choice(name:'selectionpackageversion',choices:['1.1','1.2','1.3']);
                }
            }

            
            steps {
               script {
                   echo "package the job"
                   echo "chosen env version is ${params.chooseenvversion}"
               }
            }
        }
    }
  }
