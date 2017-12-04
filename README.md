# CF CLI i18n

This repository contains the internationalization (i18n) files for the CF CLI.

This seperation from the [CF CLI](https://github.com/cloudfoundry/cli) is done to separate the CF CLI code from the process of translation.

## How it works
![Diagram](https://raw.githubusercontent.com/cloudfoundry/cli-i18n/master/translation.svg?sanitize=true)

The internationalization process of the CF CLI happens in 4 phases:
1. Extraction - Extracting all the English strings used in the CF CLI and combining them with the translated set in this repository.
1. Providing New Strings for Translators - The untranslated set is posted to a shared service that external translators can pull from.
1. Translate Strings - The translated strings are returned from the external translators and merged back into this repository.
1. Merge on Compile - The CF CLI's CI pipeline [takes the translated strings](https://github.com/cloudfoundry/cli/blob/master/ci/cli/tasks/generate-i18n-resources.yml) and [merges them into the compiled code](https://github.com/cloudfoundry/cli/blob/master/ci/cli/tasks/build-binaries.yml).

The end result of this process produces a CF CLI with a translated UI.

### Notes on process
- The process of sharing strings to and from translators (phases 2 and 3) is currently evolving.
- As strings are added to the CF CLI on a daily basis, the number of untranslated strings will grow until a translation cycle (phases 2 and 3) take place. This means some translation files will have translated strings next to untranslated strings.
