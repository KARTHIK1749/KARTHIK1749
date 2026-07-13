
# Clone the Repository

## Step 1 — Clone the Repository

```powershell
git clone https://github.com/KARTHIK1749/KARTHIK1749.git
```

---

## Step 2 — Open the Project

```powershell
cd REPOSITORY
```

---

## Step 3 — Install Dependencies

```powershell
pip install -r requirements.txt
```

---

# Project Structure

```text
.
├── .github
│   └── workflows
│       └── build.yml
├── cache
├── dark.svg
├── light.svg
├── update.py
├── ascii_to_svg.py
├── portrait.txt
├── portrait_tspan.txt
├── README.md
└── GUIDE.md
```



---

#  Converting a Photo into ASCII

## Step 1 — Choose a Good Photo

Use a front-facing portrait with good lighting. A plain background produces much cleaner ASCII art. Remove Background

**A plain background or a transparent PNG produces much cleaner ASCII art.**

> **Tip :** Higher contrast images usually generate much better results.

---

## Step 2 — Install ASCII Image Converter

### Windows

Download the latest Windows AMD64 release from:

https://github.com/TheZoraiz/ascii-image-converter/releases

Extract the ZIP file to any folder.

---

## Step 3 — Open PowerShell

```powershell
cd path\to\ascii-image-converter_Windows_amd64_64bit
```

Navigate to the folder containing the executable.

---

## Step 4 — Verify Installation

```powershell
.\ascii-image-converter.exe --version
```

If the version number appears, the installation is successful.

---

## Step 5 — Convert Your Image

```powershell
.\ascii-image-converter.exe ..\face.png --width 90 > portrait.txt
```

Generates a high-quality ASCII portrait.

---

## Step 6 — Experiment with Width

```powershell
.\ascii-image-converter.exe ..\face.png --width 40 > portrait40.txt

.\ascii-image-converter.exe ..\face.png --width 60 > portrait60.txt

.\ascii-image-converter.exe ..\face.png --width 90 > portrait90.txt

.\ascii-image-converter.exe ..\face.png --width 120 > portrait120.txt
```

Choose the width that preserves the best facial details.

---

## Step 7 — Improve Image Quality

If the portrait looks noisy:

- Increase image contrast
- Increase sharpness
- Crop unnecessary background
- Try different widths

Small edits can significantly improve the final ASCII output.

---

## Step 8 — Done

Your final ASCII portrait should be saved as:

```text
portrait.txt
```

This file will be used in the next step.

---

# Cleaning the ASCII Output

## Step 1 — Open the Generated ASCII File

Open:

```text
portrait.txt
```

---

## Step 2 — Remove Empty Lines

Delete any unnecessary blank lines from the top and bottom of the file.

This keeps the portrait vertically centered.

**NOTE :** my ASCII Code is 57 lines, make sure the ASCII code doesnt exceed to 60 or higher lines. More lines of ASCII code doesnt give you a High-Quality ASCII Portrait.  

---

## Step 3 — Fix Alignment

Ensure every line starts at the same position.

Avoid accidental spaces or tabs.

---

## Step 4 — Remove Unwanted Characters

Sometimes conversion creates noisy symbols around the portrait.

Delete anything that doesn't contribute to the image.

---

## Step 5 — Preserve Facial Details

Don't aggressively remove characters.

Focus on preserving:

- Eyes
- Nose
- Mouth
- Hair
- Shoulders

These define the portrait.

---

## Step 6 — Save the Clean Version

Save the cleaned file as:

```text
portrait.txt
```

This cleaned version will be converted into SVG.

---

# Converting ASCII into SVG

## Step 1 — Copy the provided `ascii_to_svg.py` script from this repository

Then, Run :

```text
python ascii_to_svg.py
```

This script converts ASCII characters into SVG `<tspan>` elements.

---

## Step 2 — Converted SVG Code 

After running script, you will get :

```text
portrait_tspan.txt
```

Each line becomes one SVG row with `<tspan>`

---

## Step 3 — Converted SVG Code 

Convert every ASCII line into:

```xml
<tspan x="390" y="30">ASCII LINE</tspan>
```

Each `<tspan>` represents one row of the portrait.

---

## Step 4 — Wrap Everything Inside SVG

Place all generated `<tspan>` elements inside:

```xml
<svg>

<text>

...

</text>

</svg>
```

This allows GitHub to render the portrait as a scalable vector image.

---

## Step 5 — Save the Output

Save the generated SVG as:

```text
dark.svg
```

Repeat the process if you're creating a light theme.

---

# Designing the Cyberpunk Terminal Layout

## Step 1 — Create the Terminal Window

Draw a rounded rectangle as the terminal background.

This acts as the base layout.

---

## Step 2 — Create Two Columns

Divide the terminal into:

Left

- ASCII Portrait

Right

- Information Panel

This keeps the design balanced.

**The Layout isnt fixed. Its completely optional, you can keep the ASCII portrait right and text left. Its individual's choice.**

---

## Step 3 — Add Terminal Sections

Separate information into sections such as:

- Subject
- Toolchain
- Neural Stack
- Contact
- GitHub Stats

Horizontal divider lines improve readability.

---

