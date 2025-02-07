# Git Submodule Initialization Guide

## After Cloning Repository

If you've already cloned a repository that contains submodules, use either:

```bash
# Method 1: Two steps
git submodule init
git submodule update

# Method 2: One step
git submodule update --init
```

## Fresh Clone with Submodules

When cloning a new repository with submodules:

```bash
# Clone repository with all submodules
git clone --recursive https://github.com/username/repository.git
```

## Update Existing Submodules

To update submodules to their latest versions:

```bash
# Update all submodules
git submodule update --remote

# Update specific submodule
git submodule update --remote submodule_name
```

## Common Issues
- If submodule directories are empty after cloning, run `git submodule update --init`
- If you need to update a specific submodule, navigate to its directory and pull:
  ```bash
  cd submodule_directory
  git pull origin master
  ```
