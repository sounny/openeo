# Fundamentals of Software Engineering - Course Project

This codebase is part of a pedagogical exercise designed to teach students who have never coded before how to code with AI assistance and use GitHub for a collaborative development environment.

## Objectives
*   **Code Comprehension:** Analyze code structure, identify key functions, and understand data flow.
*   **AI Integration:** Document AI-assisted code generation and modification processes.
*   **GitHub Workflow:** Detail branching, committing, pull requests, and merging strategies.
*   **Pedagogical Effectiveness:** Evaluate learning outcomes and identify areas for improvement in the teaching methodology.
*   **Deliverables:**
    *   Codebase analysis report.
    *   AI usage log.
    *   GitHub workflow documentation.
    *   Learning outcome assessment.

## Lab Handouts

### Lab 1: Building a Personal Homepage with GitHub Pages and AI Assistants

**Objective:** In this lab you will create a simple personal homepage hosted on GitHub Pages using a repository named `<yourusername>.github.io`. You will use an AI coding assistant (such as ChatGPT or GitHub Copilot) to generate the HTML content and then publish it via GitHub Pages.

**Steps:**
1.  **Sign up or sign in to GitHub.** If you don't already have an account, go to GitHub and create one. Be careful about your username – it will become part of the website URL.
2.  **Create a new repository named `<yourusername>.github.io`.** On GitHub, click **New repository**. Use your GitHub username as the repository name followed by `.github.io`. Select the **Public** option and click **Create repository**. This special naming convention tells GitHub to publish the contents at `https://<yourusername>.github.io/`.
3.  **Generate webpage code using an AI assistant.** Open your AI coding assistant and prompt it to write a simple HTML page for your personal site. You might say: *“Write a simple HTML page with a welcome message and describe my interests in space exploration.”* Copy the resulting HTML code.
4.  **Add the index.html file to your repository.** In your new GitHub repository, click **Add file → Create new file**. Name it `index.html`, paste the HTML code into the editor and commit the file to the main branch.
5.  **Enable GitHub Pages.** Go to your repository’s **Settings**. Under **Pages** (sometimes found under **Code and automation**), select the `main` branch and `/` (root) folder, then click **Save**. After a few seconds GitHub will build and publish your site.
6.  **Visit your site.** Navigate to `https://<yourusername>.github.io/` in your browser. You should see your personal homepage live. If you make edits later, commit them to the main branch – GitHub Pages will update automatically.

**Tips:**
*   You can enhance your site by adding a CSS stylesheet and more pages.
*   If you need more complex layouts, ask your AI assistant for help writing HTML and CSS.
*   If you encounter issues, use AI!

### Lab 2: OpenEO – Fork, Commit and Submit a Pull Request

**Objective:** This lab teaches you how to collaborate on an existing project. You will fork a repository, clone it locally, make changes, and submit a pull request to contribute back. This workflow is the basis of open‑source collaboration.

**Steps:**
1.  **Sign in to GitHub** with the account you used in Lab 1.
2.  **Fork the repository.** Navigate to [https://github.com/sounny/openeo](https://github.com/sounny/openeo) and click **Fork** (usually in the upper right). GitHub will create a copy of the repository under your account.
3.  **Clone your fork locally.** Open a terminal and run:
    ```bash
    git clone https://github.com/<yourusername>/openeo.git
    cd openeo
    ```
    This creates a local working directory and `.git` repository on your computer.
4.  **Create a feature branch (optional but recommended).** In your local repository:
    ```bash
    git checkout -b my-feature
    ```
    Creating a branch allows you to work on changes without affecting the main branch.
5.  **Make your changes.** Use your favourite IDE or text editor to modify the project. You might fix bugs, add capabilities or update documentation. Remember the Git workflow: edit files in the working directory, stage them with `git add`, and commit them.
6.  **Stage and commit your changes.**
    ```bash
    git add <modified files>
    git commit -m "Describe your changes"
    ```
    Git captures a snapshot of your changes in the commit. You can inspect the status of files with `git status` and view differences using `git diff`.
7.  **Push to your fork.**
    ```bash
    git push origin my-feature
    ```
    This uploads your branch to your fork on GitHub.
8.  **Open a pull request.** Visit your fork on GitHub. You’ll see a banner suggesting that you've recently pushed a branch. Click **Compare & pull request**, review your changes and submit the pull request to the original repository.
9.  **Respond to feedback.** The project maintainer may ask you to make changes. Update your branch locally, commit and push again – your pull request will update automatically.

---

# Open EO Viewer

Open EO Viewer is a lightweight Leaflet application for exploring NASA's Global Imagery Browse Services (GIBS) layers. It lets you switch between common true-color products, pick a date, and sketch areas of interest directly on the map. Drawn shapes can be exported to GeoJSON for further analysis or sharing with other tools.

## Features

- **Leaflet + GIBS integration** – browse daily NASA imagery without needing an API key.
- **Layer switching** – toggle between VIIRS and MODIS true-color layers with a single dropdown.
- **Date selection & quick navigation** – start from the latest available imagery, jump back/forward one day, or return to the newest date with dedicated buttons.
- **Drawing tools with measurements** – capture polygons or rectangles on top of the imagery, view live area/perimeter/bounding box stats on hover, and export them as GeoJSON, KML, or GeoTIFF snapshots.
- **Storm awareness** – visualize current severe storms from NASA EONET and see when the overlay last refreshed.

## Getting started

1. Open `index.html` in a browser (or serve the repository with your favorite static file server).
2. Use the layer and date controls in the toolbar to update the map imagery.
3. Activate the drawing controls in the lower-left corner to sketch features and export them via the **Export GeoJSON** button.

## Contributing

This project is intentionally simple and we welcome ideas that make it more useful. If you build a new capability—such as additional imagery layers, new export formats, or enhanced map interactions—please open a pull request so others can benefit as well. Bug fixes, documentation improvements, and other suggestions are also appreciated!

## License

This repository is released under the MIT License. See [LICENSE](LICENSE) for details.