# Jenkins

---

## 1. **What is Jenkins?**:

Jenkins is an open-source continuous integration tool widely used in software development. It automates repetitive steps in the development process such as compiling source code, running unit tests, and deploying applications.

## 2. **Why use Jenkins?**:

- **Automation of Repetitive Tasks:** Jenkins automates processes like compilation and testing, reducing human errors and speeding up development.

- **Continuous Integration:** Jenkins facilitates frequent integration of code changes into a project, ensuring better software quality.

- **Support for Numerous Plugins:** Jenkins has a vast library of plugins that extend its functionality, covering various tools and technologies.

## 3. **Basic Concepts**:

### <mark> Jobs </mark>

A Jenkins job represents an automated task, such as compiling a project or running tests. Each job has specific configurations defining how and when it should be executed.

### <mark> Build </mark>

A build refers to the execution of a Jenkins job. During a build, Jenkins takes the source code and applies defined steps from the job, such as compilation and testing.

### <mark> Pipeline </mark>

A Jenkins pipeline is a set of connected jobs arranged in a defined sequence, forming an automated workflow. Pipelines can be simple or complex, with conditions and parallel stages.

## 4. **Integration of Security with Jenkins in DevSecOps**:

### 4.1 **Automated Security Scanning**:

Jenkins can be configured to run automated security scanning tools such as SonarQube, OWASP Dependency-Check, and other static security analysis tools. These scans can be integrated into Jenkins pipelines to identify and report vulnerabilities early in the build stage.

### 4.2 **Automated Security Testing**:

By integrating automated security testing into Jenkins pipelines, DevOps teams can automatically check for vulnerabilities and potential weaknesses in code and configurations, ensuring better quality and reducing security risks.

### 4.3 **Automated Compliance Checks**:

Jenkins can also automate compliance checks against security standards and company policies. For instance, it can verify if security configurations are correctly applied in deployment environments.

### 4.4 **Secure Deployments**:

Using Jenkins to automate deployments, Continuous Deployment (CD) practices can include automated security validation mechanisms. This ensures that only secure and compliant versions are deployed into production.

### 4.5 **Secrets and Access Management**:

Jenkins supports integration with secrets and access management tools such as Vault or AWS Secrets Manager, securing the management of sensitive information used in pipelines (e.g., API keys or tokens).

### 4.6 **Security Monitoring**:

By integrating Jenkins with security monitoring tools, DevOps teams can continuously monitor development and production environments to detect and respond quickly to potential threats.

## 5. **Best Practices**:

- **Pipeline as Code**: Define your Jenkins pipelines as code (Pipeline as Code) for easy management, reproducibility, and reuse.

- **Early Security Integration:** Integrate security analyses early in the development process to identify and address vulnerabilities sooner.

- **Automation and Reporting:** Automate the generation of reports on security tests and scan results for increased visibility and proactive risk management.

![Alt text](/media/jenkinsimg.jpg)

## 6. **What is Jenkins Pipeline**:

A pipeline jenkins is a user-defined model of CD pipeline. A pipeline code defines your entire build process , which typically includes stages for building an application , testing and then delevring it .

![Alt text](/media/jenkinsPipeline.png)


## 7. **Why Pipeline**:

- **Code:** Pipelines are implemented in code and typically checked into source control, giving teams the ability to edit, review, and iterate upon their delivery pipeline.

- **Durable:** Pipelines can survive both planned and unplanned restarts of the Jenkins controller.

- **Pausable:** Pipelines can optionally stop and wait for human input or approval before continuing the Pipeline run.

- **Versatile:** Pipelines support complex real-world CD requirements, including the ability to fork/join, loop, and perform work in parallel.

- **Extensible:** The Pipeline plugin supports custom extensions to its DSL and multiple options for integration with other plugins.


## 8. **Scripted and Declarative  Pipeline fundamentals**:

 ### 8.1 **Scripted Pipeline**:
  
- bit harder due to more groovy 
- try-retry-loop
- groovy editor 
- more flexible for power users and complex requirments 

         node {
         stage('Build') {
        //
       }
       stage('Test') {
        //
       }
      stage('Deploy') {
        //
      }
      }

- Execute this Pipeline or any of its stages, on any available agent.
- Defines the "Build" stage. stage blocks are optional in Scripted 
Pipeline syntax. However, implementing stage blocks in a Scripted Pipeline provides clearer visualization of each stage's subset of tasks/steps in the Jenkins UI.
- Perform some steps related to the "Build" stage.
- Defines the "Test" stage.
- Perform some steps related to the "Test" stage.
- Defines the "Deploy" stage.
- Perform some steps related to the "Deploy" stage.

### 8.2 **Declarative Pipeline**:

- easy to use 
- more cincise and easy to read 
- validation before running 
- visual editor 
- perfect for regular user

      pipeline {
       agent any
       stages {
        stage('Build') {
            steps {
                //
            }
        }
        stage('Test') {
            steps {
                //
            }
        }
        stage('Deploy') {
            steps {
                //
            }
        }
        }
      }

- Execute this Pipeline or any of its stages, on any available agent.
- Defines the "Build" stage.
- Perform some steps related to the "Build" stage.
- Defines the "Test" stage.
- Perform some steps related to the "Test" stage.
- Defines the "Deploy" stage.
- Perform some steps related to the "Deploy" stage.

## 9. **Blue Ocean**:
Blue Ocean is a new user experience for Jenkins that provides a simplified and more intuitive way to create and