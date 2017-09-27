# Documents the Translation Process for CF CLI i18n

## Common Workflow for CLI team

*cli*

1. new strings added, modified, or deleted to code base:
    1. new command is added 
    1. existing command modified
1. CLI team members do as usual and build and test and generate new JSON files in the `cli-i18n` submodule
1. when ready to commit, the new JSON files in `cli-i18n` need to be committed to this repo
1. once the the new commit happens in `cli-i18n` repo it needs to be bumped in cli repo

*cli-i18n*

_Nothing TODO_

## Trigering the Translation of Strings

Periodically (exact length TBD) the CLI team will trigger a request for translation. This will entail:

1. run `start-translation` script
    1. determine which strings since last `sent-to-translators-<date>` tag that are new or have been modified
    1. generate a JSON file that includes the new and modified strings: `strings-to-translate.json`
    1. tag cli-i18n repo as `sent-to-translators-<date>`
    1. email (1) to translators a `translation` file (format TBD) that includes the strings that need to be transtated
1. email back the `translation` files that includes the translated strings (one file per language)
1. run `merge-translation` script
   1. checkout the `sent-to-translators-<date>` tag
   1. determine the `new or modified strings` since last `start-translation` run
   1. merge the translated strings in appropriate JSON files
   1. merge (2) the `new or modified strings` into JSON files
   1. tag cli-i18n repo as `translated-<date>` 
   1. bump the cli repo's submodule to reflect the new commits in cli-i18n

(1) email is one option, another option is to create a simple CF app that allow translators to download the `translation` file and upload the translated files
(2) there is a case when some of the new modified strings are part the strings that were translated. In this case, we will end up with JSON files with both the translated (old) string and an untranslated (new) string. That's OK since having extra strings that are not used does not cause any issue (just makes the binary bigger). Next translation process trigger should get rid of them.
