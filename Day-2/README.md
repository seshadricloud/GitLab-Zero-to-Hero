# How to onboard the project on Gitlab ?
There are multiple ways to onboard projects on Gitlab, We can see two types onboarding process

### Most commons ways:
- Import project
- Create blank project

#
### 1. Onboarding using "Import project" option :
- Navigate to the home page of Gitlab.
- Click on <b>New Project</b>
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/New-proj.png" />

#
- After that, you will see 4 types of onboarding options, click on <b>Import project</b> option
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/Import-project.png" />

#
- Click on <b>GitHub</b> option
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/Import-GitHub.png" />

#
- We can authenticate GitHub acount using 2 ways, either click on <b>Authenticate with GitHub</b> button or provide <b>Personal Access Token</b> and click on <b>Authenticate</b> button
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/Gitlab-PAT.png" />

#
- Search the project whichever you want to onboard and click on <b>Import repository</b> button
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/GItlab-node.png" />

#
- Once project is <b>Imported</b> to Gitlab, you will see <i>Completed</i> as shown in the below screeshot
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/Gitlab-nodeimp-complete.png" />

#
- Verify
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/gitlab-importVerify.png" />

#
### 2. Onboard project using "Create blank project" option :
- Click on <b>New Project</b>
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/New-proj.png" />

<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/Blank-proj.png" />

#
- Enter the project name, visibility and click on <b>Create Project</b>

#
- Login to your ubuntu server and clone the code which you want to onboard on Gitlab repository
```bash
git clone https://github.com/DevMadhup/django-todo-cicd.git
```

#
- Go to the cloned repository
```bash
cd django-todo-cicd
```

#
- Set your Gitlab remote origin repository
```bash
git remote set-url origin https://gitlab.com/devmadhup1/django-app.git
```
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/gitlab-seturl.png" />

#
- Push your code
```bash
git push -uf origin main
```
<b>Note: If your get error like below</b>
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/Gitlab-pusherror.png"/>

<b>Go to project: "Settings" → "Repository" → scroll down to "Protected branches" and allow "Force push" and "Allowed to push and merge" to Maintainers + Developers</b>
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/gitlab-protectedBranch.png"/>

#
- Again try to push code (Execute this step only if you get error on first push) :
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/Code-pushed-Gitlab.png"/>

#
- Verify on Gitlab :
<img src="https://github.com/DevMadhup/GitLab-Zero-to-Hero/blob/main/Assets/Verify-BlankCodePush-Gitlab.png"/>

#
# First CI/CD pipeline in Gitlab :

- Navigate to your code repository
- Create a new file <b>.gitlab-ci.yml</b> in your repository's root path.
> Note: Name must be .gitlab-ci.yml only
- Paste the below code in the <b>.gitlab-ci.yml</b> file and save it.
```bash
stages:
  - build
  - test
  - deploy

build_job:
  stage: build
  script:
    - echo "Building project $CI_PROJECT_NAME"

test_job:
  stage: test
  script:
    - echo "Running tests"

deploy_job:
  stage: deploy
  script:
    - echo "Deploying to production"
```
- Scroll down and navigate to <b>Build > Jobs</b> to see your jobs.
