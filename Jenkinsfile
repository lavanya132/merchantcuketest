node {
   // Mark the code checkout 'stage'....
   stage 'Checkout'
   
   git url: 'https://github.com/lavanya132/merchantcuketest.git'
   
   def mvnHome = tool 'M3'
   
   stage 'Compile'
   sh "${mvnHome}/bin/mvn clean compile"
   
   stage 'Test'
   sh "${mvnHome}/bin/mvn clean test"
   
   stage 'Collect Results'
   step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
   step([$class: 'CucumberReportPublisher', jsonReportDirectory: 'target/cucumber', fileIncludePattern: 'cucumber.json'])
   step([$class: 'SauceOnDemandTestPublisher'])
}
