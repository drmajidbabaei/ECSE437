---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Topic#2 \[Taken]

Topic 2: [Can Git Repository Visualization Support Educators?](https://ieeexplore.ieee.org/abstract/document/9978497?casa\_token=1zERXMOA7wEAAAAA:qcoRX5TCLq5jBYgrzLaTfnpPolVXjxuKR\_0PNgxEPksrt600vOIW\_sNKePfen\_ERwvMA0lzB)

{% hint style="warning" %}
This topic is taken by **Felicia Sun**
{% endhint %}

This paper, published at the 2022 Working Conference on Software Visualization (VISSOFT), was authored by Mircea Lungu, Rolf-Helge Pfeiffer, Marco D’Ambros, Michele Lanza, and Jesper Findahl.

## 1. Introduction

The central premise of this paper is the exploration of how software visualization tools, primarily designed for software engineering professionals, can also prove to be invaluable assets in the realm of education. They aim to understand how these tools can aid educators in evaluating the quality of software systems developed by students. They also argue that educators are a special kind of user that can benefit from visualization tools.

Educators evaluating large projects in a short time have a different context than other stakeholders supported by visualization tools. Here are some examples of other stakeholders:

- Reverse engineers aim specifically at making sense of the code and usually have plenty of time to understand a system.
- Developers that are “onboarded” have ample time and also have access to the expertise of senior colleagues.
- Solo-developers who visualize their own software to identify improvement or refactoring candidates have deep expertise of their own code.
- Technology or domain experts have resources to learn and adopt specialized visualization tools over time.

## 2. Are educators a special kind of user for repository visualization tools?

Educators face some unique requirements and constraints:

- Educators need to assess large projects in a short amount of time. Those are often multi-person multi-month software systems that can easily reach tens of thousands of lines.
- The educator’s time is limited, and they can’t read complete solution. Also, the source code of the project is only one of multiple deliverables. They also need to look at the requirements, problem statement, user evaluation, experimental design, etc.
- Educators need to evaluate the individual contributions and not just the final result. Contributions can be unbalanced and they need to be able to easily spot any problems that might arise from this.
- An educator might also be teaching multiple courses with diverse technologies, or supervising multiple thesis projects simultaneously. This raises the need for a technology-independent tool.
- There are also have privacy concerns, since many educators might need to assess private or institutional repositories.

Following this, the authors of the paper have the following assumptions to carry out their research:

- Educators evaluate the students' code as part of the final assessment. They have limited time (e.g. 30 mins per group). In this time, they need to have at least a starting point for discussing with students.
- Projects are large and complex, making them impossible to understand completely in that limited time.
- Students work in groups and use file-based version control systems that track changes and their authors.

## 3. Using Git-Truck for Repository Visualization

The researchers used git-truck, a visualization which visualizes the structure of a git repository using hierarchical metric-enhanced layouts, such as circle packing visualizations or tree maps. The visual size of files is proportional to their size in bytes. Color maps are also used. The visualizations are highly interactive and support filtering, zooming, and presenting details on demand. Git truck supports author unification.

Git-truck is meant to be executed directly on personal computers from a local clone of a git repository (https://github.com/git-truck/git-truck).

## 4. Usage Examples

Examples were selected by the researchers in collaboration with educators from:

- IT University of Copenhagen (ITU) in Denmark
- Università della Svizzera italiana (USI) in Switzerland

The usage examples are based on observations from 4 different courses by those educators. Note that the images mentioned can be found in the original paper.

### Usage Example 1: Finding components with a single author

Git-truck has a feature that highlights files that only had a single author in red. This allows educators to make fast assessments of the degree of actual group work going on, so they can quickly detect if there are components or even entire projects without collaboration amongst students.

In one image, the researchers looked at a part of the source code of a group project.

The visualization looked at is zoomed into the terraform folder in a larger group project. Note that Terraform is an infrastructure-as-code tool. The image suggests that although the group has five members almost all the work on this component has a single author. Later on, during the oral exam component of the course, they gave the other group members the chance to discuss concepts of infrastructure-as-code but only one could do so in any meaningful way.

### Usage Example 2: Investigating Responsibility Distribution in a Project

Another feature of the visualization tool can color-code the top contributor of each file, defined as the author who added or removed the most lines of code in the file throughout the history of the project. The goal is to support gauging how the work is distributed between members in the project or in specific areas of the project.

In the example repository, we have the Top Contributors view in the repository of another group from the same course as the other one. We can tell that all the members worked on all parts of a backend system, though the dark purple author is the top contributor for a lower amount of files.

### Usage Example 3: Investigating Responsibility Distribution in a Project

For another visualization, we can see a single author being the top contributor to most of the code files in the project. The goal of the project is that students get to experience the composition of a larger application from independently taught components. The educator in that course used this as a starting point for a discussion with the students about the individual contributions.

By discussing with the students, it was revealed that the "top contributor" is a group member who was new to Git and accidentally deleted the entire repository. Then they added everything back again. This serves as a valuable reminder to not blindly act based on the visualizations but rather discuss them with students.

Git-truck provides a rudimentary feature for selecting the last commit up to which the analysis can be done. With the help of this feature, an educator can spot projects where collaboration only becomes an issue after a certain commit.

### Usage Example 4: Gaining High-Level Architectural Insights

There’s also a feature to use color-coding to represent files based on their file extensions, while also visually scaling them proportionally according to their size and folder containment hierarchy. This view is useful to gain insights into the structure of systems with multiple languages involved.

The authors compared two projects in an intro web-dev course where the students had to implement the same front-end using React. The yellow files are for Javascript and the purple files are for CSS. The researchers observed some important differences between the way different teams would organize the files. Some groups made one big CSS file and many JavaScript files, while others decided to distribute CSS files across the system.

It was thanks to this visual representation that they were able to witness these architectural extremes and realize the importance of discussing file organization in future iterations of the course.

### Usage Example 5: Uncovering Critical Components of a System

With another visualization, the files are coloured according to a gradient. The files that are changed the most are the darkest. One of the authors of this paper browsed a repository before they had access to git-truck without spotting the god class that handled user interface interactions, database querying, scheduling, everything. Features like this one can be useful to spot bad design hidden very deeply into the directory tree.

## 5. Discussion

### Limitations:

There are some very clear limitations to these metrics-based visualizations. The researchers emphasize that educators should not rely on the visualizations without confirming hypotheses with students or triangulating with other sources.

There are instances where contribution metrics can be misleading, notably with:

- (1) automatically generated code and (2) files being committed that should not be tracked.

Besides this, there will always be unexpected usage patterns, such as the example where the student removes and adds all contents of a repository. So the takeaway here is that a repository visualization tool can highlight these unusual patterns but it is the duty of the educator to investigate them.

### Educator-Specific Tool Support

There are 6 key functionalities instrumental in increasing the adoption of such tools in education.

- Interactivity: Features like the ability to filter specific file types for visualization or zoom in on particular folders was very useful for assessing student projects. In the past, they relied on traditional git command line tools and various scripts, which are versatile, but not as user-friendly or as conveniently tailored for educational assessments.
- Author Unification: Students often use different usernames for commits due to variations in their git configurations across different devices, such as lab computers, private laptops, or home computers. Author unification can be done with git mailmap files, but students rarely configure them.
- Configurable Thresholds: The Single Author View has a 100% authorship threshold, but being able to customize this threshold, e.g. to 98% or other values, would be useful for a more tailored assessment option.
- Automatic File Filtering: Git-truck currently supports manual filtering of file types for visualization. However, this manual process can be time-consuming, especially when assessing multiple similar projects. Future research could explore automated detection of low-relevance files, using language-independent heuristics, such as identifying automatically generated code.
- Integration of Commit Messages: Currently, the educators have to review the commit messages alongside git-truck's visualizations. But ideally, commit messages should be integrated into the tool itself, making them easily accessible for educators.
- Support for Multi-Repositories: Educators frequently encounter both mono- and multi-repository projects, depending on course requirements. Many existing tools, including git-truck, primarily cater to mono-repositories. This limitation presents challenges when visualizing and comparing multi-repositories.

### Generalizability

Git-truck is designed with usability in mind. However, none of the visualizations it implements are unique or difficult to implement (though interactive features do require more effort). The usage examples presented earlier are likely to be useful for other educators using similar tools.

## 6. Related Work

Two separate researchers, Wattenberger and Tornhill, use circle packing, just like git-truck, to highlight metrics on top of repository structure. However, their work is not targeted at educators, but rather developers and business responsibles. Furthermore, although both provide online systems that could possibly visualize non-private GitHub repositories, none of the two services has the interactive nature argued for in this paper.

Two other researchers, Raclet and Silvestre, proposed Git4School, an analytics dashboard that enables a lecturer to follow the work of the students, commit by commit, to identify students experiencing difficulties. Their work is intended for a kind of educator and student in a context where the educator needs to guide individual student closely.

Kim et al. presented an interactive git repository visualization tool called Githru. They aim to support developers and domain experts in understanding a project's development history focusing on properties of the git commit graph. That is different from the goal presented in this paper.

Specialized tools focus on certain aspects of git repositories only.

- Cosentino et al.'s Gitana: Computes truck factors, identifies crucial authors for software projects.
- Gource (https://gource.io/): Animates authors and their contributions over time.
- Git Timeline Generator (https://www.preceden.com/git): Visualizes contribution frequencies over time.
- git-of-theseus: Creates static visualizations of repository growth over time.
- GitHub's built-in repository visualizations: Presents activity statistics, such as commit frequencies and number of contributors, among others.

## 7. Conclusions and Future Work

In conclusion, the authors of the paper argued that educators represent a distinct user category for software visualization tools. Multiple case studies from various courses and universities have demonstrated that git repository visualization can significantly aid educators in the assessment of group projects.

However, it's essential to acknowledge that the case studies presented are based on the experiences of a select group of educators who utilized a specific tool for group project assessment. The researchers plan to expand the research to include a wider group of educators. Their goal is to solidify the conclusions and also be able to offer clear guidance to educators and tool developers.

They are also hoping to delve into exploring the potential usage of such tools throughout the duration of a semester, since here they only researched using git repository visualization tools for the final evaluation phase. They hope this examination will provide a better understanding of the dynamic role of these tools in the educational process.

## 8. References

1. M. Lungu, R. -H. Pfeiffer, M. D’Ambros, M. Lanza and J. Findahl, "Can Git Repository Visualization Support Educators in Assessing Group Projects?," 2022 Working Conference on Software Visualization (VISSOFT), Limassol, Cyprus, 2022, pp. 187-191, doi: 10.1109/VISSOFT55257.2022.00030.
2. A. Tornhill, "Your code as a crime scene: use forensic techniques to arrest defects bottlenecks and bad design in your programs", Your Code as a Crime Scene, pp. 1-218, 2015.
3. A. Wattenberger, "Visualizing a codebase", 2021, [online] Available: https://githubnext.com/projects/repo-visualization.
4. J.-B. Raclet and F. Silvestre, "Git4school: A dashboard for supporting teacher interventions in software engineering courses", European Conference on Technology Enhanced Learning, pp. 392-397, 2020.
5. Y. Kim, J. Kim, H. Jeon, Y.-H. Kim, H. Song, B. Kim, et al., "Githru: visual analytics for understanding software development history through git metadata analysis", IEEE Transactions on Visualization and Computer Graphics, vol. 27, no. 2, pp. 656-666, 2020.
6. V. Cosentino, J. L. C. Izquierdo and J.
