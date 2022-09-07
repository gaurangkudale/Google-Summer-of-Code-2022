![alt text](https://github.com/gaurangkudale/Google-Summer-of-Code-2022/blob/main-gk/gsoc2022%20logo.png)


# Gradle support for SymbolicPathFinder 
The following report summarizes the work done during Google Summer of Code 2021 along with the results, scope for improvements and future work. This also serves as the final project report with all the contributions.
## Basic Info

- **Name:** Gaurang Kudale
- **Email:** gaurangkudale@yahoo.com
- **Github Username:** [gaurangkudale](https://github.com/gaurangkudale)
- **LinkedIn:** https://www.linkedin.com/in/gaurangkudale/
- **University:** [Pune University](http://www.unipune.ac.in/)
- **Organization:** [JavaPathFinder](https://github.com/javapathfinder)
- **Project Title:** Add gradle support to SPF.
- **Project Link:** [github.com/project-ideas](https://github.com/javapathfinder/jpf-core/wiki/GSoC-2022-Project-Ideas#support-gradle-for-spf)

&nbsp;
&nbsp;

## About [SymbolicPathFinder](https://github.com/SymbolicPathFinder/jpf-symbc)
Symbolic PathFinder (SPF) combines symbolic execution with model checking and constraint solving for test case generation. In this tool, programs are executed on symbolic inputs representing multiple concrete inputs. Values of variables are represented as numeric constraints, generated from analysis of the code structure. These constraints are then solved to generate test inputs guaranteed to reach that part of code. Essentially SPF performs symbolic execution for Java programs at the bytecode level. Symbolic PathFinder uses the analysis engine of the Ames JPF model checking tool (i.e. jpf-core).

&nbsp;
&nbsp;

## **Work Summary**
- **Migrate the build from Ant to Gradle.**
- **Add jpf-core as Git-Submodule to SPF.**
- **Restructuring SPF.**
- **Upgrade the Gradle version of jpf-symbc (5.4.1 to 6.9).**
- **Build Continuous Integration (CI) pipeline for jpf-symbc.**
- **Upgrade the Documentation of jpf-symbc.**

&nbsp;
&nbsp;

## **Overview**

Gradle is a build automation tool known for its flexibility to build software. A build automation tool is used to automate the creation of applications. The building process includes compiling, linking, and packaging the code. The process becomes more consistent with the help of build automation tools. Currently, SymbolicPathFinder is using Ant as a build automation tool but the Gradle resolves all the issues faced by build tools like Maven and ANT. It is Well-Known to be highly customizable when it comes to different projects dealing with various technologies. We can customize the project according to the needs of the project. Gradle is popular to provide high-speed performance, nearly twice as fast as Maven. Gradle makes it easy to build common types of projects by adding layers of conventions and pre-built functionality through plugins. We can apply all those to enhance our SPF project. In SPF we have introduced gradle multi-project build by adding jpf-core as a git-submodule pluse restructuring the hole repository accourding to the dependencies declared.

&nbsp;

- **Current Directory structure of SPF**
&nbsp;
```{bash}
     SPF (Gradle Root Project)
        ---| jpf-core (Git-Submodule + Gradle Sub-Project)
        ---| jpf-symbc (Gradle Sub-Project)
```
After adding [jpf-core](https://github.com/javapathfinder/jpf-core) as a git-submodule to the SPF, We have linked the another repository to SPF and as we know jpf-symbc depends on artifacts produced by the jpf-core. The main gole of introducing git-submodule is to download and build jpf-symbc as well as jpf-core at once for better user experience.In future if there is another project which depends on artifacts produced by either jpf-core/jpf-symbc then we as add it at the same lavel of gradle sub-project.

&nbsp;
In this project, we also have Continuous Integration (CI) pipeline functionality available from now on, Which will get triggered when code changes and any PR made by the contributor, It should make sure all of your changes work with the rest of the code when it's integrated. It should also compile your code, run tests, and check that it's functional, Here the GitHub Action is used to impliment the CI pipeline.


## Pull Request and Git-Commits
>### The main Pull-Request : [#76](https://github.com/SymbolicPathFinder/jpf-symbc/pull/76)

- :heavy_check_mark: [#1 git-commit](https://github.com/SymbolicPathFinder/jpf-symbc/pull/76/commits/2d45b091b473b6345f63deaa43745aa9e44c19f9)  **Migrate the build from Ant to Gradle.**
- :heavy_check_mark: [#2 git-commit](https://github.com/SymbolicPathFinder/jpf-symbc/pull/76/commits/64ef1b03602ca217dbf6492597250e6a451c933b)  **Add jpf-core as Git-Submodule to SPF.**
- :heavy_check_mark: [#3 git-commit](https://github.com/SymbolicPathFinder/jpf-symbc/pull/76/commits/a4bbad74e4f3af254287caf60f8389c6cd41022c)  **Upgrade the Gradle version of jpf-symbc (5.4.1 to 6.9).**
- :heavy_check_mark: [#4 git-commit](https://github.com/SymbolicPathFinder/jpf-symbc/pull/76/commits/61ae27530de3425c3a6295b81e19e61a35ab377d)  **Build Continuous Integration (CI) pipeline for jpf-symbc.**
- :heavy_check_mark: [#5 git-commit](https://github.com/SymbolicPathFinder/jpf-symbc/pull/76/commits/c9dd5915cfe8628996de79f4b1f849e6d38acadb)  **Upgrade the Documentation of jpf-symbc.**
- :heavy_check_mark: [#6 git-commit](https://github.com/SymbolicPathFinder/jpf-symbc/pull/76/commits/794c9f3ee9c4b669da597690964a0209b4c0bd77)  **Restructuring SPF.**
- :heavy_check_mark: [#7 PR](https://github.com/javapathfinder/jpf-core/pull/339) , [#8](https://github.com/javapathfinder/jpf-core/pull/338) & [#9](https://github.com/javapathfinder/jpf-core/commit/b75579ae1e162a01f708702e66ab1522f0419d3c)  **Fixing the unexpected bugs in jpf-core i.e. adding missing import statments**


## Future Scope
- Improve Junit testing by fixing some unit tests and adding new unit tests.
- Migrating Junit 4.12 to Junit 5.
- Updating java version 8 to 11 or 12.

## Note of Thanks
It was a great experience working for three months on my project for Java Pathfinder under Google Summer of Code. I sincerely thank my mentors **Yannic Nollar** and **Corina Pasareanu** whose support, guidance and continuous encouragement helped me immensely in bringing this work where it stands.

Thanks, Google and Java Pathfinder for giving me this opportunity.
