# Resume Builder

A LaTeX-based automated system for maintaining multiple versions of your resume with different project combinations. This tool solves a common problem in job applications: the need to customize your resume for different positions while keeping the content consistent and professional.

## Why Use This?

When applying for different positions, you often want to highlight different projects based on their relevance to each role. For example:
- A machine learning position might need your ML projects
- A web development role might need your full-stack projects
- A research position might need your academic projects

Maintaining multiple versions of your resume manually can be tedious and error-prone. If you update one section (like your work experience or skills), you need to update it across all versions. This tool automates that process by:

1. Keeping your core information (education, experience, skills) in a single template
2. Storing each project as a separate file
3. Automatically generating all possible combinations of your projects
4. Building professional PDFs using LaTeX
5. Using GitHub Actions to automate the build process

This way, you can focus on writing great content while the tool handles the tedious work of maintaining multiple resume versions.

## 🌟 Features

- Automatically generates multiple PDF resumes with different project combinations
- Supports both combinations and permutations modes
- Uses LaTeX for professional-looking documents
- Automated builds via GitHub Actions
- Easy project management through simple LaTeX files

## 🚀 Getting Started

### Prerequisites

- Git
- LaTeX installation (for local builds)
- Python 3.x (for local builds)

### Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/resume-builder.git
   cd resume-builder
   ```

2. Customize the template:
   - Edit `template.tex` with your personal information
   - Replace the details in the header (name, contact info, etc.)
   - Update the Education and Experience sections
   - Modify the Skills section as needed

3. Add your projects:
   - Create a new `.tex` file for each project in the `projects/` directory
   - Follow the format shown in the example `LLM.tex`
   - Each project file should contain a single `rSubsection` environment

4. Commit and push your changes:
   ```bash
   git add .
   git commit -m "Update resume content"
   git push
   ```

5. GitHub Actions will automatically:
   - Build all PDF combinations
   - Commit them to the `output/` directory
   - Push the changes back to your repository

6. Pull the generated PDFs:
   ```bash
   git pull
   ```

### 📁 Repository Structure

```
resume-builder/
├── .github/workflows/
│   └── build.yml         # GitHub Actions workflow
├── projects/
│   ├── LLM.tex          # Example project
│   └── *.tex            # Your project files
├── output/              # Generated PDFs
├── template.tex         # Main resume template
├── resume.cls          # LaTeX class file
└── build.py            # Build script
```

## 🛠️ Configuration

### Build Modes

The builder supports two modes:

1. **Combinations** (default):
   - Generates PDFs for each unique combination of 2-3 projects
   - Order doesn't matter
   - Example: For projects A, B, C:
     - 2 projects: AB, AC, BC
     - 3 projects: ABC

2. **Permutations**:
   - Generates PDFs for each possible arrangement of 2-3 projects
   - Order matters
   - Example: For projects A, B, C:
     - 2 projects: AB, BA, AC, CA, BC, CB
     - 3 projects: ABC, ACB, BAC, BCA, CAB, CBA

### GitHub Actions Configuration

The build mode and PDF name can be configured in `.github/workflows/build.yml`:

```yaml
pre_compile: |
  MODE="permutations"      # "combinations" or "permutations"
  PDF_NAME="YourName.pdf"  # Name of generated PDFs
```

### Local Building

To build locally:

```bash
python build.py --mode combinations --pdf_name YourName.pdf
```

## 💡 Tips

- Use [skip ci] in your commit message to prevent GitHub Actions from building PDFs
- Keep project descriptions concise and focused
- Use LaTeX commands for consistent formatting
- Regular commits will trigger automatic PDF generation
- Pull after each build to get the latest PDFs

## 📝 Project File Format

Each project file in the `projects/` directory should follow this structure:

```latex
\begin{rSubsection}
{Project Title}{}{}{} % The extra {} are for date and location if needed

\item Point 1 about the project
\item Point 2 about the project
\end{rSubsection}
```

## 🤝 Contributing

Feel free to submit issues and enhancement requests!

## 📄 License

This project is open source and available under the [MIT License](LICENSE).