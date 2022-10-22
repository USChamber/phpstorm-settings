PhpStorm Settings for Team Workflow
==================================

The steps below outline a baseline for a team-based workflow using PhpStorm. 

- Global Code Style Schema and Inspections Profiles are shared via Settings Repositories
- Global configuration settings are managed in the project-specific `.idea` folder
- Local environment configuration and workflow preferences are managed by individual developers

## Install PhpStorm Plugins

1. Go to _Preferences → Plugins_
2. Install plugins below

- DDEV Integration
- .env files support
- PHP Annotations
- PHP Inspections (EA Extended)
- Symfony Support
- Yii2 Inspections

## Install Settings Repositories

1. Go to _Preferences → Tools → Settings Repository_
2. Add Read-only Sources below
3. Restart PhpStorm

- [https://github.com/USChamber/phpstorm-settings](https://github.com/USChamber/phpstorm-settings) (this repository)
- [https://github.com/barrelstrength/PhpStorm-Live-Templates-Craft-CMS](https://github.com/barrelstrength/PhpStorm-Live-Templates-Craft-CMS) (optional)
- [https://github.com/barrelstrength/PhpStorm-Live-Templates-Twig-Extended](https://github.com/barrelstrength/PhpStorm-Live-Templates-Twig-Extended) (optional)

## Configure Shared Code Style

1. Go to _Preferences → Editor → Code Style_
2. Select **Scheme** → _USCC Web App_
3. Commit to project `.idea` folder 

## Configure Inspections

1. Go to _Preferences → Editor → Inspections_
2. Select **Profile** → _USCC Web App_
3. Commit to project `.idea` folder

## Configure Automated Save Workflow

1. Go to _Preferences → Tools → Actions On Save_
2. Enable actions on save below

- [ ] Reformat code
- [ ] Optimize imports
- [ ] Run code cleanup

----

## Notes

### User-specific Settings Repository vs. Read-only` Settings Repositories

Each PhpStorm project is able to configure a user-specific Settings Repository via _File → Manage IDE Settings → Settings Repository_. This feature is helpful if use multiple computers and want to sync your PhpStorm configuration between them. By default, this feature saves ALL preferences, which can become tedious when also trying to share settings via Read-only Settings Repositories. 

To use a personal, user-specific repo alongside a team workflow, add a `.gitignore` file to your personal Settings Repository and be sure to exclude all configuration files that might be used for project-specific configurations in the project `.idea` folder, or that may need to be configured on a project-by-project basis. 

```
# Example .gitignore
codestyles/*
code.style.schemes.xml
databaseDrivers.xml
inspection/*
nodejs.xml
web-types-npm-loader.xml
```

### Local settings path 

PhpStorm settings that are not found in the `.idea` folder are saved in the folder: 

```
~/Library/Application Support/JetBrains/PhpStorm[##.##]/...
```
