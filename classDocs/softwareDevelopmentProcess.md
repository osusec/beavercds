# Software Development Process

## Principles

- We will maintain a weekly meeting with our project supervisor to keep the team and
supervisor on the same page.
- We are responsive with our asynchronous communication and answer within 24 hours via discord.
- We will use GitHub issues to keep a backlog of issues.
- The backlog will always have work items ready for the next two weeks at the minimum.
- All changes need to be developed in a separate git branch.
- Once the bug is found a new issue is made to keep track of it.
- We divide the work into two distinct phases: bug identification and bug resolution.
- The Pull Request has to be reviewed by at least one team member before being merged.
- The Pull Request needs to comply with the Definition of Done (see later) and should be linked to the corresponding work item.
- Major project decisions will be made collaboratively, with each team member having a say in shaping the project's direction. This will primarily happen in midweek meetings with just the team present but also could happen with meetings with the project manager.

## Process

- The team will conduct backlog planning meetings every week (Friday 3:45 PM) with the
project manager to prioritize tasks and identify the most critical issues. During these
meetings, you will refine and add new items to the backlog.
- A GitHub issues page is made and will be kept up to date with new and old tasks along with the team member responsible for the task. Found bugs will result in the creation of an issue.
- Regular demo and review sessions will be held with stakeholders to showcase the progress made, discuss findings, and gather feedback. This can be done in the weekly meetings or additional meetings can be scheduled depending on the backlog of tasks.
- Assignments and responsibilities for each task are clearly defined within the team via GitHub issues.
- Code review is a crucial part of the process, ensuring that code changes meet quality standards and follow best practices. These will primarily be done in individual group meetings throughout the week without the project manager.
- Testing is a continuous aspect of the process. The team will develop comprehensive test cases and actively work on resolving identified bugs in a robust thorough manner.

## Roles

Nicholas Graves: Lead Engineer
Benjamin Lane: Lead Engineer
Kai Morita-McVey: Lead Engineer

| Tool/Category   | Solution |
|--------------- | --------------- |
| Version Control   | GitHub repository   |
| Project Management | GitHub issues and projects |
| Documentation | Documentation already exists for this project. Se we will be adding to an already existing set of documentation. [rCDS documentation](https://rcds.redpwn.net/en/latest/).|
| Test Framework | We will be using past CTF challenges as test deployments for our product. |
| Linting and Formatting | black and flake8 | 
| CI/CD | GitHub Actions |
| IDE | VSCode(ium), Vim |
| Graphic Design | Figma and pen and Paper (depending on task) |
| Others | Kubernetes (k8s) |

## Definition of Done (DoD)

- All acceptance criteria for the task or user story are validated and met.
- Code changes are successfully merged into the main branch of the version control repository.
- Comprehensive regression testing is conducted to ensure that the changes do not introduce new issues or regressions in existing functionality.
- Comprehensive regression testing is conducted to ensure that the changes do not introduce new issues or regressions in existing functionality.
- Any potentially game-changing alterations are recognized, assessed, and action is taken to lessen their effects or offer explicit instructions on how to adjust to the changes.
- The changes are deployed to a staging environment for final testing and validation before production deployment.
- The finished task or user story, together with any pertinent functionality, is showcased in a demo or presentation that will be created for the upcoming stakeholder meeting.
- A peer review process is conducted, involving at least one team member reviewing the code changes to ensure code quality and adherence to coding standards.

## Release Cycle

- Deploy to a staging environment after every successful merge to the main branch. This provides a continuous testing environment for ongoing development.
- Plan to release to the production environment after thorough testing and validation in the staging environment.
- Release bug fixes and patches as needed to address issues or vulnerabilities. These releases should be scheduled based on the severity and urgency of the bugs.
- Conduct release planning meetings to determine the content of each release, including features, bug fixes, and enhancements. Ensure that stakeholders are aligned on release priorities.
- Gather feedback from users and stakeholders after each release and use it for continuous improvement and refinement of the project.


## Environments

| Environment    | Infrastructure | Deployment | What is it for? | Monitoring |
|---------------- | --------------- | --------------- | --------------- | --------------- |
|Production | Kubernetes (k8s) | Release | Deploying the challenges | N/A|
|Staging (test) | Test using local k8s version | Pull Request | Testing and validating new bug fixes and features | N/A |
| Dev | Local | Commit | Development and unit tests | N/A|


