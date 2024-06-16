# DevOps

## 1. **What is DevOps**:
DevOps is a set of practices that combine software development (Dev) and IT operations (Ops) to shorten the development lifecycle and deliver high-quality software continuously.
the goal of DevOps is to automate and integrate the processes between software development and IT teams , allowing them to build,test, and release software faster and more reliably.
## 2. **Traditional Scenario**:
  * Developers: write the code and push it to a repo (GitHub)
    * Operations teams: Manage the servers and infrastructure
    * Testing teams: Test the software
    * Often , there are conflicts when the code works on the developer's machine but not in the server environement 
## 3. **Challenges in the Application Release Process**:
 
   ### 3.1 **Miscommunication and Lack of Collaboration**:
   *  Developers and operations teams often work in silos, leading to delays and errors.
    
   * Developers may not consider deployment environments, while operations teams may not understand the code thoroughly.
   ### 3.2 **Different Incentives**:
* Developers aim to release new features quickly.
* Operations focus on maintaining stability and preventing disruptions
    ### 3.3 **Security and Testing Roadblocks**:
 * Manual security evaluations and testing processes can significantly delay releases
    ### 3.4 **Manual Processes**:
* Manual deployments and infrastructure configurations are slow and error-prone.
### 3.5 **Lack of automation**

## 4. **DevOps Solution**:
DevOps engineers bridge the gap between development and operations by automating the software development lifecycle (SDLC), ensuring seamless and efficient collaboration between the two teams.

## 5. **Role od DevOps Engineer**:
 * Automate the release process
* Manage CI/CD pipelines
* Prepare and configure infrastructure
* Ensure continuous testing and monitoring
* Collaborate with development, operations, and security teams

## 6. **What are the different phases in DevOps?**:

![The Google Logo](/media\devopsimage.png)

 * <mark> Plan:</mark> Initially, there should be a plan for the type of application that needs to be
 developed. Getting a rough picture of the development process is always a good
 idea.
 * <mark> Code:</mark>The application is coded as per the end-user requirements.
 * <mark>Build:</mark> Build the application by integrating various codes formed in the previous
 steps.
 * <mark> Test: </mark> This is the most crucial step of the application development. Test the
 application and rebuild, if necessary.
 * <mark>Integrate:</mark> Multiple codes from different programmers are integrated into one.
 * <mark>Deploy:</mark> Code is deployed into a cloud environment for further usage. It is
 ensured that any new changes do not affect the functioning of a high traffic
 website.
 * <mark>Operate:</mark> Operations are performed on the code if required.
 * <mark>Monitor:</mark> Application performance is monitored. Changes are made to meet the
 end-user requirements

 ## 7. **Continuous Integration (CI)**:
 Continuous Integration means regularly merging all developers' code changes into a shared repository. This helps find and fix problems early. Tools automatically build and test the new code to ensure it integrates well with the existing codebase.
 ## 8.**Continuous Testing**:
 Testing is crucial to ensure the software works correctly. Continuous Testing involves running automated tests to check for bugs or issues. These tests happen frequently, usually every time new code is integrated. It helps catch problems early, making them easier to fix.
 ## 9. **Continuous Delivery/Deployment(CD)**:
 Continuous Deployment means automatically deploying the tested code to production, where users can access it. This stage ensures that new features or fixes reach users quickly. It involves:

  * Automating the release process
  * Ensuring the new code doesn't disrupt the existing system

  |Continuous Delivery |  Continuous Deployment |
| ----- | ------- |
| Ensures code can be safely deployed on toproduction | Every change that passes the automated tests is deployed toproduction automatically     |
| Delivers every change to a production-like environment through rigorous automated testing  | There is no explicit approval from a developer and requires a developed culture of monitoring |
## 10. **Continuous Improvement**:
DevOps is an ongoing process. Continuous Improvement involves regularly reviewing all stages of the lifecycle to find ways to enhance the process. It means learning from experiences and making adjustments to improve speed, quality, and reliability.
