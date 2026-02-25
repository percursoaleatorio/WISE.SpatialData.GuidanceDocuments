## 🛠 Setting Up the wiseEnvironment

This project uses [Conda](https://docs.conda.io/en/latest/) to manage its dependencies and ensure a reproducible workflow. 

All required packages for data analysis, bioinformatics, and documentation are specified in the [environment.yml](./src/environment.yml) file.

### Prerequisites

Make sure you have **Miniconda**, **Anaconda**, or **Mamba** installed on your system.

### Installation & Activation

**1. Navigate to the project folder:**
Open your terminal and ensure you are in the root directory of the project where the `environment.yml` file was copied to:

```bash
cd path/to/your/project

```

**2. Create the environment:**
Run the following command to build the environment. This will download and install all the exact package versions required for the project:

```bash
conda env create -f environment.yml

```

*(Note: If you use `mamba`, replace `conda` with `mamba` for a significantly faster installation).*

**3. Activate the environment:**
Once the installation finishes, you need to activate the environment before running any scripts or starting JupyterLab:

```bash
conda activate wiseEnvironment

```

You should now see `(wiseEnvironment)` at the beginning of your terminal prompt.

### Updating the Environment

If the project's dependencies change and the `environment.yml` file is updated, you can refresh your local setup without recreating it from scratch by running:

```bash
conda env update -f environment.yml --prune

```

## 📖 Building and Viewing Documentation

This project uses [Sphinx](https://www.sphinx-doc.org/) for documentation, enriched with [MyST](https://myst-parser.readthedocs.io/) for Markdown support and `sphinx-autodoc2` for automatic docstring generation.

Before building the documentation, ensure your Conda environment is activated:

```bash
conda activate wiseEnvironment

```

### Option 1: "Live build" (Recommended for Development)

If you are actively writing or editing documentation, the best way to preview your changes is using `sphinx-autobuild`. This will start a local web server and automatically refresh your browser whenever you save a file.

**1. Start the autobuild server:**
Navigate to the root of your project and run:

```bash
sphinx-autobuild docs docs/_build/html

```

*(Note: If your Sphinx source files are in a different directory than `**docs**`, adjust the paths accordingly).*

**2. View the docs:**
Open your web browser and navigate to the local URL provided in the terminal (usually `http://127.0.0.1:8000`).

### Option 2: Standard HTML Build

If you just want to generate the static HTML files once without starting a persistent server, you can use the standard build command.

**1. Build the HTML files:**
Navigate to your documentation directory (usually `docs/`) and run:

```bash
make html

```

*(On Windows, use `.\make.bat html` instead).*

**2. View the docs:**
Open the generated `index.html` file in your browser. You can typically find it at:

```text
docs/_build/html/index.html

```

### Option 3: Publishing to GitHub Pages

Once your documentation is ready to be shared, you can automatically publish it using GitHub Pages. 
The best way to do this is by setting up a GitHub Actions workflow that automatically builds and deploys your HTML files whenever you push changes to your main branch.

**1. Create a GitHub Actions workflow:**
Create a new configuration file in your repository at `.github/workflows/documentation.yml`.

Use the configuration  in the [documentation.yml](./src/documentation.yml) file.

**2. Configure your repository settings:**
Once the action runs for the first time, it will create a new branch called `gh-pages`.

* Go to your repository on GitHub.
* Navigate to **Settings** > **Pages**.
* Under **Build and deployment**, set the **Source** to "Deploy from a branch".
* Select the `gh-pages` branch and the `/ (root)` folder, then click **Save**.

Your documentation will now be publicly accessible at `https://<your-username>.github.io/<your-repository-name>/`!

