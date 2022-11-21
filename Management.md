# Project Management Plan

## Overview

### WBS & Estimation


### Project Objectives


### Project Risks



## Management Approach

### Project Process


### Quality Management


### Training Plan

| Area               | Participants | When, Duration      | Waiver Criteria            |
| ------------------ | ------------ | ------------------- | -------------------------- |
| Blockchain         | Project Team | 20/07/2022, 2 weeks | Mandatory                  |
| Hyperledger Fabric | Project Team | 01/10/2022, 2 weeks | Mandatory for Backend Team |
| Java, Javalin      | Project Team | 01/09/2022, 1 weeks | Mandatory                  |

## Master Schedule


## Project Organization


## Project Communication

### Communication Plan

| Item           | Target                    | Purpose                                   | When           | Type          |
| -------------- | ------------------------- | ----------------------------------------- | -------------- | ------------- |
| Discord        | Project Team              | Review meeting & Status report            | Monday, Friday | Voice, Remote |
| Google Meeting | Project Team & Supervisor | Review meeting, Sprint revision & Closeup | Wednesday      | Voice, Remote |
| Messenger      | Project Team & Supervisor | Meeting planning, Q&A & Status report     | Everyday       | Text, Remote  |
| FU Library     | Project Team              | Pair programming & Code review            | Planned        | Offline       |

### External Interfaces

## Configuration Management

### Tools & Infrastructures

#### Common

| Type               | Tool                    |
| ------------------ | ----------------------- |
| Version Control    | Git, GitHub             |
| UML                | PlantUML, Graphviz      |
| Deployment         | Docker                  |
| Project Management | Quarto, GitHub Projects |

### Backend

| Type                 | Tool                                                     |
| -------------------- | -------------------------------------------------------- |
| Programming Language | Java                                                     |
| Library              | Javalin, Fabric SDKs, HSCore, Guava, Genson, EvalEx, JWT |
| Compiler             | JDK, Lombok                                              |
| UI                   | TinyLog, JLine, Fabric CLI                               |
| DBMS                 | H2, Hibernate, Minifabric                                |
| IDE / Editor         | IntelliJ IDEA, VSCode                                    |

### Frontend

| Type                 | Tool       |
| -------------------- | ---------- |
| Programming Language | TypeScript |
| Library              | React      |
| Compiler             | Node       |
| UI                   | React      |
| IDE / Editor         | VSCode     |

### Document Management

We use Quarto to build documents from Markdown files and use GitHub to manage the files and their changes. A participant will create a new branch to edit the files, create pull requests and wait for the project manager to review the changes and merge to the main branch. Then, it'll be built in three outputs: a website using GitHub Pages for visualization, A PDF document & A MS-Word document.

### Source Code Management

We manage the source code by using GitHub. Endpoints of the project will be upload into separated repositories. Once the code is changed, the participant will create a new branch, create a relevant pull request, and wait for code owners to review and merge to the main branch.
