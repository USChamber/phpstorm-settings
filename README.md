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

The selected **Scheme** will be saved to your project settings:

```
.idea/codeStyles/codeStyleConfig.xml
```

## Configure Inspections

1. Go to _Preferences → Editor → Inspections_
2. Select **Profile** → _USCC Web App_
3. Commit to project `.idea` folder

The selected **Profile** will be saved to your project settings:

```
.idea/inspectionProfiles/profiles_settings.xml
```

## Configure Automated Save Workflow

1. Go to _Preferences → Tools → Actions On Save_
2. Enable actions on save below

- [ ] Reformat code
- [ ] Optimize imports
- [ ] Run code cleanup

----

## Notes

### User-specific Settings Repository vs. Read-only Settings Repositories

Each PhpStorm project is able to configure a user-specific Settings Repository via _File → Manage IDE Settings → Settings Repository_. This feature is helpful if you use multiple computers and want to sync your PhpStorm configuration between them. By default, this feature saves _ALL_ preferences, which can become tedious when also trying to share settings via Read-only Settings Repositories. 

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

PhpStorm settings that are not found in the `.idea` folder are saved in the application settings folder: 

```
~/Library/Application Support/JetBrains/PhpStorm[##.##]/...
```

### Update Lifecycle

An update to a Settings Repository may look like the following:

- Open PhpStorm preferences and updates the desired setting in your local environment
- Find the updated setting configuration file in the local settings path above
- Copy the updated configuration file or individual setting to the shared Settings Repository repo (make sure you are only changing the desired settings if copying the entire file)
- Commit and push your changes to the shared Settings Repository
- Restart PhpStorm and notify team members to do the same

The folder structure of the configuration files in the Settings Repository should match the folder structure of the configuration files in the local application settings folder.
