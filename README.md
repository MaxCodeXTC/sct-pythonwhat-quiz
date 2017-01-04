# sct-testwhat-quiz

This repo contains a number of python exercises, many of which are missing SCTs.
Each exercise has a number of passing or failing submissions (shown below).
Complete the missing SCTs to the best of your ability, so that each listed solution passes or fails appropriately, and with the correct feedback message.

![](img/example_exercise.png)

## How to Take the Quiz

Simply fork this repo, and modify the exercises in the teach editor. 
See the section below for directions on using the teach editor.

---

## DataCamp Template Course
<a href=https://www.datacamp.com//teach/repositories/77063397/go target="_blank"><img src="https://s3.amazonaws.com/assets.datacamp.com/img/github/content-engineering-repos/course_button.png" width="150"></a>
<a href=https://www.datacamp.com//teach/repositories target="_blank"><img src="https://s3.amazonaws.com/assets.datacamp.com/img/github/content-engineering-repos/dashboard_button.png" width="150"></a>

This an automatically generated <a href=https://www.datacamp.com target="_blank">DataCamp</a> course. You can start from these template files to create your own course.

Changes you make to this GitHub repository are automatically reflected in the linked DataCamp course. This means that you can enjoy all the advantages of version control, collaboration, issue handling ... of GitHub.

## Workflow

1. Edit the markdown and yml files in this repository. You can use GitHub's online editor or use <a href=https://git-scm.com/ target="_blank">git</a> locally and push your changes.
2. Check out your build attempts on the <a href=https://www.datacamp.com//teach/repositories target="_blank">Dashboard</a>.
3. Check out your automatically updated <a href=https://www.datacamp.com/teach/repositories/77063397/go target="_blank">course on DataCamp</a>

## Getting Started

A DataCamp course consists of two types of files:

- `course.yml`, a <a href=http://docs.ansible.com/ansible/YAMLSyntax.html target="_blank">YAML-formatted file</a> that's prepopulated with some general course information.
- `chapterX.md`, a markdown file with:
   - a YAML header containing chapter information.
   - markdown chunks representing DataCamp Exercises.

To learn more about the structure of a DataCamp course, check out the <a href=https://www.datacamp.com//teach/documentation#tab_course_structure target="_blank">documentation</a>.

Every DataCamp exercise consists of different parts, read up about them <a href=https://www.datacamp.com//teach/documentation#tab_code_exercises target="_blank">here</a>. A very important part about DataCamp exercises is to provide automated personalized feedback to students. In python, these so-called Submission Correctness Tests (SCTs) are written with the <a href=https://github.com/datacamp/testwhat target="_blank">`testwhat`</a> package. SCTs for Python exercises are coded up with <a href=https://github.com/datacamp/pythonwhat target="_blank">`pythonwhat`</a>. Check out the GitHub repositories' wiki pages for more information and examples.

Want to learn more? Check out the <a href=https://www.datacamp.com//teach/documentation target="_blank">documentation</a> on teaching at DataCamp.

*Happy teaching!*
