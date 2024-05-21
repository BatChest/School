# Define CI and CD
## Continuous Integration
- Automates integrating changes 
	- Developers push changes to a shared repository
	- Infer automatically if changes are compatible 
	- If changes are compatible merge changes and start a build 
## Continuous Deployment
- Automates deploying changes
	- Infer automatically if new build is production-ready
	- Automatically deploy production-ready builds

# CI/CD Capabilities
- **Streamlined Development Process**: 
	- CI/CD automates the integration, release, and deployment processes, accelerating the software development lifecycle.
- **Reduced Complexity and Increased Efficiency**: 
	- CI/CD decreases complexity and increases efficiency as applications grow larger.
- **Faster Releases and Reduced Downtime**: 
	- CI/CD minimizes downtime and accelerates code releases by automating manual human intervention.
- **Improved Code Quality**: 
	- CI/CD helps avoid bugs and code failures while maintaining a continuous cycle of software development and updates.
- **Enhanced Collaboration**: 
	- CI/CD promotes better coordination between development and operations teams.
- **Immediate Feedback**: 
	- CI/CD allows for more frequent and effective incorporation of user feedback due to the ability to quickly integrate updates and changes to code.
- **Automation Tools**: 
	- CI/CD tools like GitLab CI automate the integration, release, and deployment processes, accelerating the app’s lifecycle and preventing costly bugs.
# Developer Practices that Enable CI/CD:**
- **Keeping Pipelines Fast**: 
	- CI/CD pipelines should be fast and dependable. This can be achieved by scaling out CI/CD infrastructure and optimizing tests.
- **Isolating and Securing the CI/CD Environment**: 
	- The CI/CD system is critical infrastructure that needs to be secured since it has complete access to the codebase and credentials to deploy in various environments.
- **Adopting a Security-First Approach**: 
	- Prioritizing software security is crucial to avoid the risk of data theft.
- **Building Once and Using Everywhere**: 
	- The same build should be used across all environments to ensure consistency.
- **Failing Fast and Fixing Early**: 
	- The sooner a failure is detected, the sooner it can be fixed. This reduces the overall time to recovery.
- **Planning Test Automation**: 
	- Automated testing is a critical part of DevOps best practices. It helps discover bugs and errors sooner, leading to higher-quality code.
- **Checking Adaptability for Microservices Architecture**: 
	- Microservices architecture can help decrease complexity, increase efficiency, and streamline workflows.
# Code Analysis that Enables CI and CD:**
- **Static Code Analysis**: 
	- Static code analysis is a method of debugging by examining source code before a program is run. It’s done by analyzing a set of code against a set (or multiple sets) of coding rules. This type of analysis addresses weaknesses in source code that might lead to vulnerabilities.
- **Dynamic Code Analysis**: 
	- Dynamic analysis is the testing and evaluation of a program by executing data in real-time. The objective is to find errors in a program while it is running, rather than by repeatedly examining the code offline.
- **Security Code Analysis**: 
	- Security code analysis is the process of detecting vulnerabilities in a piece of software. This can be done through several methods such as Static Application Security Testing (SAST), Dynamic Application Security Testing (DAST), or Interactive Application Security Testing (IAST).
- **Automated Code Review**: 
	- Automated code review software checks source code for compliance with a predefined set of rules or best practices set out by the organization.

# Examples of CI/CD tools
- Jenkins 
	- platform for creating a Continuous Integration/Continuous Delivery (CI/CD) environment
- Travis CI
	- supports rapid software development and publishing
	- allows automation across the user’s pipeline, from code building, testing to deployment
- Circle CI
	- helps modern engineering teams automate builds, boost developer productivity, and release new, high-quality software quickly. It’s a cloud-based CI/CD tool that automates installation and delivery procedures

# What's the relationship between CI/CD and devops?
- CI/CD is a key part of DevOps
- On the spectrum from tool to practice to way of working
	- CI/CD is a practice relying on a specific tools
	- DevOps is a way of working relying on CI/CD and other practices 

# How do CI/CD and version control (git/GitHub) interact?
- CI/CD tools run on top of Git
- git/GitHub actions trigger CI/CD tools
	- commit 
	- PR
