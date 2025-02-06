# Basic Git Submodule Creation Guide

## Create a Submodule

### 1. Create Main Repository
```bash
# Create and initialize main repository
mkdir main-project
cd main-project
git init
```

### 2. Add a Submodule
```bash
# Add existing repository as a submodule
git submodule add https://github.com/username/sub-repository.git

# Or specify a different directory name
git submodule add https://github.com/username/sub-repository.git custom-name
```

### 3. Commit the Changes
```bash
# The above command creates .gitmodules file
git add .gitmodules
git add sub-repository
git commit -m "Add submodule"
```

## Basic Structure
After adding a submodule, your repository will look like this:
```
main-project/
├── .git/
├── .gitmodules          # Contains submodule information
└── sub-repository/      # The submodule directory
```

## .gitmodules Content
The .gitmodules file will contain:
```
[submodule "sub-repository"]
    path = sub-repository
    url = https://github.com/username/sub-repository.git
```

## Basic Commands
```bash
# Check submodule status
git submodule status

# Initialize submodule
git submodule init

# Update submodule
git submodule update

# Remove submodule
git submodule deinit sub-repository
git rm sub-repository
git commit -m "Remove submodule"
```
