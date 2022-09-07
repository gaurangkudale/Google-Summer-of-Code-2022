![alt text](https://github.com/gaurangkudale/Google-Summer-of-Code-2022/blob/main-gk/gsoc2022%20logo.png)


# Gradle support for SymbolicPathFinder 
> By [Gaurang Kudale](https://www.linkedin.com/in/gaurangkudale/)

&nbsp;
&nbsp;

### About [SymbolicPathFinder](https://github.com/SymbolicPathFinder/jpf-symbc)
Symbolic PathFinder (SPF) combines symbolic execution with model checking and constraint solving for test case generation. In this tool, programs are executed on symbolic inputs representing multiple concrete inputs. Values of variables are represented as numeric constraints, generated from analysis of the code structure. These constraints are then solved to generate test inputs guaranteed to reach that part of code. Essentially SPF performs symbolic execution for Java programs at the bytecode level. Symbolic PathFinder uses the analysis engine of the Ames JPF model checking tool (i.e. jpf-core).

&nbsp;
&nbsp;

### **Work Summary**
- **Migrate the build from Ant to Gradle.**
- **Add jpf-core as Git-Submodule to jpf-symbc.**
- **Upgrade the Gradle version of jpf-symbc (5.4.1 to 6.9).**
- **Build Continuous Integration (CI) pipeline for jpf-symbc.**
- **Upgrade the Documentation of jpf-symbc.**

&nbsp;
&nbsp;

### **Overview**

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
In this project, we also have Continuous Integration (CI) pipeline functionality available from now which will get triggered when code changes and any PR made by the contributor, It should make sure all of your changes work with the rest of the code when it's integrated. It should also compile your code, run tests, and check that it's functional, Here the GitHub Action is used to impliment the CI pipeline.
