# Contribute to backend-swe-interview-questions

## Welcome
This repo contains technical questions (and answers) on several topics you might want to prepare for an interview for a Backend position. We believe in the power of open source and are always looking for contributors to help us improve the quality of the questions. Any contributions are welcome and appreciated.

## What can I contribute?
This repository contains a collection of technical questions and answers on several topics such as [Database](./answers/database.md), [Networking](./answers/networking.md), [Operating System](./answers/os.md),[Programming Paradigm](./answers/programming-paradigm.md), [Security](./answers/security.md), [Software Development Process](./answers/software-development-process.md) and many more to come. There are some types of contributions we are actively looking for:
- **Answers**: There are many questions that have no answer yet, you can search the whole project `To be defined.`. If you have an answer to a question, please submit it as a pull request.

<img width="578" alt="Screen Shot 2022-04-10 at 15 10 41" src="https://user-images.githubusercontent.com/8603085/162608993-1be7eb6f-7a45-4ebc-8c38-bf15ad9b05be.png">

- **Questions**: If you have a question that you think should be included in the list, please add it to [README.md](./README.md). If you have an answer to that question, add it to [answers](./answers) folder as well. If you haven't had the answer yet, it's OK, just specify `To be defined.` to the corresponding answer file. We will seek for help for the answer from the community later.

- **New topics**: If you think there is a new topic that should be added to the list, please create a new issue to discuss with the authors and maintainers of this project about if we should have that. Please submit at least 1 sample question as well.

## How to contribute?
For all contributors, we recommend the standard [GitHub flow](https://docs.github.com/en/get-started/quickstart/github-flow) based on [forking and pull requests](https://docs.github.com/en/get-started/quickstart/contributing-to-projects).

Besides, we want the format of all markdown files to be consistent, so we chose [prettier](https://prettier.io/) is the tool to help us achieve that goal. You are recommended to install the [VSCode Prettier Extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) to format the file on save. Please remember to run the formatting command before you commit:
```bash
npm run prettier:fix
```

We also have a GitHub action to help if your file changes in the commits and pull requests are formatted correctly.