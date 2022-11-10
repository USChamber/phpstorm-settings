PhpStorm Settings for Team Workflow
==================================

The steps below outline a baseline for a team-based workflow using PhpStorm.

- Global Code Style Schema and Inspections Profiles are shared via Settings Repositories
- Global configuration settings are managed in the project-specific `.idea` folder
- Local environment configuration and workflow preferences are managed by individual developers

## Install PhpStorm Plugins

1. Go to _Preferences → Plugins_
2. Install plugins below

- PHP Annotations
- PHP Inspections (EA Extended)
- Yii2 Inspections
- Symfony Support

## Install Settings Repositories

1. Go to _Preferences → Tools → Settings Repository_
2. Add Read-only Sources below
3. Restart PhpStorm

- [https://github.com/USChamber/phpstorm-settings](https://github.com/USChamber/phpstorm-settings) (this repository)
- [https://github.com/barrelstrength/PhpStorm-Live-Templates-Craft-CMS](https://github.com/barrelstrength/PhpStorm-Live-Templates-Craft-CMS) (
  optional)
- [https://github.com/barrelstrength/PhpStorm-Live-Templates-Twig-Extended](https://github.com/barrelstrength/PhpStorm-Live-Templates-Twig-Extended) (
  optional)

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

## Update Lifecycle

An update to this Settings Repository may look like the following:

- [ ] Open PhpStorm preferences and update the desired setting in your local environment
- [ ] Export the Code Style Scheme _Preferences → Editor → Scheme → Export → IntelliJ IDEA code style XML_
- [ ] Copy the updated configuration file or individual setting to the shared Settings Repository repo (look closely
  at the diff before you commit to make sure you are only changing the desired settings)
- [ ] Commit and push your changes to the shared Settings Repository
- [ ] Restart PhpStorm and notify team members to do the same

The folder structure of the configuration files in the Settings Repository should match the folder structure of the
configuration files in the local application settings folder. See _Local settings path_ section below for details.

Code Style changes are initially stored in the project `.idea` folder and will override Code Style rules in the shared
Settings Repository. See _Managing settings priority_ section below for more details.

----

## Notes

### User-specific Settings Repository vs. Read-only Settings Repositories

Each PhpStorm project is able to configure a user-specific Settings Repository via _File → Manage IDE Settings →
Settings Repository_. This feature may be helpful if you use multiple computers and want to sync your PhpStorm
configuration between them. By default, this feature saves _ALL_ preferences, which can become tedious and create
conflicts when also trying to share settings via Read-only Settings Repositories.

### Local settings paths

If you are curious or troubleshooting what exists, PhpStorm settings that are not found in the `.idea` folder are saved
in the application settings folder:

```
~/Library/Application Support/JetBrains/PhpStorm[##.##]/...
```

PhpStorm caches things nearby:

```
~/Library/Cache/JetBrains/...
```

### Managing settings priority

Once you make a change to your local project, PhpStorm will save a Project specific Code Style XML file to the
project `.idea` folder:

```
.idea/codeStyles/Project.xml
```

As we use a shared Settings Repository for the Code Style across multiple projects, we don't want this file in any given
project and it is likely excluded via the project `.gitignore`. To avoid conflicts and confusion between the Code
Style in the synced Read-only Settings Repository and the project, you will want to delete the project-specific Code
Style override after you've updated the shared Settings Repository with your exported file.

Toggle the visibility of the `.idea` folder in your PhpStorm project via _Maintenance -> Registry ->
projectView.hide.dot.idea_ setting.