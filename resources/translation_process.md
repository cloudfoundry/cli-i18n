# Documents the Translation Process for CF CLI i18n

## Common Workflow for CLI team

*cli*

1. new strings added, modified, or deleted to code base:
    1. new command is added 
    1. existing command modified
1. CLI team members do as usual and build and tests and generate new JSON files in the cli-i18n
1. when ready to commit, the new JSON files in cli-i18n need to be committed to this repo
1. once the the new commit happens in cli-i18n repo it needs to be bumped in cli repo

*cli-i18n*

_Nothing needs to be done_

## Trigering the Translation of Strings

1. run a translation script: `start-translation`
    1. determine which strings since last `sent-to-translators-<date>` tag that are new or have been modified
    1. generate a JSON file that includes the new or modified strings: `strings-to-translate.json`
    1. tag cli-i18n repo as `sent-to-translators-<date>`
    1. email(*) to translators a `translation` file (format TBD) that includes the strings that need to be transtated
1. email back the `translation` file that includes the 

(*) email is one option, another option is to create a simple CF app that allow translators to download the `translation` file and upload the file when it includes the translated strings
