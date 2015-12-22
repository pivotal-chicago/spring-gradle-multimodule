# Springboot Multimodule Starter
  
  This repo exists to serve as a starting point for a Spring Boot multimodule Gradle setup.
  The structure is set up so that the all Gradle tasks are run from the root directory of 
  the project, and it will build and test all submodules from there. The root `build.gradle`
  will be responsible for all build process related task creation as well as any common setup
  for submodules. This allows for submodule `build.gradle` to be super clean and only need to 
  know about the additional setup/dependencies that it needs.
  
  It also contains a simple `StandUpTest` which is designed to simulate Spring standing the 
  application up. This will point out any missing `Autowired` or `Service/Component/Controller`
  annotations.

# Gradle Scripts

  All Gradle scripts need to be run from the root of the project, where the Gradle Wrapper lives.
  After you have crafted your commit, you can run the `deliver` task.
  ```
  ./gradlew deliver
  ```
  This will rebase with GitHub, run test and build all sub-modules, and then push to GitHub.
  
  You can tag a release build by running the `tagRelease` task.
  ```
  ./gradlew tagRelease
  ```
  This will create a tag with the current version and the abbreviated SHA of the latest commit and push it to GitHub
  
  You can test, build, and deploy any sub-module individually by prepending the task name with the module name.
  ```
  ./gradlew :<module>:<task>
  ```
