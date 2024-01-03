---
permalink: /readme/
layout: default
---

# AMR Website Readme

A new website for our Autonomous Multi-Robot Lab (AMR) at TU Delft. The webiste is built using Jekyll, [Boostrap 5 css](https://getbootstrap.com/docs/5.3/getting-started/introduction/) and hosted on GitHub Pages. It builds automatically when a commit is pushed to the `main` branch. **It takes some minutes** to build and for the changes to be reflected on the website. Check the build progress in actions (github repo).

> **Note:** Any file for projects, etc... can be either .md, or .html, just choose the most convenient and maintain the same frontmatter.

> **Note:** The website is still under development. If you find any bugs or have any suggestions, please open an issue or submit a pull request.

- [AMR Website Readme](#amr-website-readme)
  - [How to add a new publication](#how-to-add-a-new-publication)
  - [Adding a New Project](#adding-a-new-project)
  - [Adding a New Person](#adding-a-new-person)
  - [Adding a New Research Area](#adding-a-new-research-area)
  - [Adding a New News Item](#adding-a-new-news-item)
  - [Adding a New Robot](#adding-a-new-robot)
  - [Adding a New MSc project](#adding-a-new-msc-project)
  - [Adding to Vacancies or Education](#adding-to-vacancies-or-education)
  - [(Rare) Adding a New Page](#rare-adding-a-new-page)
  - [Some utilities](#some-utilities)
    - [Linking local files and images in your content](#linking-local-files-and-images-in-your-content)


## How to add a new publication

Each publication in the `_data/publications.json` file is represented as a JSON object. Juts add yours (at the top for example, they then order by date) and commit. It has the following fields:

- `title`: The title of the publication. This should be a string.

- `authors`: An array of strings, where each string is the name of an author of the publication.

- `date`: The date of the publication in "YYYY-MM-DD" format. If you don't know the day or month, just put any (e.g 2023-01-01).

- `type`: The type of the publication (available: *"journal", "conference", "workshop", "thesis", "other"*.).

- `venue`: The venue where the publication was published (e.g., the name of a journal or conference). Do not put the year.

- `links`: A dictionary, where each object represents a link related to the publication. Each link object should have a name (e.g., "web":, "PDF": ) and the associated URL.

- `note`: Any additional notes about the publication (e.g. "Nominated for best bets paper award"). This field is optional. is added after the date in the publication entry.

- `image`: (OPTIONAL) The path (or url) to an image file that represents the publication. This image is displayed on the publication's card on the website. **RECOMMENDED: The image should be square (same width and height)**. If you don't have an image, don't add this field.

- `belongs_to_projects`: An array of strings, where each string is the id of a project that the publication is associated with. The publication will then display in that project's page. If the publication is not associated with any project, use "note": null. Project ids are defined in each `_projects/` entry. Currently: *"airlab-manipulation", "airlab-ondemand", "drones-emergency", "game-theoretic-mp", "ridepooling", "scene-reasoning-team", "safevru", "harmony", "interact", "trilogy".*

- `abstract`: The abstract of the publication, as a long string.

Here's an example of what a publication object might look like:

```json
{
    {
        "title": "Learning to Play Trajectory Games Against Opponents with Unknown Objectives",
        "authors": [
            "X. Liu",
            "L. Peters",
            "J. Alonso-Mora"
        ],
        "date": "2023-04-01",
        "type": "journal",
        "venue": "Proceedings of IEEE Robotics and Automation Letters (RA-L)",
        "links": [
            {
                "web": "https://xinjie-liu.github.io/projects/game/"
            },
            {
                "PDF": "/assets/files/publications/liu2022ral.pdf"
            },
            {
                "video": "https://www.youtube.com/watch?v=f0KJuCC1Xyo"
            }
        ],
        "image": "/assets/images/publications/liu2022ral.png",
        "note": null,
        "belongs_to_projects": ["game-theoretic-mp", "interact"],
        "abstract": "Abstract: Many autonomous agents, such a..."
    },
}
```

## Adding a New Project

To add a new project to the website, you need to create a new Markdown file in the `_projects/` directory. The easiest is just to copy another project and change the data for yours.The file should start with a YAML frontmatter block that looks like this:

```yaml
---
title: "INTERACT: Intuitive Interaction for Robots among Humans"
project_id: interact
belongs_to_areas: [social-robots, mobile-manipulation]
date: 2023-01-01
# end_date: 2028-01-01 # end date if ended, approximated if not sure.
description: >-
  In this project, interactions of mobile robots and humans is key...
image: /assets/images/projects/INTERACT_picture.jpg
links:
    - name: Project Website
      url: "https://..."
    - name: "Github: multi-agent fabrics"
      url: "https://github.com/tud-amr/multi-robot-fabrics"
fundings: This project is founded the ERC Starting Grant project "Intuitive Interaction for Humans among Robots (INTERACT)". 
people:
    - name: Saray Bakker 
    - name: Andreu Matoses Gimenez
    - name: Dr. Clarence Chen
    - name: Prof. Javier Alonso-Mora
      extra_info: Autonomous Multi-Robot Lab (AMR) TU Delft
    - name: Prof. Wendelin Bohmer 
      extra_info: Key collaborator.
---
# Here you put the main body of the page, in markdown. You can also mix in html, or change this .md to .html
## About the Project...
```

Here's what each field means:

- `title`: The title of the project.

- `project_id`: A unique identifier for the project. This is used by publications to associate themselves with this project. Currently available: *"autonomous-vehicles", "entertainment", "flying-robots", "mobile-manipulation", "social-robots", "transportation"*

- `belongs_to_areas`: A list of area IDs that this project belongs to.

- `date`: The start date of the project. This is used for display purposes and for ordering projects on the website.

- `end_date`: (optional, just comment or remove if not applicable) The end date of the project. This is used for display purposes.

- `description`: A description of the project. This is displayed on the project's card on the website.

- `image`: The path (or url) to an image file that represents the project. This image is displayed on the project's card on the website.

- `links`: A list of links related to the project. Each link should have a `name` and a `url`.

- `fundings`: Information about the project's funding sources.

- `people`: A list of people involved in the project. Each person should have a `name`, and can optionally have `extra_info` about their role or affiliation.

## Adding a New Person

To add a new person to the website, you need to create a new Markdown file in the `_people/` directory. The easiest is just to copy another person and change the data for yours.The file should start with a YAML frontmatter block that looks like this:

```yaml
---
name: Andreu Matoses Gimenez
title: PhD Candidate
type: phd-candidate
joined_date: 2023-06-01
image: https://andreumatoses.github.io/images/profile.jpg
preferred_link: https://andreumatoses.github.io/
links:
    - name: Website
      url: "https://andreumatoses.github.io/"
    - name: Google Scholar
      url: "https://scholar.google.com/citations?user=JydqDdEAAAAJ&hl=en&inst=6173373803492361994&oi=ao"
    - name: Contact
      url: "https://www.tudelft.nl/staff/j.alonsomora/"
---
```

Here's what each field means:

- `name`: The person's name.

- `title`: The title that shows below the person's name on the website.

- `type`: The person's role in the team (e.g., *"post-doc", "phd-candidate", "professor", "engineer"*).

- `joined_date`: The date when the person joined the team.

- `left_date`: (optional, comment if not) The date when the person left the team. If you add a left date, the member will be moved to the past members section and the image field will not be used.

- `image`: The URL or path to an image file that represents the person. This image is displayed on the person's card on the website. **IMPORTANT: The image should be square (same width and height)**.

- `preferred_link`: The URL that you want to be linked from the person's name (in projects, authors). This field is optional. (hasn't been implemented yet)

- `links`: A list of links related to the person. Each link should have a `name` and a `url`.

## Adding a New Research Area

Straight forward, just add a new file in the `_areas/` directory. The file should start with a YAML frontmatter block that looks like this:

```yaml
---
title: Social Robots
subtitle: Among Humans | Motion Planners | Interaction | Social Preferences
area_id: social-robots # You add this ID in the project's front matter to associate it with this research area.
# image: # Currently not used. Didn't see the use.
---
The vision of ground robots seamlessly ...
```

## Adding a New News Item

Straight forward, just add a new file in the `_news/` directory. The file should start with a YAML frontmatter block, followed by the content, that looks like this:

```yaml
---
title: Workshop on Human Multi-Robot Interaction at IROS 2023
date: 2023-09-01
---
We are co-organizing the Workshop on Human Multi-Robot Interaction at IROS 2023. ... 
```

## Adding a New Robot

Straight forward, just add a new file in the `_robots/` directory. The file should start with a YAML frontmatter block that looks like this:

```yaml
---
name: Jackal   
subtitle: Differential-drive robotic research platform from Clearpath with custom perception pipeline.
type: ground robot # The type of robot: ground robot, flying robot, manipulator, mobile manipulator
image: /assets/images/robots/jackal.jpg
used_in_projects: [harmony, drones-emergency, ridepooling, scene-reasoning-team] # List of project IDs, separated by commas.
---

Hi! I am Jackal...
```

## Adding a New MSc project
TO DO

## Adding to Vacancies or Education

Directly edit the corresponding markdown file in the root directory. Should be very straight forward.

## (Rare) Adding a New Page

To add a new page, first create a new Markdown file in the root directory. The file should start with a YAML frontmatter block that looks like this:

```yaml
---
title: Vacancies
permalink: /vacancies/
---
```

By default it will use the page layout, which contains a title and a content section (plus all the basic components such as navbar, footer, etc..). If you want to use a different layout, you can specify it in the frontmatter block. 

Then to make the page accessible from the navbar, you need to add it to the `_data/navbar.yml` file. Just add a new entry to the list, with the title and the URL (the same as the `permalink` in the frontmatter block).

## Some utilities

### Linking local files and images in your content

Github pages makes it a bit annoying to link to local (without the http://...) files and images. The easiest way is to put them in the `assets/...` directory. Then you can link to them using the `site.baseurl` variable to append to the path. For example, to link to the file `assets/files/publications/liu2022ral.pdf`, you can use the following markdown:

```markdown
[Link to the PDF]({{ '/assets/files/publications/23-wilde-ral.pdf' | relative_url}})
```
[Link to the PDF]({{ '/assets/files/publications/23-wilde-ral.pdf' | relative_url}})

Images are the same (put the html in the markdown file as is), just append the `relative_url` variable:

```markdown
<div class="image-div mb-3 d-flex justify-content-center">
    <img src="{{ '/assets/images/cover_pic_4x3.png' | relative_url}}" class="img-fluid" width="600" alt="lab">
</div>
```
<div class="image-div mb-3 d-flex justify-content-center">
    <img src="{{ '/assets/images/cover_pic_4x3.png' | relative_url}}" class="img-fluid" width="600" alt="lab">
</div>