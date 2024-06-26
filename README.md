# Introduction
I'm big on DevOps. My goal, from the get-go has been to automate all deployments. In fact, DevOps is integrated in SDLC process for every release I've done.
Over the years my teams and I have spent a lot of time and effort experimenting and perfecting the deployment pipelines shared here.

# The Magic YAMLs
These yaml files are agnostic to the project/service and can be used by anyone.

## PR Builds
For any repo all you nedd are these 2 yaml files to run the gated PR builds:
- PR.Build.yaml
- build-and-test.yaml

The beauty of these files are:
- They do not need to be modified for each repo. When you create a new repo, just follow the instructions below
- They automatically build the project files and run the test cases in the repo they're present in
- They run for every PR that is created
- You can enforce code-coverage

### How to use it
1. Download the 2 yaml files and put them in a folder inside your solution
2. Create an ADO pipeline using the PR.Build.yaml file
3. Change the path/name pattern of your project under test and unit test projects
4. Save and run the pipeline to test

## NuGet Packages
For automated publish of NuGet package code from it's repo, we use the following 2 yaml files:
- NuGet.Publish.yaml
- build-and-test.yaml (which is also used by the PR build above)

The beauty of these files are:
- That they do not need to be modified for each repo. When we create a new nuget repo, ust follow the instructions below
- They automatically build the project files and run the test cases in the repo they're present in
- They publish the NuGet package automatically once the merge to main is complete
- The minor version of the package is automatically incremented with every deployment

### How to use it
1. Download the 2 yaml files and put them in a folder inside your solution
2. Create an ADO pipeline using the NuGet.Publish.yaml file
3. Change the path/name pattern of your nuget project and unit test projects
4. (optional) You can change the versioning scheme as you'd like 
5. Save and run the pipeline to test
