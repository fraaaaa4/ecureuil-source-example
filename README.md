# Ecureuil example repository
This is a Ecureuil example repository, with two main files. Before starting, remember to enable Pages in the settings of the repository; this is needed, as otherwise the frontend won't be able to download and update the sources.

Pages will offer then the root of the repository. Before this you should:
- put all the JSON files for your apps into a folder of the source; the name of the source must be the same as the ID of the source in `sources.json`
- once compiled all the details about the sources, the file must be named `sources.json`

Ecureuil will use the `sources.json` file to know the details of the sources in the repository, and the `source-name-index.json` file generated via a GitHub Action pipeline to know all the apps contained in the repository. It's mandatory, therefore, that the pipeline completes correctly and without errors to make your sources usable in Ecureuil.

## Sources
The file `sources-example.json` contains an example on how an Ecureuil source should be structured. 
A JSON file can contain multiple sources; just make sure that, in the repository directory tree, they're in their respective folder.

The infos contained in this file will be shown in the Sources settings page in Ecureuil.

A few infos inside should be the same between this file, and the app JSON files:
- the id of the source, and the id of the source inside the app JSON must be the same
- the category of an app should be one of the ones in the Category array in this file

## App
Each app json should be contained in the folder of their respective source, and there should be a separate JSON for each app.

The file `app-example.jsone` contains all the infos needed for a single app. This repository contains also an example 7-Zip entry, to verify that Actions actually work; you can check out the completed Action and file too. If you copy the example file, remember to rename it from .jsone to .json, as it’s renamed as such so the action can be completed while ignoring that example app.

Once the GitHub Action completes, all the JSONs about apps will be put into a single JSON containing all the infos on the repos, and apps contained within. 
Ecureuil will use this to populate the front-end.

## YML and pipeline
The `build-catalogs.yml` contains the pipeline for publishing the source to GitHub Pages, so then make it be available in the frontend itself. The file itself contains all the needed informations, and must be edited from the template.

The name `source-name` inside the file should be substituted with the name of your source; it should be the same as the name of the folder containing the app JSONs.

A GitHub pipeline will put together all the app JSONs into a single JSON, and then it'll be offered through Pages.