- builds are run in isolation in a cloud build environment (VM/container)
- build is tested
- developer receives automated feedback on build status 
- CI tools can:
	- automatically merge changes to main branch 

# Benefits of CI/CD
1. **Streamlined Development Process**: CI/CD streamlines and accelerates the software development lifecycle by automating the integration, release, and deployment processes.
    
2. **Reduced Complexity and Increased Efficiency**: As applications grow larger, CI/CD can help decrease complexity, increase efficiency, and streamline workflows.
    
3. **Faster Releases and Reduced Downtime**: Because CI/CD automates the manual human intervention traditionally needed to get new code from a commit into production, downtime is minimized and code releases happen faster.
    
4. **Improved Code Quality**: CI/CD helps organizations avoid bugs and code failures while maintaining a continuous cycle of software development and updates.
    
5. **Enhanced Collaboration**: CI/CD promotes better coordination between development and operations teams.
    
6. **Immediate Feedback**: With the ability to more quickly integrate updates and changes to code, user feedback can be incorporated more frequently and effectively.
    
7. **Automation Tools**: CI/CD tools like GitLab CI help automate the integration, release, and deployment processes to accelerate the app’s lifecycle while helping prevent costly bugs.

# Loose coupling vs. tight coupling in software architecture
- **Tight Coupling**:
    - High interdependence between components.
    - Changes in one component may affect others.
    - Can make the system difficult to scale, maintain, and modify.
- **Loose Coupling**:
    - Components are independent of each other.
    - Changes in one component don’t require changes in others.
    - Promotes flexibility and maintainability but can increase complexity.

# Results from developer surveys (trends, not specific numbers)
1. **Growing Interest in DevOps**: 
	1. The fact that 84% of developers participate in DevOps-related activities indicates a strong trend towards DevOps practices. 
	2. This suggests that developers are recognizing the benefits of DevOps, such as increased deployment frequency and reduced lead time for changes.
    
2. **Specialization in DevOps**: 
	1. While a large number of developers are involved in DevOps activities, only 7% identify as DevOps specialists. 
	2. This could indicate that while DevOps practices are being widely adopted, there is still a need for specialized roles to manage and optimize these practices.
    
3. **Integration of DevOps into Developer Roles**: 
	1. The high percentage of developers participating in DevOps-related activities could also suggest that DevOps practices are becoming an integral part of the developer role, rather than being confined to specialized roles.

