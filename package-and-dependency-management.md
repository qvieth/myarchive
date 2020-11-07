# [package-and-dependency-management](https://guides.sonatype.com/foundations/devops/out-of-wild-pkg-dep-mgmt/)

<!-- vim-markdown-toc GFM -->

* [what do we mean when we say package and dependency management?](#what-do-we-mean-when-we-say-package-and-dependency-management)
* [Application-level Package (or Dependency) Managers](#application-level-package-or-dependency-managers)
* [How do Application-level Package Managers Work?](#how-do-application-level-package-managers-work)
    * [Project code](#project-code)
    * [Manifest file](#manifest-file)
    * [Lock file](#lock-file)
    * [Dependency code](#dependency-code)
    * [process summary](#process-summary)
    * [Application-level Package Manager - 3 Examples](#application-level-package-manager---3-examples)
        * [Maven Example](#maven-example)
        * [npm Example](#npm-example)
        * [.NET Example](#net-example)
    * [And then there’s this other type of package manager…](#and-then-theres-this-other-type-of-package-manager)
    * [I use a Version/Source Control Management repository to store my source code. Why do I need a Repository Manager for my binaries?](#i-use-a-versionsource-control-management-repository-to-store-my-source-code-why-do-i-need-a-repository-manager-for-my-binaries)

<!-- vim-markdown-toc -->

you will learn :
    - the role of __package managers__, their corresponding __language-specific registries__
    - the key components of an __application-level package__ (or __dependency__) manager and how they work, including examples for 3 different programming languages
    - how a universal package manager (i.e., binary repository manager) differs from __language-specific registries/repositories__ and __source control__ management repositories, and why it’s a critical piece in your devops toolchain.

## what do we mean when we say package and dependency management?
- __package manager - dependency management - repository - and repository manager__
- let’s get to the heart of what we mean when we talk about these terms in the context of __devops__
- some of the most common __devops concepts__ and __related tooling__ include source control management (scm) solutions like _github_
- __ci/cd servers__ like _jenkins_ or _bamboo_ for automating stages of your __software development lifecycle__ (sdlc)
- __automated infrastructure configuration__ management tooling like _ansible, terraform, chef_ or _puppet_
- and __containerization__ and __orchestration tools__ like _docker_ and _kubernetes_
- the __universal package manager__ can be a key component in helping “further the technical and cultural goals of devops” in your organization.

## Application-level Package (or Dependency) Managers
- So, what are __application-level__ package/dependency managers?
- Examples of application-level package managers include:
    - Apache Maven
    - npm
    - NuGet
    - RubyGems
    - PyPI
- the role of software developer has changed in recent years, and the __reliance on open source software__ to build applications only to increase.
- This means that the applications we develop often depend on other people’s code
- In fact, according to Sonatype’s State of the Software Supply Chain Report, a modern application is made up of more than 80% OSS components.
- With this reliance on third-party dependencies to build software comes the realization that things can get messy quickly
- especially when a __direct dependency__ pulls in another component, resulting in nested transitive dependencies

- Managing this intricate web of __dependencies__ out in the wild, unassisted, is no small task
- Here is where application-level package managers can help:
    - to build our software we need to bring in all parts on which it depends
    - including __language libraries__ and __remote third-party modules__
    - But it’s important to ensure that we have all necessary __dependencies__, particularly when dependencies themselves __depend on others__
    - This is why we need a __Dependency Manager__, often invoked during the software __build process__

- __Application-level package managers__ are often closely linked to an __online repository__ (__aka registry__) that stores __packages__ (refered as __libraries__) for that particular programming language
- For example, __Maven__ by default sources components from the __Central Repository for Java (and other languages) that Sonatype manages__, and __npm__ pulls packages from the Javascript registry at npmjs.org.

## How do Application-level Package Managers Work?
- We’ve established that managing dependencies is a complex task
- But as Boyer explains in his Medium article, “It’s not the algorithmic side that makes [application-level package managers] hard.”
- Apache Maven application-level package manager's primary goal is to :
    - making the build process easy
    - providing quality project information

- We’re simplifying a bit, but below are the key components used by most application dependency managers
- It’s the interplay—and forward “movement”—of the elements listed below that makes for an effective dependency management system

### Project code
- First you have your source code that’s being actively developed
- that is, the project you want the application-level package manager to manage dependencies for
- This is usually stored in a Source Code Manager (SCM), such as GitHub.

### Manifest file
- A __manifest__ is a file, specific to your particular __application-level package manager__, that you create to list the direct __dependencies__ necessary for your project
- It nails down your __intent__, such as using version 1.4 and above for Package X.

### Lock file
- A __lock file__, then, is machine-generated from the manifest
- and it contains the actual dependencies and versions that the application-level package manager resolved from the manifest file as the project was being built
- It basically contains all of the information necessary to __reproduce__ the __project’s dependencies__

### Dependency code
- Next, the dependency code is generated
- containing all of the __source code__ and/or __binary files__ as listed in the __lock file__
- and __arranged on disk__ such that the compiler/interpreter will find and use it as __intended__
- but __isolated__ so that nothing else would have a reason to __mutate__ it

### process summary
- Dependency managers start by __reading the manifest file__, in which direct dependencies are noted
- They then __read the metadata__ of these __dependencies__ from their repositories to figure out the __next level__ of dependencies
- In other cases, they may download the dependencies right away and then process their dependencies
- Either way, all dependencies must be downloaded and installed

### Application-level Package Manager - 3 Examples
#### Maven Example
- As we briefly mentioned earlier, the Maven application-level package manager is based on a Project Object Model (POM)
- The pom.xml is Maven’s take on a manifest file, including all of the necessary information to build a Java application
- According to Maven’s docs, “the cornerstone of the POM is its dependency list.” When your project is compiled, Maven downloads and links your OSS dependencies, including “the dependencies of those dependencies (transitive dependencies), allowing your list to focus solely on the dependencies your project requires.”
- Here is an example snippet from the Dependencies subsection of the docs:
```
 <dependencies>
   <dependency>
     <groupId>junit</groupId>
     <artifactId>junit</artifactId>
     <version>4.12</version>
     <type>jar</type>
     <scope>test</scope>
     <optional>true</optional>
   </dependency>
   ...
 </dependencies>
```
- for more information on the groupID, artifactId, version, type, and other parameters that make up the Dependencies section of the pom.xml, see Maven’s docs.
- You may have noticed that we haven’t mentioned a lock file for Maven yet
- In the Maven package manager, according to this StackOverflow thread :
- “There is no need to have a feature such as ‘lock file’, or anything like this, if your pom.xml strictly defines the versions of your dependencies.”
- So, if you declare a specific version in your pom.xml, Maven will only resolve that version; therefore, your pom.xml becomes both a manifest and a lock file.
- There are differing schools of thought around how to specify your dependency versions in any application-level package manager’s manifest
- but if you lean toward the school of thought that favors version specificity (i.e., avoiding version ranges) as part of enabling reproducible builds
- the lock file becomes unnecessary
- Reproducible, or deterministic, builds are increasingly seen as a best practice within software development

#### npm Example
- In the case of the node package manager (npm), the package.json file serves as the project manifest
- For Javascript developers using npm, use of version ranges when specifying their dependencies is pretty common
- likely because it’s mentioned explicitly in the docs (but also because it’s less maintenance and enables faster updating of dependencies)
- and so lock files in the form of a package-lock.json or npm-shrinkrap.json are used to document the exact versions that were ultimately used in the build process
- Note that even with the “manifestation of the manifest” documenting the package versions used in the lock file
- there are certain risks with specifying “latest” or version ranges for your dependencies, and we’ll discuss that a bit more later on.)
- Here is a package.json snippet from the npm docs showing an example:
```
{
  "name": "my_package",
  "version": "1.0.0",
  "dependencies": {
    "my_dep": "^1.0.0",
    "another_dep": "~2.2.0"
  }
}
```
#### .NET Example
- In the case of the NuGet application-level package manager used by .NET developers, a .nuspec file is used as the manifest
- Here is an example .nuspec snippet with dependencies specified:
```
  <dependencies>
      <dependency id="another-package" version="3.0.0" />
      <dependency id="yet-another-package" version="1.0.0" />
  </dependencies>
```
- In addition, lock file functionality for NuGet was somewhat recently introduced, for NuGet.exe versions 4.9 and above.

### And then there’s this other type of package manager…
- Once the components that make up your application are downloaded, and your machine understands how to arrange them using your application-level package manager
- where do the components and “built” artifacts go?
- Enter the __universal package manager__ (a.k.a., __binary Repository Manager__):
    - Also known as binary repository manager, it is a software tool designed to optimize the download and storage of binary files, artifacts and packages used and produced in the software development process
    - These package managers aim to standardize the way enterprises treat all package types
    - They give users the ability to apply security and compliance metrics across all artifact types
    - Universal package managers have been referred to as being at the center of a DevOps toolchain

- So, why do I need a Binary Repository Manager?
- Binary repository managers serve a couple of important functions as part of a modern software development lifecycle.
- First, they can serve as a local copy, or “proxy,” repository for the language-specific package repositories/registries we discussed earlier
- Creating these proxy repositories in a repository manager to store and cache your OSS components locally
- rather than downloading them directly from an online repository every time you kick off a build—can provide some of the following benefits
    - Increasing build performance due to a wider distribution of software and locally available parts.
    - Reducing network bandwidth and dependency on remote repositories.
    - Insulating your company from outages in the internet, outages of public repositories (Maven Central, npm, etc.), or even removal of an open source component.
- In addition, repository managers serve as a “single source of truth” for the binaries used in your build processes.
- At this stage, you may be asking yourself, but why can’t I just store my binaries where I store my source code?
- And the short answer is that you can
- But you probably won’t want to after you understand more about how version or source control tools like GitHub differ from binary repository managers…

### I use a Version/Source Control Management repository to store my source code. Why do I need a Repository Manager for my binaries?
- Repository Managers vs VCS (Version Control Systems)
- binary files are much larger in size, and need a lot of metadata stored with them, such as package name, version, license, etc
- They also don’t need to be diffed or cloned in the way that source code does.
- Because of these differences, an __artifact repository__ makes a lot more sense for __storing binaries__, whether they’re the outputs of your build (.zip, .jar, .war, etc.), packages downloaded from an online registry, Docker images, etc.
- This thread on StackOverflow also provides some clarification on how the two tools differ:
    - In everyday use, you’d store your source code and its history in a github
    - and store your __build artifacts__ (e.g. the __compiled software__ you want to deliver) in Nexus
- Put more succinctly: “You manage what you code in Git, and what you build in Nexus.”

- while __proxy repositories__ are the best method to store open source packages downloaded from online registries (registrar) as we mentioned earlier
- __hosted repositories__ can serve as a means to store your __internal build artifacts__, including __snapshots__ and __releases__

- Lastly, another advantage that repository managers provide is risk reduction in your build process
- We alluded earlier to opening yourself up to certain risks when specifying the “latest” versions of a particular dependency
- or even a version range, in your application-level package manager’s manifest
- Downloading unvetted versions directly from online registries presents more risk because bad actors are increasingly poisoning the well
- injecting malicious code into libraries or removing them all together.

- the ability to insulate yourself from outages or vulnerabilities that may occur in such cases is made possible by use of a caching repository manager.

- putting it all together [(see the picture)](https://guides.sonatype.com/foundations/devops/out-of-wild-pkg-dep-mgmt/) 
- more course [repository management basics](https://learn.sonatype.com/courses/nxrm-admin-100/)
