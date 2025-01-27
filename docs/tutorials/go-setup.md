# Kavin's Go Hello World tutorial

Primary Author: Kavin Sankar (https://github.com/ksankar15)

This tutorial will teach you how to setup a devcontainer and create a basic Go program. You will not even need to have Go installed on your computer thanks to the power of devcontainers.

<h3><strong>Prerequisites</strong></h3>

Make sure you have:

<ol>
    <li> A GitHub account</li>
    <li> Git installed</li>
    <li> VS Code installed</li>
    <li> Docker installed</li>
    <li> Command Line and Terminal Experience</li>
</ol>

<h3><strong>Part 1: Initialization and Setup</strong></h3>

<h4><strong>Step 1: Create a Local Directory and initialize Git</strong></h4>

(1) Open your terminal or command prompt.

(2) Create a new directory for your project. (Note: Of course, if you'd like to organize this tutorial somewhere else on your machine, go ahead and change into that parent directory first. By default this will be in your user's home directory.):

    mkdir go-tutorial
    cd go-tutorial

(3) Initialize a new Git repository:

    git init

(4) Create a README with a link to this page:

    echo "# Go Tutorial" > README.md
    echo "Link to tutorial: https://ksankar15.github.io/comp423-course-notes/tutorials/go-setup/" >> README.md
    git add README.md
    git commit -m "Initial commit with README"

<h4><strong>Step 2: Create a Remote Repository on GitHub</strong></h4>

(1) Log in to your GitHub account and navigate to the Create a New Repository page.

(2) Fill in the details as follows:

Repository Name: comp423-go-tutorial<br>
Description: "Hello World in Go"<br>
Visibility: Public<br>
<br>
(3) Do not initialize the repository with a README, .gitignore, or license.

(4) Click <strong>Create Repository</strong>.

<h4><strong>Step 3: Link your Local Repository to GitHub</strong></h4>

(1) Add the GitHub repository as a remote:

    git remote add origin https://github.com/<your-username>/comp423-go-tutorial.git

Replace <code>&lt;your-username&gt;</code> with your GitHub username.

(2) Check your default branch name with the subcommand <code>git branch</code>. If it's not <code>main</code>, rename it to <code>main</code> with the following command: <code>git branch -M main</code>. Old versions of git choose the name <code>master</code> for the primary branch, but these days <code>main</code> is the standard primary branch name.

(3) Push your local commits to the GitHub repository:

    git push --set-upstream origin main

(4) Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use <code>git</code> log locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.

<h3><strong>Part 2: Setting up the DevContainer</strong></h3>

<h4><strong>Step 1: Add DevContainer Configuration</strong></h4>

<ol>
    <li>In VS Code, open the <code>go-tutorial</code> directory. You can do this via: File > Open Folder.</li>
    <li>Install the <strong>Dev Containers</strong> extension for VS Code.</li>
    <li>Create a <code>.devcontainer</code> directory in the root of your project with the following file inside of this "hidden" configuration directory:</li>
    <code>.devcontainer/devcontainer.json</code>
</ol>

In the <code>devcontainer.json</code> file put in the following code to configure the devcontainer.

    {
        "image": "mcr.microsoft.com/vscode/devcontainers/go:0-1",
        "extensions": [
        "   golang.go"
        ],
        "settings": {
            "go.useLanguageServer": true
        }
    }

<h4><strong>Step 2. Reopen the Project in a VSCode Dev Container</strong></h4>
Reopen the project in the container by pressing <code>Ctrl+Shift+P</code> (or <code>Cmd+Shift+P</code> on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running <code>go version</code> in the terminal to see your dev container is running a recent version of Go.

<h3><strong>Part 3: Creating Hello World in Go</strong></h3>

<h4><strong>Step 1: Initialize a Go module</strong></h4>

Initialize a new go module by running the following command inside the VS Code terminal (which is now inside the devcontainer):

    go mod init tutorial.com/hello_world

<h4><strong>Step 2: Code Hello World</strong></h4>

Create a new file called <code>main.go</code> in your directory with the following code.

    package main

    import "fmt"

    func main() {
        fmt.Println("Hello World")
    }

<h4><strong>Step 3: Running Hello World without creating a binary executable</strong></h4>

To quickly run your Hello World program without creating a binary executable type the following command in your terminal:

    go run main.go

You should see an "Hello World" printed to your terminal as a result of running <code>main.go</code>.

<h4><strong>Step 4: Running Hello World by creating a binary executable</strong></h4>

(1) The <code>go build</code> command compiles packages and dependencies into an executable binary file. In order to build the <code>main.go</code> file run the following command in the terminal:

    go build -o hello_world main.go

This command creates an executable file named <code>hello_world</code> in your working directory.

(2) Next, run the following line in your terminal:

    ./hello_world

This command runs the compiled executable <code>hello_world</code> and prints out "Hello World" just like when we used the <code>go run main.go</code> command. But this time instead of using the <code>run</code> subcommand, which directly compiles and executes Go code without creating a seperate binary file, with the <code>build</code> subcommand, we compile source code into an executable binary file. This process is similar to when in COMP 211 we would manually compiles C programs with <code>gcc</code> command to call the GNU C Compiler, which would give us an executable file <code>a.out</code> to run.

<h3><strong>Part 4: Pushing to GitHub</strong></h3>

Now that we have finished our Hello World program in Go, we want to push it to GitHub.

(1) In order to do that we first need to stage and commit our changes with the following commands:

    git add .
    git commit -m "Hello World Program"

(2) Then we push the changes to GitHub:

    git push origin main

Now we have officially finished our Hello World program and uploaded it to GitHub. Congrats!