# Purpose and benefits of build systems
- A tool or set of tools that automates the process of building compiling, and packaging software from its source code
- Manages dependencies
- controls the build process
- ensures that the final software product is ready for use
- Programming language and package ecosystem
- Project complexity and scalability requirements 
- Community support and available plugins/extensions
- Learning curve and ease of use
- Integration with other tools (e.g. IDE's, CI/CD pipelines)

# Know the key inputs to a build system
![[Pasted image 20240514160237.png]]

# Understand how a build system uses a Directed Acyclic Graph (DAG) to model dependencies between source files and build targets
![[Pasted image 20240514173229.png]]

The core of a build system is a **Directed Acyclic Graph (DAG)** that represents the dependencies between the source files and build targets 
- With a DAG we have different vertices like a graph
![[Pasted image 20240514163459.png]]
- Each vertices represent a dependency 
![[Pasted image 20240514163610.png]]
- Imagine we're building a GPS app and we have the intermediate library as one vertex
- Then we have the UI on the other vertex 
- The Intermediate GEO library might depend on some math calculation library that's an external dependency 
- The UI depend on some UI from work from that other dependency 
- The app depend on those two dependency links 
- Its a directed graph because dependencies are just one way and the authors of the library don't we are writing an app but we care about the functionality that's provided by their framework (directional)
- There is no cycle making acyclic 
- The dotted line represents the boundary between external software(stuff we didn't write) and internal software(source code for our app)

# Name common build systems
- **GNU Make**: 
	- A widely used build automation tool that automatically builds executable programs and libraries from source code.
- **CMake**: 
	- A cross-platform free and open-source software tool for managing the build process of software using a compiler-independent method.
- **QMake**: 
	- A build automation tool from Qt toolkit that helps simplify the build process for development project across different platforms.

# Name benefits and challenges of using build systems
## Benefits
- Programming language and package ecosystem
- Project complexity and scalability requirements 
- Community support and available plugins/extensions
- Learning curve and ease of use
- Integration with other tools (e.g. IDE's, CI/CD pipelines)
## Challenges
- Complexity 
- Learning Curve 
- Performance
- Dependencies
- Debugging

# Know build system best practices
- **Modular build configuration**
	- Separate things out
	- Work on things separately 
- Use **version control** for build configuration files
	- Want to go back if something breaks
	- Revert back to older version
- Regularly **update and maintain dependencies**
- Use **semantic versioning** for dependencies 
- Integrate build tools with continuous integration and delivery **(CI/CD)** pipelines 
- **Monitor and improve performance**
- Use **build optimizations** (e.g., incremental builds, parallel execution)
- Document build processes and provide clear instructions 

# Name and describe types of builds and their use cases
![[Pasted image 20240514173147.png]]

# Know the stages of a typical build lifecycle
1. **Pre-Build**: This is the initial stage where the environment setup takes place. It includes setting up the necessary tools and dependencies required for the build process.
    
2. **Compilation**: In this stage, the source code is compiled into binary code. The compiler checks the syntax of the code and ensures that it adheres to the rules of the programming language.
    
3. **Testing**: After the code is compiled, it is tested to ensure that it behaves as expected. This can include unit tests, integration tests, and system tests.
    
4. **Packaging**: Once the code has passed all tests, it is packaged into a distributable format such as a JAR file for Java applications or an executable file for C++ applications.
    
5. **Verification**: This stage involves checking the packaged application to ensure it meets the necessary quality standards. This can include code reviews, static code analysis, and security checks.
    
6. **Deployment**: The final stage is deploying the packaged application to a server or a cloud platform. This could be a staging environment for further testing or a production environment for end users.
    
7. **Monitoring**: After deployment, the application is monitored to ensure it is running smoothly and efficiently. This can involve tracking performance metrics, logging errors, and alerting developers to any issues.

# Be aware of key properties of build systems  
  - Speed, correctness, maintainability, minimality, self-tracking
  - Speed 
- Correctness
	- Should get the same results every time from the same inputs 
	- Leftovers from a previous build should not interfere with the next
- Maintainability
	- Ease to add new tasks or artifacts
	- Ease to reason about the build process 
- Exception for nondeterministic builds 
- Minimality
	- A build system is minimal if it executes tasks at most once per build and only if they transitively depend on inputs that charged since the previous build - Build System a la Carte
- Self-tracking
	- The build system can detect when a task has changed and recomputed the result automatically 

# Understand build system scheduling and optimizations
## Topological, restarting, suspending scheduling
- **Topological** (Make):
	- Use file modification times to detect changes
	- Execute tasks in topological order
- Example of Topological Sort
![[Pasted image 20240515111244.png|500]]

- **Restarting (Excel)**
	- Arrange tasks in a linear sequence
		- Check dependencies while computing. If Task C requires Task D, calculating C, put D before C in the sequence, then keep going 
		- May partially compute C several times

- **Suspending** (SHAKE)
	- Instead of aborting, freeze the computation state, compute the dependencies, then unfreeze 

## Early cutoff optimization
- Don't compute dependent tasks if the inputs haven't changed
- Supported by Shake and Bazel, not supported by Make or Excel

## Handling dynamic dependencies
1. **Dynamic Dependencies**: 
	- dependencies that change as a result of computation occurring during the build
	- They are unpredictable before the build starts and can vary between builds based on the results of certain computations or conditions during the build process
    
2. **Handling Dynamic Dependencies**: 
	- To support dynamic dependencies, some build systems interleave dependency analysis and builder execution
	- They enforce invariants on the dependency graph through a dynamic analysis
	- This allows the build system to adjust to changes in dependencies that occur during the build process
    
3. **Challenges**: 
	- Handling dynamic dependencies can be challenging because it introduces a level of unpredictability into the build process
	- This can make it harder to optimize the build process and can potentially lead to inconsistencies if not managed properly