## Step 4 — Choose a Color Palette

Example:

```text
Background : Black

Primary Text : White

Accent : Cyan

Highlight : Green

Warning : Red
```

Using only a few colors keeps the terminal clean. Choose According to your Theme.

---

## Step 5 — Export the Final SVG

Save the finished terminal as:

```text
dark.svg

light.svg
```

These files will be embedded inside the README.

---

# Dynamic GitHub Stats

## Step 1 — Decide Which Stats to Display

Examples:

- Repositories
- Stars
- Followers
- Following
- Commits
- Lines of Code

Choose only the metrics you want.

---

## Step 2 — Fetch GitHub Data

Use the GitHub GraphQL API inside Python.

Retrieve all required profile statistics.

---

## Step 3 — Replace SVG Placeholders

Locate placeholder values inside the SVG.

Replace them with the latest GitHub data.

---

## Step 4 — Save the Updated SVG

Overwrite:

```text
dark.svg

light.svg
```

The profile now reflects the latest statistics.

---

# Python Update Script

## Step 1 — Copy the script from this repo

Create:

```text
update.py
```

And copy the python script from this repo and make required updates in the script.

This script updates the SVG automatically.

---

## Step 2 — Read Existing SVG Files

Loads:

```text
dark.svg

light.svg
```

---

## Step 3 — Fetch GitHub Statistics

Calls the GitHub GraphQL API.

Stores the response.

---

## Step 4 — Update Every Placeholder

Replaces:

- Repo count
- Stars
- Followers
- Commits
- LOC

with live values.

---

## Step 5 — Save the Files

Writes the updated SVG back to disk.

Your README now contains fresh statistics.

---

# GitHub Personal Access Token Setup

## Step 1 — Open GitHub Settings

GitHub

↓

Settings

↓

Developer Settings

↓

Personal Access Tokens

↓

Fine-grained Tokens

---

## Step 2 — Generate a New Token

Click:

```text
Generate new token
```

---

## Step 3 — Configure Permissions

Grant the required permissions for reading repository data.

### PAT permissions :

- Contents -> Read And Write
- Metadata -> Read only

---

## Step 4 — Copy the Token

Copy the generated token immediately.

You won't be able to see it again.

> Never commit this token to GitHub.

---

# Setup GitHub Secrets

## Step 1 — Open Repository Settings

GitHub Repository

↓

Settings

↓

Secrets and variables

↓

Actions

---

## Step 2 — Create ACCESS_TOKEN

Click:

```text
New repository secret
```

Name:

```text
ACCESS_TOKEN
```

Value:

```text
Your Personal Access Token
```

---

## Step 3 — Create USER_NAME

Create another secret.

Name:

```text
USER_NAME
```

Value:

```text
Your GitHub Username
```

---

## Step 4 — Save

Click **Add Secret**.

GitHub Actions can now access these values securely.

---

# GitHub Actions Workflow

## Step 1 — Create Workflow Folder

Create:

```text
.github/workflows
```

GitHub automatically detects workflow files inside this directory.

---

## Step 2 — Create the Workflow

Create:

```text
build.yml
```

Paste the workflow from this repository.

---

## Step 3 — Commit the Workflow

```powershell
git add .

git commit -m "Add GitHub Actions"

git push origin main
```

Pushing the workflow triggers GitHub Actions.

---

## Step 4 — Verify the Workflow

GitHub Repository

↓

Actions

↓

README Build

↓

Latest Run

A green checkmark indicates the workflow completed successfully.

---

## Step 5 — Automatic Updates

The workflow runs according to the cron schedule and automatically commits updated SVG files.

---

# Running the Project

## Step 1 — Run the Script

Run : 

```powershell
python update.py
```

The SVG files will be regenerated.

---

## Step 2 — Preview the README

Commit and push your changes.

Open your GitHub profile to verify everything is displayed correctly.

---

# Automatic Daily Updates

## Step 1 — Configure the Cron Schedule

Inside:

```text
build.yml
```

Set your preferred schedule.

Example:

```yaml
cron: "0 0 * * *"
```

Runs once every day.

---

## Step 2 — Push the Workflow

```powershell
git add .

git commit -m "Enable daily updates"

git push origin main
```

---

## Step 3 — Verify the Schedule

Open:

GitHub Repository

↓

Actions

↓

README Build

↓

Latest Run

Ensure the scheduled workflow executes successfully.

---

# Customization Guide

## Customize Your Information

You can edit:

- Name
- Role
- Email
- Portfolio
- Social Links
- Bio

inside your SVG template.

---

## Customize the Terminal

Change:

- Colors
- Fonts
- Borders
- Section Titles
- Layout
- Terminal Width

to create your own style.

---


## Add More GitHub Statistics

You can display additional information such as:

- Pull Requests
- Issues
- Contributions
- Streaks
- Languages
- Custom Metrics

Simply extend the Python update script.

---

## Build Your Own Theme

Nothing in this project is tied to a cyberpunk design.

Try creating your own:

- Retro CRT Terminal
- Matrix Theme
- Hacker Console
- Neon Theme
- Anime Dashboard
- Minimal Terminal

The workflow remains exactly the same 

**The design is entirely up to you.**