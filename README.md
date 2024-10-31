# Omaka
Sandbox Angular/Nestjs application using dev containers and nx for build management

## Prerequisites
### Windows PCs
1) Ensure HyperV is enabled both in BIOS and Windows
2) Install WSL2
3) Install Docker Desktop
4) Install Visual Studio Code
5) Add the Remote Development set of extensions to VS Code

### MacOS
TBD.


## nx Workspace

First step is to create the nx workspace. This will be the container for the Angular and Nestjs applications.

First create a code folder in the WSL2 portion of the hard drive. This is where the code will be stored and where the dev container will be mounted.
Even though we will be using containers, they are more efficient mounting a Linux folder than a Windows folder outside of WSL2.

Then create the nx workspace in the code folder. The workspace will be called Omaka.

```sh
npx create-nx-workspace@latest Omaka --package-manager=pnpm
```

Select the angular application. Will add the nestjs application later.


## Dev Container
The development environment will exist in a Docker container that can be used in any environment meeting the prerequisites above. Open the workspace folder in VS Code and create a dev container configuration file.


1) Add Dev Container Configuration Files: Nodejs & Javascript. Will add Typescript, Angular CLI, Nest CLI, pnpm and nx as a features.
2) Add the VS Code extensions to the dev container configuration file.
3) Open the repository as a container in VS Code.
4) Add the list of recommended extensions to the dev container configuration file. - see the devcontainer.json file in the .devcontainer folder for the extensions.
5) Forward the port 4000 in the dev container to the host machine for running Angular app in the host browser.
6) Update the name of the dev container in the devcontainer.json file.
7) Rebuild the dev container

At this stage you now have an dev container with a monorepos with an angular application and the necessary tools to start building the application.


## Repository
Create an empty repository in GitHub and push the local code to the repository.

```sh
git remote add origin https://github.com/<user name>/Omaka.git
git push -u origin main
```

## Nestjs Server Project
Create a nestjs project in the nx workspace.

```sh
pnpm add @nx/nest
nx generate @nx/nest:app apps/omaka-server
```

# nx
✨ Your new, shiny [Nx workspace](https://nx.dev) is ready ✨.

[Learn more about this workspace setup and its capabilities](https://nx.dev/getting-started/tutorials/angular-monorepo-tutorial?utm_source=nx_project&amp;utm_medium=readme&amp;utm_campaign=nx_projects) or run `npx nx graph` to visually explore what was created. Now, let's get you up to speed!

## Run tasks

To run the dev server for your app, use:

```sh
npx nx serve omaka-client
```

To create a production bundle:

```sh
npx nx build omaka-client
```

To see all available targets to run for a project, run:

```sh
npx nx show project omaka-client
```

These targets are either [inferred automatically](https://nx.dev/concepts/inferred-tasks?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) or defined in the `project.json` or `package.json` files.

[More about running tasks in the docs &raquo;](https://nx.dev/features/run-tasks?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Add new projects

While you could add new projects to your workspace manually, you might want to leverage [Nx plugins](https://nx.dev/concepts/nx-plugins?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) and their [code generation](https://nx.dev/features/generate-code?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) feature.

Use the plugin's generator to create new projects.

To generate a new application, use:

```sh
npx nx g @nx/angular:app demo
```

To generate a new library, use:

```sh
npx nx g @nx/angular:lib mylib
```

You can use `npx nx list` to get a list of installed plugins. Then, run `npx nx list <plugin-name>` to learn about more specific capabilities of a particular plugin. Alternatively, [install Nx Console](https://nx.dev/getting-started/editor-setup?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) to browse plugins and generators in your IDE.

[Learn more about Nx plugins &raquo;](https://nx.dev/concepts/nx-plugins?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) | [Browse the plugin registry &raquo;](https://nx.dev/plugin-registry?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Set up CI!

### Step 1

To connect to Nx Cloud, run the following command:

```sh
npx nx connect
```

Connecting to Nx Cloud ensures a [fast and scalable CI](https://nx.dev/ci/intro/why-nx-cloud?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) pipeline. It includes features such as:

- [Remote caching](https://nx.dev/ci/features/remote-cache?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [Task distribution across multiple machines](https://nx.dev/ci/features/distribute-task-execution?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [Automated e2e test splitting](https://nx.dev/ci/features/split-e2e-tasks?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [Task flakiness detection and rerunning](https://nx.dev/ci/features/flaky-tasks?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

### Step 2

Use the following command to configure a CI workflow for your workspace:

```sh
npx nx g ci-workflow
```

[Learn more about Nx on CI](https://nx.dev/ci/intro/ci-with-nx#ready-get-started-with-your-provider?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Install Nx Console

Nx Console is an editor extension that enriches your developer experience. It lets you run tasks, generate code, and improves code autocompletion in your IDE. It is available for VSCode and IntelliJ.

[Install Nx Console &raquo;](https://nx.dev/getting-started/editor-setup?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Useful links

Learn more:

- [Learn more about this workspace setup](https://nx.dev/getting-started/tutorials/angular-monorepo-tutorial?utm_source=nx_project&amp;utm_medium=readme&amp;utm_campaign=nx_projects)
- [Learn about Nx on CI](https://nx.dev/ci/intro/ci-with-nx?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [Releasing Packages with Nx release](https://nx.dev/features/manage-releases?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [What are Nx plugins?](https://nx.dev/concepts/nx-plugins?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

And join the Nx community:
- [Discord](https://go.nx.dev/community)
- [Follow us on X](https://twitter.com/nxdevtools) or [LinkedIn](https://www.linkedin.com/company/nrwl)
- [Our Youtube channel](https://www.youtube.com/@nxdevtools)
- [Our blog](https://nx.dev/blog?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
